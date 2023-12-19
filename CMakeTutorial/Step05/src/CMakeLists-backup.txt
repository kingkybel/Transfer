# Put the greeter in a static library
add_library(greeter STATIC greeter.cc)
# Adding something we can run - Output name matches target name
add_executable(step5 step5.cc greeter.cc)
target_link_libraries(step5 greeter)
