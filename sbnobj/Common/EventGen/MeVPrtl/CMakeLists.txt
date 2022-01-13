cet_find_library( DK2NU_TREE NAMES dk2nuTree PATHS ENV DK2NUDATA_LIB NO_DEFAULT_PATH ) ### MIGRATE-ACTION-RECOMMENDED: use of ENV ... may be UPS-dependent ### MIGRATE-ACTION-RECOMME ### MIGRATE-ACTION-RECOMMENDED: use cet_find_package() with target semantics for linking
include_directories( $ENV{DK2NUDATA_INC} ) ### MIGRATE-ACTION-RECOMMENDED: use target_link_directories() with target semantics

cet_make(  ### MIGRATE-ACTION-RECOMMENDED: use cet_make_library(), build_dictionary(), basic_plugin() with explicit source lists
  LIBRARIES
    cetlib_except::cetlib_except
    nusimdata::SimulationBase
    ${ROOT_BASIC_LIB_LIST}
  NO_DICTIONARY
  )

art_dictionary(DICTIONARY_LIBRARIES sbnobj::Common_EventGen_MeVPrtl nusimdata::SimulationBase)

install_headers()
install_source()
