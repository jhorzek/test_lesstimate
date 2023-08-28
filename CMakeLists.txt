# This file was partially generated with cmake-init by friendlyanon at https://github.com/friendlyanon/cmake-init

cmake_minimum_required(VERSION 3.14 FATAL_ERROR)

project(lesstimateTests LANGUAGES CXX)

include(cmake/CPM.cmake)

# ---- Dependencies ----
CPMAddPackage(
	URL "https://sourceforge.net/projects/arma/files/armadillo-12.6.3.tar.xz"
	NAME armadillo
	VERSION 12.6.3
)

CPMAddPackage(
  NAME Catch2
  GITHUB_REPOSITORY catchorg/Catch2
  VERSION 3.4.0
)

CPMAddPackage("gh:jhorzek/lesstimate#8ac2bf41b34a67b0a6fb751c1605cee3cd07edc4")

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
