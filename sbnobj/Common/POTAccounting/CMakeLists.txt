cet_make( 
  LIBRARIES
    cetlib_except::cetlib_except
    ${ROOT_BASIC_LIB_LIST}
  NO_DICTIONARY
  )

art_dictionary(DICTIONARY_LIBRARIES sbnobj_Common_POTAccounting)

install_headers()
install_source()
