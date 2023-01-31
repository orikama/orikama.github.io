+++
title = 'Clang'
+++

## Modules

- [Standard C++ Modules](https://clang.llvm.org/docs/StandardCPlusPlusModules.html)
  - do not confuse it with Clang extension(?) [Clang modules](https://clang.llvm.org/docs/Modules.html)

### Compilation

{{% notice style="info" title="Header Unit" icon=" " %}}
```shell
clang++ -std=c++20 -xc++-system-header --precompile concepts -o concepts.pcm
```
{{% /notice %}}

{{% notice style="info" title="Module Interface Partition Unit" icon=" " %}}
```shell
clang -std=c++20 -xc++-module -fmodule-file=<MODULE_FILE> Module-InterfacePartition.ixx --precompile -o Module-InterfacePartition.pcm
```
{{% /notice %}}

{{% notice style="info" title="Primary Module Interface Unit" icon=" " %}}
```shell
clang++ -std=c++20 -xc++-module -fprebuilt-module-path=. Module.ixx --precompile -o Module.pcm
# or
clang++ -std=c++20 -xc++-module -fmodule-file=Module-InterfacePartition.pcm Module.ixx --precompile -o Module.pcm
```
{{% /notice %}}

{{% notice style="info" title="Module Implementation Unit" icon=" " %}}
```shell
clang++ -std=c++20 -fmodule-file=M.pcm Module.cpp -c -o Module.o
```
{{% /notice %}}

- `<MODULE_FILE>` path to this module dependency (eg. `concepts.pcm` or `OtherModule.pcm`)
  - the only(?) way to specify `header unit` dependencies
  - can be used for usual modules too, otherwise `-fprebuilt-module-path=<DIR>`
  - can be used multiple times
- `-xc++-module` if the file extension is not `.cppm`
  - probably in the future other extensions will be added as well

## Compilation Database

- [JSON Compilation Database Format Specification](https://clang.llvm.org/docs/JSONCompilationDatabase.html)

I heckin love that it's called "Compilation Database" but the file name should be "compile_commands.json"

## LibTooling

- [LibTooling](https://clang.llvm.org/docs/LibTooling.html)
- [Tutorial for building tools using LibTooling and LibASTMatchers](https://clang.llvm.org/docs/LibASTMatchersTutorial.html)

Seems like analyzing modules AST is a little bit hard at the moment?  
Looks like you need to precompile every `import` to get correct AST in some cases, not that simple as with headers?  
And since Clang support for modules is lagging behind a bit(to put it lightly) you can get a lot of errors while precompiling modules.  
At least I've got a lot of errors while trying to compile module partition that was importing `<type_traits>` and `<concepts>` as a header units.  
And here I tought that may be using Clang to build my project that uses modules will be a bit early, but surely it's capable enough for AST analysis.

## Build LLVM/Clang from sources

- [Getting Started with the LLVM System](https://llvm.org/docs/GettingStarted.htm)
- [Building LLVM with CMake](https://llvm.org/docs/CMake.html)

Probably not the best possible configuration, but works for my needs

{{% notice style="info" title="CMakePresets.json" icon=" " %}}

<!-- TODO: Make it wider or add horizontal scroll? -->

```json
{
    "version": 6,
    "cmakeMinimumRequired": {
        "major": 3,
        "minor": 25,
        "patch": 0
    },
    "configurePresets": [
        {
            "name": "binary-dir",
            "binaryDir": "${sourceParentDir}/build/${presetName}",
            "hidden": true
        },

        {
            "name": "configuration-debug",
            "cacheVariables": {
                "CMAKE_BUILD_TYPE": "Debug"
            },
            "hidden": true
        },
        {
            "name": "configuration-release",
            "cacheVariables": {
                "CMAKE_BUILD_TYPE": "Release"
            },
            "hidden": true
        },
        {
            "name": "configuration-multi",
            "cacheVariables": {
                "CMAKE_CONFIGURATION_TYPES": "Debug;Release"
            },
            "hidden": true
        },

        {
            "name": "toolset-clang-cl",
            "toolset":{
                "strategy": "set",
                "value": "ClangCL"
            },
            "hidden": true
        },

        {
            "name": "compiler-clang",
            "cacheVariables": {
                "CMAKE_CXX_COMPILER": "clang"
            },
            "hidden": true
        },
        {
            "name": "compiler-msvc",
            "cacheVariables": {
                "CMAKE_CXX_COMPILER": "cl"
            },
            "hidden": true
        },

        {
            "name": "generator-ninja",
            "generator": "Ninja",
            "architecture": {
                "strategy": "external",
                "value": "x64"
            },
            "hidden": true
        },
        {
            "name": "generator-ninja-multi",
            "generator": "Ninja Multi-Config",
            "architecture": {
                "strategy": "external",
                "value": "x64"
            },
            "hidden": true
        },
        {
            "name": "generator-vs",
            "generator": "Visual Studio 17 2022",
            "architecture": {
                "strategy": "set",
                "value": "x64"
            },
            "hidden": true
        },

        {
            "name": "settings-vs-clang",
            "vendor": {
                "microsoft.com/VisualStudioSettings/CMake/1.0": {
                    "intelliSenseMode": "windows-clang-x64"
                }
            },
            "hidden": true
        },
        {
            "name": "settings-vs-msvc",
            "vendor": {
                "microsoft.com/VisualStudioSettings/CMake/1.0": {
                    "enableMicrosoftCodeAnalysis": true
                }
            },
            "hidden": true
        },

        {
            "name": "vars-llvm-common",
            "cacheVariables": {
                "CMAKE_INSTALL_PREFIX": "C:/Program Files/LLVM/17.0.0",
                "CMAKE_SKIP_INSTALL_ALL_DEPENDENCY": true,

                "BUILD_SHARED_LIBS": "OFF",
                "LLVM_BUILD_32_BITS": "OFF",
                "LLVM_BUILD_BENCHMARKS": "OFF",
                "LLVM_BUILD_DOCS": "OFF",
                "LLVM_BUILD_EXAMPLES": "OFF",
                "LLVM_BUILD_INSTRUMENTED_COVERAGE": "OFF",
                "LLVM_BUILD_TESTS": "OFF",
                "LLVM_ENABLE_BINDINGS": "OFF",
                "LLVM_ENABLE_DOXYGEN": "OFF",
                "LLVM_ENABLE_PROJECTS": "clang",
                "LLVM_ENABLE_RTTI": "OFF",
                "LLVM_ENABLE_SPHINX": "OFF",
                "LLVM_INCLUDE_BENCHMARKS": "OFF",
                "LLVM_INCLUDE_EXAMPLES": "OFF",
                "LLVM_INCLUDE_TESTS": "OFF",
                "LLVM_OPTIMIZED_TABLEGEN": "ON",
                "LLVM_TARGETS_TO_BUILD": "X86"
            },
            "hidden": true
        },
        {
            "name": "vars-llvm-msvc",
            "cacheVariables": {
                "LLVM_ENABLE_DIA_SDK": "ON"
            },
            "hidden": true
        },

        { "name": "ninja-clang-debug",   "inherits": [ "binary-dir", "configuration-debug",   "compiler-clang", "generator-ninja", "settings-vs-clang" ] },
        { "name": "ninja-clang-release", "inherits": [ "binary-dir", "configuration-release", "compiler-clang", "generator-ninja", "settings-vs-clang" ] },

        { "name": "ninja-msvc",          "inherits": [ "binary-dir", "configuration-multi",   "compiler-msvc", "generator-ninja-multi", "settings-vs-msvc", "cmake-exe", "vars-llvm-common", "vars-llvm-msvc" ] },
        { "name": "ninja-msvc-debug",    "inherits": [ "binary-dir", "configuration-debug",   "compiler-msvc", "generator-ninja",       "settings-vs-msvc", "cmake-exe", "vars-llvm-common", "vars-llvm-msvc" ] },
        { "name": "ninja-msvc-release",  "inherits": [ "binary-dir", "configuration-release", "compiler-msvc", "generator-ninja",       "settings-vs-msvc", "cmake-exe", "vars-llvm-common", "vars-llvm-msvc" ] },

        { "name": "visual-studio-clang", "inherits": [ "binary-dir", "configuration-multi", "toolset-clang-cl", "generator-vs", "settings-vs-clang", "vars-llvm-common", "vars-llvm-msvc" ] },
        { "name": "visual-studio-msvc",  "inherits": [ "binary-dir", "configuration-multi", "compiler-msvc",    "generator-vs", "settings-vs-msvc",  "vars-llvm-common", "vars-llvm-msvc" ] }
    ]
}
```

{{% /notice %}}
