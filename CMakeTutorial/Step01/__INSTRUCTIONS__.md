00) run: ls -Fax
01) run: cmake .
02) run: ls -Fax
03) observe: files and folders created
04) run: make
05) run: ls -Fax
06) observe: executable ./step1 created
07) run: ./step1
08) observe: "Hello World"

The above works, but "clutters" the directory.
Instead create a build directory and build from there

10) rm -rf CMakeCache.txt CMakeFiles/ cmake_install.cmake Makefile step1
11) mkdir ./build
12) cd build
13) cmake ..
14) make
15) observe: files and folders created and executable built in build folder and not cluttering project directory

The build directory is a file that can be removed and should not be used for project-files of any kind

