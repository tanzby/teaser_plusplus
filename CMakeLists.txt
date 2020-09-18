cmake_minimum_required(VERSION 3.17)
project(teaser)

set(CMAKE_CXX_STANDARD 17)

if (CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif (CMAKE_BUILD_TYPE)

set(CMAKE_CXX_FLAGS_RELEASE "-O3")

find_package(PCL REQUIRED)
find_package(Eigen3 REQUIRED)
include_directories(include ${EIGEN3_INCLUDE_DIRS} ${PCL_INCLUDE_DIRS})

add_subdirectory(thirdparty)
include_directories(thirdparty/spectra/include)
include_directories(thirdparty/pmc/include)
include_directories(thirdparty/tinyply/source)

add_library(${PROJECT_NAME} SHARED
    src/certification.cc
    src/fpfh.cc
    src/graph.cc
    src/matcher.cc
    src/ply_io.cc
    src/registration.cc
)
target_link_libraries(${PROJECT_NAME} ${PCL_LIBRARIES} pmc tinyply)

add_subdirectory(test)