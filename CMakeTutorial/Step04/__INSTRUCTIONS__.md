# Add a library and link to it
Almost always in C++ we use libraries to re-use code and increase productivity.
Now we will create a library and link it to executable.

# Add a library target
Cmake has another target type for libraries similar to `add_executable` called
`add_library`

01) edit src/CMakeLists.txt and add the following lines to the start of the file:
```
# Put the greeter in a static library
add_library(greeter STATIC greeter.cc)
```
02) remove the `greeter.cc` from the step4 executable target
03) save, create and change into a build directory and try to build
04) observe1: The library builds correctly:
```
[100%] Linking CXX static library libgreeter.a
[100%] Built target greeter
```
05) observe2: The build of the executable fails with the familiar error `undefined reference to 'sayHello()'`


The reason for this is that we did not tell cmake that the greeter library is necessary for the build of the exe.
So we need to tell cmake that the executable target `step4` needs a library called `greeter`.
_NOTE_: In Posix systems library-filneames typically follow the naming convention `lib<name>(_)?<version>.(a|o)`,
        for example libdietersutils_1.0.2.a.
        In cmake it is sufficient to provide the <name> - part of the filename to identify the library.
        In our case we created the library file `libgreeter.a` which we want to link to the exe.

11) add the following line at the end of the file src\CMakeLists.txt
```
target_link_libraries(step4 greeter)
```
12) run `make` again
13) observe that the build is now successful (find both the library and the executable in the build/src folder)

# If you want to try this again then
31) cd CMakeTutorial/Step04
32) rm -rf build
33) cp CMakeLists-backup.txt CMakeLists.txt
34) cp src/CMakeLists-backup.txt src/CMakeLists.txt
