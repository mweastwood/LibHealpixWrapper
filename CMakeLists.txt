cmake_minimum_required(VERSION 2.6)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -std=c++0x")

project(LibHealpixWrapper)

add_library(healpixwrapper SHARED healpixwrapper.cpp)

find_library(HEALPIX_CXX_LIBRARY healpix_cxx)
target_link_libraries(healpixwrapper "${HEALPIX_CXX_LIBRARY}")

find_path(HEALPIX_CXX_HEADERS healpix_cxx/healpix_map.h)
target_include_directories(healpixwrapper PUBLIC "${HEALPIX_CXX_HEADERS}")

install(TARGETS healpixwrapper DESTINATION lib)

