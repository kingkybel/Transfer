# Better structure for CMake
The project is a very small one. Realistic programs have sometimes hundreds of header and source files.
So whilst it is theoretically possible to create only one CMakeLists.txt file, it would become messy and
unmaintainable.

# Include sub-directories
The best way to structure the cmake hierarchy is to follow the project folder hierarchy.
Normally only the root-folder and sub-folders containing C++ source files have a CMakeLists.txt,
but this is not a restriction: you can put a CMakeLists.txt anywhere you like.

The way to tell cmake to include sub-directories for processing is the instruction `add_subdirectory`.

01) in the Step03 - root directory create a build sub-folder
02) in the Step03/src folder create a CMakelists.txt file, e.g. by `touch ./src/CMakeLists.txt`
03) edit ./CMakeLists.txt and ./src/CMakeLists.txt and move the lines
```
# Adding something we can run - Output name matches target name
add_executable(step3 src/step3.cc src/greeter.cc)
```
from ./CMakeLists.txt to ./src/CMakeLists.txt and save both files
04) edit the file ./CMakeLists.txt and add the line 
```
add_subdirectory(src)
```
at the end of the file and save it.
05) in the build folder run `cmake ..`
06) observe: The build fails with error message
```
CMake Error at src/CMakeLists.txt:1 (add_executable):
  Cannot find source file:

    src/step3.cc
```
07) edit src/CMakeLists.txt to remove `src/` from the add_executable target file
08) save and run cmake again.
09) run `make` and this time the executable will be built successfully

# What's tricks?
cmake looks for files in relative folders to the current folder, so since the CMakeLists.txt
is *in* the folder src we needed to remove it from the files in the add_executable target.

# If you want to try this again then
31) cd CMakeTutorial/Step03
32) rm -rf build
33) cp CMakeLists-backup.txt CMakeLists.txt
34) rm src/CMakeLists.txt


