# ======================================================================
#  sbnobj main build file
#
#  cd .../path/to/build/directory
#  source .../path/to/sbnobj/ups/setup_for_development <-d|-p>
#  cmake [-DCMAKE_INSTALL_PREFIX=/install/path]
#        -DCMAKE_BUILD_TYPE=$CETPKG_TYPE
#        $CETPKG_SOURCE
#  make
#  make test
#  make install
#  make package (builds distribution tarfile)
# ======================================================================
cmake_minimum_required(VERSION 3.19 FATAL_ERROR)



find_package(cetmodules 2.29.02 REQUIRED)
project(sbnobj VERSION 09.12.09 LANGUAGES CXX)

message(STATUS
  "\n-- ============================================================================="
  "\n-- === *** Start of configuration of ${PROJECT_NAME} ***"
  "\n-- ===")

# cetbuildtools contains our cmake modules ### MIGRATE-ACTION-REQUIRED: remove

list(APPEND CMAKE_MODULE_PATH $ENV{CANVAS_ROOT_IO_DIR}/Modules) ### MIGRATE-ACTION-REQUIRED: remove

include(CetCMakeEnv)
cet_cmake_env()

cet_set_compiler_flags(DIAGS CAUTIOUS
  WERROR
  NO_UNDEFINED
  EXTRA_FLAGS -pedantic
  EXTRA_CXX_FLAGS -Wno-unused-local-typedefs
)

cet_report_compiler_flags(REPORT_THRESHOLD VERBOSE)

# these are minimum required versions, not the actual product versions
find_package( messagefacility )
find_package( canvas ) ### MIGRATE-ACTION-RECOMMENDED: use cet_find_package() with target semantics for linking
find_package( larcoreobj ) ### MIGRATE-ACTION-RECOMMENDED: use cet_find_package() with target semantics for linking
find_package( lardataobj ) ### MIGRATE-ACTION-RECOMMENDED: use cet_find_package() with target semantics for linking
find_package( larcorealg ) ### MIGRATE-ACTION-RECOMMENDED: use cet_find_package() with target semantics for linking
find_package( lardataalg ) ### MIGRATE-ACTION-RECOMMENDED: use cet_find_package() with target semantics for linking
find_package( nusimdata ) ### MIGRATE-ACTION-RECOMMENDED: use cet_find_package() with target semantics for linking
find_package( Boost COMPONENTS system)
find_package( ROOT )
find_package( CLHEP COMPONENTS All)

# macros for dictionary and simple_plugin
include(ArtDictionary)
include(CetMake)
include(BasicPlugin)

# add cet_find_library commands here when needed ### MIGRATE-ACTION-RECOMMENDED: use cet_find_package() with target semantics for linking

# ADD SOURCE CODE SUBDIRECTORIES HERE
add_subdirectory(sbnobj)

# tests
add_subdirectory(test)

# ups - table and config files
# must be AFTER all other subdirectories

# packaging utility - must be last


message(STATUS
  "\n-- ==="
  "\n-- === *** End of configuration of ${PROJECT_NAME} ***"
  "\n-- ============================================================================="
  "\n-- "
  )
cet_cmake_config()
