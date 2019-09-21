cmake_minimum_required(VERSION 3.2)

include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.23.201.tar.gz"
    SHA1 "29f10683f10c7b35e1f599d71542af0c2daa6a01"
)

project(App)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)
set(HUNTER_BUILD_SHARED_LIBS ON)

hunter_add_package(jaegertracing)
find_package(jaegertracing CONFIG REQUIRED)
list(APPEND LIBS jaegertracing::jaegertracing)

add_executable(app App.cpp)
target_link_libraries(app PUBLIC ${LIBS})
