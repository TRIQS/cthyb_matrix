find_package(TriqsTest)
triqs_add_test_hdf(single_site_bethe " -p 1.e-5" )
triqs_add_test_hdf(cdmft_4_sites " -p 1.e-5"  )
