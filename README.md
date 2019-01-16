# Practice Code: Modern CMake
Delibrate practice project for updating skills on latest versions of CMake.

## Objectives
Configure and setup CMake to be able to build a C++ Windows console application using
Visual Studio Code on Windows 10.  In order to make this practice more interesting, the 
application must use the following dependent libraries.

- Boost C++
- ZLib
- Google Test
- Apache Arrow/Parquet

Initially, the binary versions of these libraries will be installed using Anaconda.  The
**conda** folder will hold the description of how the Anaconda enviroment can be created.

## Build Procedure
### Generation Step
Execute the following commands to generate the Visual Studio build files.

```mkdir build```
```cd build```
```cmake -G "Visual Studio 15 2017 Win64" -DCMAKE_BUILD_TYPE=Release ..```