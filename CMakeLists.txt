project(pybind11-exceptions-bug LANGUAGES CXX)
cmake_minimum_required(VERSION 3.16 FATAL_ERROR)

find_package(Python3 REQUIRED COMPONENTS Interpreter Development NumPy)
add_subdirectory(pybind11)
find_package(Armadillo CONFIG REQUIRED)
add_subdirectory(carma)
pybind11_add_module(pymod MODULE pymod.cpp)
# the offending line: not linking fixes error:
target_link_libraries(pymod PUBLIC carma)

FILE(TOUCH "${PROJECT_BINARY_DIR}/__init__.py")