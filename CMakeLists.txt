cmake_minimum_required(VERSION 3.15)

set(VCPKG_TARGET_TRIPLET x64-linux)

set(project_VERSION 0.0.0)

project(project
	VERSION ${project_VERSION}
	DESCRIPTION "project"
	LANGUAGES C CXX)

include(CMakePackageConfigHelpers)
include(GNUInstallDirs)

find_package(GTest CONFIG REQUIRED)
add_executable(main main.cpp)
target_link_libraries(main PRIVATE GTest::gtest GTest::gtest_main GTest::gmock GTest::gmock_main)
