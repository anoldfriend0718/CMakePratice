# vcpkg

## introduction

- [overview](https://github.com/microsoft/vcpkg)
- [index](https://github.com/microsoft/vcpkg/blob/master/docs/index.md)
- [manifest](https://github.com/microsoft/vcpkg/blob/master/docs/specifications/manifests.md)
- [example: Installing and Using Packages Example: SQLite](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake)

## Integrated with VSCode

### With CMake

- Unlike other platforms, we do not automatically add the include\ directory to your compilation line by default.

op 1. 当您希望将 vcpkg 作为一个子模块加入到您的工程中时， 您可以在第一个 project() 调用之前将以下内容添加到 CMakeLists.txt 中， 而无需将 CMAKE_TOOLCHAIN_FILE 传递给 cmake 调用。

```cmake
set(CMAKE_TOOLCHAIN_FILE ${CMAKE_CURRENT_SOURCE_DIR}/vcpkg/scripts/buildsystems/vcpkg.cmake
  CACHE STRING "Vcpkg toolchain file")
```

op 2. set in setting.json

```json
    "cmake.configureSettings": {
        "CMAKE_TOOLCHAIN_FILE": "/home/anoldfriend/Workspace/MyRepo/vcpkg/scripts/buildsystems/vcpkg.cmake"
    }
```

## Notes

### manifests

- 当使用 manifest 模式的时候，需要将最外层的 CMakeLists.txt 和 vcpkg.json 放在同一个目录下，否则不能成功
