
# Explore the directory
00) in VSCode open a new terminal by clicking Terminal->New Terminal
01) in the commandline terminal change to the Step01 directory (cd Step01)
02) run: ls -Fax
03) observe: only a step1.cc (C++ source) and a CMakeLists.txt file are present (apart frome these instructions)
04) in VSCode open CMakeLists.txt and step1.cc
05) step1.cc is a syntacially correct c++ main file orf a hello-world program (take my word for it)
06) `cmake_minimum_required`, `project` and `add_executable`(step1 step1.cc) are the only instructions in the file
07) "#" lines are comments

# Use "make" to build an executable
In Posix systems where make is installed, simple compile operations can be done without any Makefiles
10) type: make step1
11) observe: a compilation is performed and an executable file "step1" is created.
12) type ./step1 to execute the fiel to verify a hello world message is created

## Why does this work?
    - only system headers and system libraries are used
    - system headers and system libraries are in standard directories
    - make is installed
    - make knows what to do with simple *.cpp *.cc files

# Use "cmake" build an executable
So why bother with cmake?
    - you might want to use libraries/headers that are not in standard path, are non-standard themthelves
    - your executable consists of more than one file
    - you want different versions of the build (debug/release/performance test/...)
    -...
Solution is to define what steps to take to create the executable in one or more CMakeLists.txt files.
The CMakeLists.txt is a fixed name (case sensitive) and the one in this directory is as simple as it gets.

20) run: cmake .
21) run: ls -Fax
22) observe: files and folders created, but no `step1` executable
23) run: make
24) run: ls -Fax
25) observe: executable ./step1 created
26) run: ./step1
27) observe: "Hello World"

# Housekeeping
The above works, but "clutters" the directory.
Instead create a build directory and build from there

30) rm -rf CMakeCache.txt CMakeFiles/ cmake_install.cmake Makefile step1
31) mkdir ./build
32) cd build
33) cmake ..
34) make
35) observe: files and folders created and executable built in build folder and not cluttering project directory

_NOTE_: The build directory is a file that is intended as working directory, subject to being removed and should not be
        used for project-files that you want to keep.
        If you want to re-build the project completely, then recreate the build directory. and start from step 30) again.

