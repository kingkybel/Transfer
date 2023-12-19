cmake_minimum_required(VERSION 3.8)

# This is your project statement. You should always list languages;
# Listing the version is nice here since it sets lots of useful variables
project(
  Step1
  VERSION 1.0
  LANGUAGES CXX)

# Adding something we can run - Output name matches target name
add_executable(step1 step1.cc)
