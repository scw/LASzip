
set(PNACL_PROGRAM plasio_laszip.pexe)

include_directories(
    .
    ../include
    $ENV{NACL_ROOT}/include
$ENV{NACL_ROOT}/include/pnacl)


add_executable(${PNACL_PROGRAM}   queue.cpp hello.cpp)
target_link_libraries(${PNACL_PROGRAM} laszip )

link_directories( $ENV{NACL_ROOT}/toolchain/mac_pnacl/usr/lib )
# target_link_libraries(  ${PNACL_PROGRAM} 
#                          stdc++ c m g c++ nacl nacl_exception)

link_directories( $ENV{NACL_ROOT}/lib/pnacl/Release )
target_link_libraries(  ${PNACL_PROGRAM} 
                         ppapi_cpp ppapi_simple ppapi_stub pthread nacl_io jsoncpp)



pnacl_finalise(${PNACL_PROGRAM})
pnacl_nmf(${PNACL_PROGRAM})
