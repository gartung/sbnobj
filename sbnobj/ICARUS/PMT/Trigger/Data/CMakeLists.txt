cet_make(  ### MIGRATE-ACTION-RECOMMENDED: use cet_make_library(), build_dictionary(), basic_plugin() with explicit source lists
  LIBRARIES
    lardataobj::RawData
    larcorealg::CoreUtils
    lardataalg::DetectorInfo
    cetlib_except::cetlib_except
  NO_DICTIONARY
  )

art_dictionary(DICTIONARY_LIBRARIES sbnobj::ICARUS_PMT_Trigger_Data)

install_headers()
install_source()
