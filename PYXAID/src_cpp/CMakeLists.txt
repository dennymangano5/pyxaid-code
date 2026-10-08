cmake_minimum_required(VERSION 3.15)
project(pyxaid_custom CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# --- Python + pybind11 ---
find_package(Python3 REQUIRED COMPONENTS Interpreter Development)
find_package(pybind11 REQUIRED)

# --- Sorgenti ---
pybind11_add_module(pyxaid_core
    namd_export.cpp
    namd.cpp
    ElectronicStructure.cpp
    InputStructure.cpp
    state.cpp
    aux.cpp
    io.cpp
    random.cpp
    matrix.cpp
)

# Flag di compilazione (opzionale ma consigliato)
target_compile_options(pyxaid_core PRIVATE -O2 -Wall)

install(TARGETS pyxaid_core DESTINATION .)
