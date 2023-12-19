# Better structure
In order to better structure the product the following was done:
- created a subfolder called "include/" to contain header (*.h) file
- created a subfolder called "src/" to contain C++ - implementation files (*.cc or *.cpp or *.cxx)
- created a source and header pair that implements a function include/greeter.h and src/greeter.cc
- moved the main file step2.cc into the src/ folder

So Let's try to build without modifying the CMakeLists.txt

00) rm -rf CMakeCache.txt CMakeFiles/ cmake_install.cmake Makefile step2
01) mkdir -p ./build
02) cd build
03) cmake ..
04) observe: files and folders created and not cluttering project directory
05) make
06) observe: build fails with "Step02/src/step2.cc:1:10: fatal error: greeter.h: No such file or directory"

# What happened?
The pre-processor tries to do it's job and replace the #include instruction in line 1 of the file step2.cc
with the contents of the file - but it cannot find the file.
By default the compiler looks only in the local directory and in the systemfolder(s) like `/usr/include`
for header files

# How do we fix it?
We have to tell cmake where to find headerfiles

10) open the CmakeLists.txt file in the project folder for editing
11) at the very end of the file add the following lines
```
include_directories(
  ${CMAKE_SOURCE_DIR}/include
  )
```
12) save the file and exit
13) in the build directory try `make` again
14) observe: the build fails again, but with a different error:
```
/usr/bin/ld: CMakeFiles/step1.dir/src/step2.cc.o: in function `main':
step2.cc:(.text+0x9): undefined reference to `sayHello()'
collect2: error: ld returned 1 exit status
make[2]: *** [CMakeFiles/step1.dir/build.make:97: step1] Error 1
make[1]: *** [CMakeFiles/Makefile2:83: CMakeFiles/step1.dir/all] Error 2
make: *** [Makefile:91: all] Error 2
```
_NOTE_: The variable `CMAKE_SOURCE_DIR` is a cmake variable that is set to the directory of the current CMakeLists.txt


# What the heck?
Now our program passes the pre-processor stage, which means now the header file is found and pre-processed.
The compilation also succeeds - I know this because I did not get a syntax error.
However - the linker fails with an undefined symbol/reference.
We defined the function `sayHello()` in the file 'src/greeter.h' but we failed to let cmake know that this files
needs to be compiled.

# Make it work
21) open the CmakeLists.txt file in the project folder for editing
22) edit the line
```
add_executable(step2 src/step2.cc)
```
to also include the greeter - souce
```
add_executable(step2 src/step2.cc src/greeter.cc)
```
23) do `make` again
24) observe: the build now works and the executable is created
25) ./step2  # should show the Hello World message

# If you want to try this again then
31) cd CMakeTutorial/Step02
32) rm -rf build
33) cp CMakeLists-backup.txt CmakeLists.txt





