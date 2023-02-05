cmake_minimum_required(VERSION 3.15)

set(VCPKG_TARGET_TRIPLET x64-linux)
include(/home/work/vcpkg/scripts/buildsystems/vcpkg.cmake)

set(project_VERSION 0.0.0)

project(project
	VERSION ${project_VERSION}
	DESCRIPTION "project"
	LANGUAGES C CXX)

include(CMakePackageConfigHelpers)
include(GNUInstallDirs)

find_path(FST_INCLUDE_DIRS "fst/fst.h")
find_library(FST_LIBRARY NAMES fst fstscript)
add_executable(main main.cpp)
target_include_directories(main PRIVATE ${FST_INCLUDE_DIRS})
target_link_libraries(main PRIVATE ${FST_LIBRARY})
