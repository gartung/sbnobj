cet_find_library( DK2NU_TREE NAMES dk2nuTree PATHS ENV DK2NUDATA_LIB NO_DEFAULT_PATH ) ### MIGRATE-ACTION-RECOMMENDED: use of ENV ... may be UPS-dependent ### MIGRATE-ACTION-RECOMME ### MIGRATE-ACTION-RECOMMENDED: use cet_find_package() with target semantics for linking
include_directories( $ENV{DK2NUDATA_INC} ) ### MIGRATE-ACTION-RECOMMENDED: use target_link_directories() with target semantics

cet_make(  ### MIGRATE-ACTION-RECOMMENDED: use cet_make_library(), build_dictionary(), basic_plugin() with explicit source lists
  NO_DICTIONARY
  LIBRARIES
    cetlib_except::cetlib_except
    ROOT::Matrix
    ROOT::Core
    CLHEP::CLHEP
    nusimdata::SimulationBase
    ${ART_FRAMEWORK_SERVICES_REGISTRY}
    ${ART_FRAMEWORK_SERVICES_OPTIONAL}
    ${ART_FRAMEWORK_SERVICES_OPTIONAL_RANDOMNUMBERGENERATOR_SERVICE}
)

art_dictionary(DICTIONARY_LIBRARIES sbnobj::Common_SBNEventWeight)

install_headers()
install_source()

