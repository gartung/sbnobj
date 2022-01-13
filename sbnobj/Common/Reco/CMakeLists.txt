cet_make(  ### MIGRATE-ACTION-RECOMMENDED: use cet_make_library(), build_dictionary(), basic_plugin() with explicit source lists
  LIBRARIES
    cetlib_except::cetlib_except
    messagefacility::MF_MessageLogger
    larcorealg::Geometry
    lardataobj::AnalysisBase
    ${ROOT_BASIC_LIB_LIST}
  NO_DICTIONARY
  )

art_dictionary(DICTIONARY_LIBRARIES sbnobj::Common_Reco)

install_headers()
install_source()
