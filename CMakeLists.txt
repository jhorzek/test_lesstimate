# This file was partially generated with cmake-init by friendlyanon at https://github.com/friendlyanon/cmake-init

cmake_minimum_required(VERSION 3.14 FATAL_ERROR)

project(lesstimateTests LANGUAGES CXX)

# download CPM.cmake
file(
  DOWNLOAD
  https://github.com/cpm-cmake/CPM.cmake/releases/download/v0.40.8/CPM.cmake
  ${CMAKE_CURRENT_BINARY_DIR}/cmake/CPM.cmake
  EXPECTED_HASH SHA256=78ba32abdf798bc616bab7c73aac32a17bbd7b06ad9e26a6add69de8f3ae4791
)
include(${CMAKE_CURRENT_BINARY_DIR}/cmake/CPM.cmake)

# ---- Dependencies ----
CPMAddPackage(
	URL "https://sourceforge.net/projects/arma/files/armadillo-15.0.3.tar.xz"
	NAME armadillo
	VERSION 15.0.3
)

CPMAddPackage(
  NAME Catch2
  GITHUB_REPOSITORY catchorg/Catch2
  VERSION 3.4.0
)

CPMAddPackage("gh:jhorzek/lesstimate#LESSTIMATE_VERSION")

#include(Catch)

# ---- Tests ----

add_executable(lesstimate_test source/lesstimate_test.cpp)
                 
target_link_libraries(
    lesstimate_test PRIVATE
    armadillo
    lesstimate::lesstimate
    Catch2::Catch2WithMain
)
target_compile_features(lesstimate_test PRIVATE cxx_std_17)

#catch_discover_tests(lesstimate_test)

# ---- End-of-file commands ----

#add_folders(Test)
