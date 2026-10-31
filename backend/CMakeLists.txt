cmake_minimum_required(VERSION 3.28.3)
project(backend)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(Drogon CONFIG REQUIRED)

add_executable(backend
  src/main.cpp
)

target_link_libraries(backend PRIVATE
  Drogon::Drogon
)
