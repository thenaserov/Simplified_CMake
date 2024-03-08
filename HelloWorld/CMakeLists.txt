cmake_minimum_required(VERSION 3.22)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(HelloWorld VERSION 1.0)
add_executable(HelloWorld main.cpp)
# to make executable -> cmake . && make
