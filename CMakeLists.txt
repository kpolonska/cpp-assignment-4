cmake_minimum_required(VERSION 3.20)

project(elevator LANGUAGES CXX)

add_library(elevator_lib STATIC)
target_sources(elevator_lib PRIVATE source/libraries/elevator/src/elevator.cpp)
target_include_directories(elevator_lib PUBLIC source/libraries/elevator/include)
target_compile_features(elevator_lib PUBLIC cxx_std_23)
set_target_properties(elevator_lib PROPERTIES CXX_EXTENSIONS OFF)

add_executable(elevator_app)
target_sources(elevator_app PRIVATE source/application/src/main.cpp)
target_link_libraries(elevator_app PRIVATE elevator_lib)
target_compile_features(elevator_app PUBLIC cxx_std_23)
set_target_properties(elevator_app PROPERTIES CXX_EXTENSIONS OFF)
add_executable(probe_app)
target_sources(probe_app PRIVATE source/probe/src/main.cpp)
target_compile_features(probe_app PRIVATE cxx_std_23)
set_target_properties(probe_app PROPERTIES CXX_EXTENSIONS OFF)
