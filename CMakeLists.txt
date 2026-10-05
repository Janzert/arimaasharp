cmake_minimum_required(VERSION 3.16)
project(sharp CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
  set(CMAKE_BUILD_TYPE Release)
endif()

# The engine and all its tools are one program; main/main.cpp picks the mode
# from the first argument ("sharp aei" runs it as an AEI engine).
file(GLOB SOURCES CONFIGURE_DEPENDS */*.cpp)

find_package(Threads REQUIRED)
add_executable(sharp ${SOURCES})
target_link_libraries(sharp PRIVATE Threads::Threads)

# A dev build takes a command first ("sharp runBasicTests", "sharp aei", ...)
# and enables dev-only engine options.
option(SHARP_DEV "Build the developer command line instead of the engine" OFF)
if(SHARP_DEV)
  target_compile_definitions(sharp PRIVATE SHARP_DEV)
endif()
