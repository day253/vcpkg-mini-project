cmake_minimum_required(VERSION 3.15)

set(VCPKG_TARGET_TRIPLET x64-linux)
include(/workspaces/vcpkg/scripts/buildsystems/vcpkg.cmake)

set(project_VERSION 0.0.0)

project(project
	VERSION ${project_VERSION}
	DESCRIPTION "project"
	LANGUAGES C CXX)

include(CMakePackageConfigHelpers)
include(GNUInstallDirs)

find_package(PkgConfig REQUIRED)
pkg_check_modules(marisa REQUIRED IMPORTED_TARGET marisa)

add_executable(main main.cpp)
target_link_libraries(main PkgConfig::marisa)
