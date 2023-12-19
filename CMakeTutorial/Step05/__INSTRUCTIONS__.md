# Modifying where to put artefacts
A bit annoying is, that the executables and libraries are put into the bowels of the build directory.
It can be difficult to find the artefacts, which, after all, are what we do the build for in the first place.

# Adjusting CMAKE_* variables
cmake provides a lot of variables to customize builds. They include:
- directories
- tools
- (compile-) parameters
- and more

They start with `CMAKE_` so you should avoid using this prefix lest you override an existing one.
For writing output of your build to a custom location cmake provides the following variables:

- `CMAKE_RUNTIME_OUTPUT_DIRECTORY`: location for executables
- `CMAKE_LIBRARY_OUTPUT_DIRECTORY`: location for dynamic libraries (*.so, *.dll)
- `CMAKE_ARCHIVE_OUTPUT_DIRECTORY`: location for static libraries (*.a, *.lib)

01) in the root CMakeLists.txt add the following lines
```
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/output/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/output/lib)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/output/lib)
```
02) run cmake in your build directory
03) observe: the folders Step05/output/bin and Step05/output/lib are created
04) run `make`
05) observe:
    - the libgreeter.a file is in the `lib` folder
    - the step5 executable is in the `bin` folder

# Extra credits
Create a dynamic (SHARED) library instead of a static one

# If you want to try this again then
31) cd CMakeTutorial/Step05
32) rm -rf build output
33) cp CMakeLists-backup.txt CMakeLists.txt
34) cp src/CMakeLists-backup.txt src/CMakeLists.txt
