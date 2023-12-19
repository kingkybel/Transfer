cmake_minimum_required(VERSION 3.8)

# This is your project statement. You should always list languages;
# Listing the version is nice here since it sets lots of useful variables
project(
  Step3
  VERSION 1.0
  LANGUAGES CXX)

# Adding something we can run - Output name matches target name
add_executable(step3 src/step3.cc src/greeter.cc)
include_directories(
  ${CMAKE_SOURCE_DIR}/include
  )

