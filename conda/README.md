# Practice Code Modern CMake
Delibrate practice project for updating skills on latest versions of CMake.

## Objectives
This file documents the process of getting the third party libraries installed 
using Anaconda.  The following commands should be used to manage the Python environment.

### Create Environment (Command Line)
```conda create --name devcmake python=3.6 cmake git pkgconfig boost-cpp zlib rapidjson```

### Create Environment (From File)
```conda env create -f environment.yml```

### Activate Environment
```conda activate devcmake```

### Export Environment
```conda env export > environment.yml```

### Remove Environment
```conda remove --name devcmake --all```
