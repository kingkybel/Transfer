cmake_minimum_required(VERSION 3.8)

# This is your project statement. You should always list languages;
# Listing the version is nice here since it sets lots of useful variables
project(
  Step5
  VERSION 1.0
  LANGUAGES CXX)

include_directories(
  ${CMAKE_SOURCE_DIR}/include
  )

add_subdirectory(src)
