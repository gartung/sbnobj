cet_make(  ### MIGRATE-ACTION-RECOMMENDED: use cet_make_library(), build_dictionary(), basic_plugin() with explicit source lists
  LIBRARIES
    cetlib_except::cetlib_except
    lardataobj::Simulation
  NO_DICTIONARY
  )

art_dictionary(DICTIONARY_LIBRARIES sbnobj::SBND_CRT)

install_headers()
install_source()
