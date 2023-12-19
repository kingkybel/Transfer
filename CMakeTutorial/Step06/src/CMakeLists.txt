# Put the greeter in a static library
# add_library(greeter STATIC greeter.cc)
# Adding something we can run - Output name matches target name
set(CMAKE_PREFIX_PATH "/usr/lib;/usr/slib;${CMAKE_PREFIX_PATH};${CMAKE_SOURCE_DIR}/installdir")
message("CMAKE_PREFIX_PATH=${CMAKE_PREFIX_PATH}")
find_library(GREETER_LIB NAMES greeter)
message("GREETER_LIB=${GREETER_LIB}")
add_executable(step6 step6.cc greeter.cc)
target_link_libraries(step6 ${GREETER_LIB})
