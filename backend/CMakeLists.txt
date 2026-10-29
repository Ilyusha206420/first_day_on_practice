cmake_minimum_required(VERSION 4.4)
project(backend)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

include(FetchContent)
FetchContent_Declare(
  drogon
  GIT_REPOSITORY https://github.com/drogonframework/drogon
)
FetchContent_MakeAvailable(drogon)

add_executable(backend
  src/main.cpp
)

target_link_libraries(backend PRIVATE
  Drogon::Drogon
)
