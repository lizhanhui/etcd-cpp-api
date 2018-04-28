add_library(etcd-cpp-api SHARED Client.cpp Response.cpp Value.cpp json_constants.cpp)
set_property(TARGET etcd-cpp-api PROPERTY CXX_STANDARD 11)

target_link_libraries(etcd-cpp-api ${CPPREST_LIB} ${OPENSSL_LIBRARIES} ${Boost_LIBRARIES})
message("Boost libraries: ${Boost_LIBRARIES}")

install (TARGETS etcd-cpp-api DESTINATION lib)
install (FILES ../etcd/Client.hpp
               ../etcd/Response.hpp
               ../etcd/Value.hpp
               DESTINATION include/etcd)
