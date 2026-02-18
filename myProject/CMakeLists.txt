# This locks behaviour rules of CMake.
# Without this line, CMake guesses legacy behaviours.

cmake_minimum_required(VERSION 3.20)


# When CMake reads this line it:
# Detects the compiler (finds MSVC, linker, windows SDK)
# Creates core variables (myProject = PROJECT_NAME)
# Enables a language (LANGUAGES CXX = C++) rules for compiling C++

project(myProject LANGUAGES CXX)


# This sets a requirement property
# All future C++ target should request C++ 20)

set(CMAKE_CXX_STANDARD 20)


# This strengthen the rule
# Without it, if compiler doesn't support C++ 20
# it silently downgrade to C++ 17
# With it on, if compiler doesn't support C++ 20
# configuration fails
# It prevents mysterious bugs on older compilers

set(CMAKE_CXX_STANDARD_REQUIRED ON)


# This creates a target node inside CMake's dependency graph
# Target:
# Name: MyProject
# Type: Executable
# Sources: main.cpp
# Language: C++
# Requires: C++20

add_executable(myProject "src/main.cpp")