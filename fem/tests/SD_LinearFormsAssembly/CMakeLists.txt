INCLUDE(test_macros)
INCLUDE_DIRECTORIES(${CMAKE_BINARY_DIR}/fem/src)

CONFIGURE_FILE(linearftest.sif linearftest.sif COPYONLY)
ADD_ELMERTEST_MODULE(SD_LinearFormsAssembly LinearFormsAssembly 
                                         LinearFormsAssembly.F90)

file(COPY LinearFormsAssembly.F90 cube.grd ELMERSOLVER_STARTINFO DESTINATION 
                                       "${CMAKE_CURRENT_BINARY_DIR}/")

ADD_ELMER_TEST(SD_LinearFormsAssembly LABELS benchmark threaded serendipity)
