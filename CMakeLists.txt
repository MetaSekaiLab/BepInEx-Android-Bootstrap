cmake_minimum_required(VERSION 3.22)
project(modbootstrap LANGUAGES CXX)

add_library(modbootstrap SHARED native/bootstrap.cpp)
target_compile_features(modbootstrap PRIVATE cxx_std_17)
target_compile_options(modbootstrap PRIVATE -Wall -Wextra -Werror)
target_link_options(modbootstrap PRIVATE -Wl,--export-dynamic $<$<CONFIG:Release>:-Wl,--strip-all>)
target_link_libraries(modbootstrap PRIVATE android dl log)
