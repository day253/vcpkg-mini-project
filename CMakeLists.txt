cmake_minimum_required(VERSION 3.15)

set(VCPKG_TARGET_TRIPLET x64-linux)

set(project_VERSION 0.0.0)

project(project
	VERSION ${project_VERSION}
	DESCRIPTION "project"
	LANGUAGES C CXX)

set(CMAKE_CXX_FLAGS "${CMAKE_CPP_FLAGS} -DNDEBUG -O2 -D__const__=__unused__ -pipe -W -Wall -Wno-unused-parameter -fPIC -fno-omit-frame-pointer")
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(FindProtobuf)
protobuf_generate_cpp(PROTO_SRC PROTO_HEADER echo.proto)
include_directories(${CMAKE_CURRENT_BINARY_DIR})
find_package(unofficial-brpc CONFIG REQUIRED)

add_executable(streaming_echo_server server.cpp ${PROTO_SRC} ${PROTO_HEADER})
add_executable(streaming_echo_client client.cpp ${PROTO_SRC} ${PROTO_HEADER})

target_link_libraries(streaming_echo_server unofficial::brpc::brpc-static)
target_link_libraries(streaming_echo_client unofficial::brpc::brpc-static)