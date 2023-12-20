# Put the greeter in a static library
add_library(greeter STATIC greeter.cc)
# Adding something we can run - Output name matches target name
add_executable(step6 step6.cc greeter.cc)
target_link_libraries(step6 greeter)
