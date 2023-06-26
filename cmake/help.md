## solution sample
```cmake
cmake_minimum_required(VERSION 3.19)

option(MW_PROJECT_NAME_FROM_DIRECTORY "Use the directory name  of the source directory as project name" ON)
if(MW_PROJECT_NAME_FROM_DIRECTORY)
	mw_set_project_name_from_source_dir(project_name)
else()
	set(project_name <project_name>)
endif()
project(${project_name} LANGUAGES C CXX)

if (MSVC)
    # warning level 4
    add_compile_options(/W4 /WX)
else()
    # additional warnings
    add_compile_options(-Wall -Wextra -Wpedantic -Werror)
endif()

set(CMAKE_CXX_STANDARD 17)
set_property(GLOBAL PROPERTY USE_FOLDERS ON)
set(CMAKE_SUPPRESS_REGENERATION OFF)

option(MY_USE_UNITY_BUILD "use unity build" OFF)
option(MY_RUN_TESTS "enable testing" ON)

list(APPEND CMAKE_MODULE_PATH
    "C:/Users/Andrew/source/repos/cmake-tutorial/dev/cmake")
include(common)

add_external_lib(my_testing_tools)
add_external_lib(math)
add_external_lib(misc)
add_external_lib(data_structures)

add_compile_definitions(
    LOCAL_LAUNCH
    INPUT_FILENAME="input.txt"
    OUTPUT_FILENAME="output.txt"
    EXPECTED_FILENAME="expected.txt"
)
if(MY_RUN_TESTS)
    add_compile_definitions(LOCAL_RUN)
endif()

add_subdirectory(sample)
```

## executable/library project/target sample
```cmake
set(CURRENT_TARGET <project_name>) # try to use alias instead of explicit use of target name

add_executable(<project_name>)
add_library(<project_name> STATIC)
file(GLOB SOURCE_FILES
    public/*.hpp
    public/*.h
    private/*.hpp
    private/*.h
    src/*.cpp
    src/*.c
    *.hpp
    *.h
    *.cpp
    *.c
)
target_sources(<project_name> PUBLIC ${SOURCE_FILES})

target_include_directories(<project_name>
    PUBLIC public
    PRIVATE private
    PRIVATE .
)
target_link_libraries(<project_name> PUBLIC <library>)

set_target_properties(<project_name> PROPERTIES FOLDER <vs_path>)
source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR})

# add_subdirectory(<project_tests>)
```

## misc functions

* `add_subdirectory(<path>)` - read cmake file in specified path and add it to ...?

## project functions

* `add_executable(<project name>)` - adds executable project to the solution
* `file(GLOB SOURCE_FILES *.cpp *.hpp *.h)` - grubs all files that match patterns to the list variable `SOURCE_FILES`
* `set_target_properties(<target_name> PROPERTIES FOLDER <path>)` - 
* `target_include_directories(<project_name> PRIVATE .)` - 
* `target_sources(<project_name> PUBLIC ${SOURCE_FILES})` - 
* `source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR})` - 
* `target_link_libraries(<project_name> PUBLIC <library>)` - 
* `get_filename_component(THIS_TARGET_NAME ${CMAKE_CURRENT_LIST_DIR} NAME)` - 
* `list(APPEND CMAKE_PREFIX_PATH "C:/Users/Andrew/source/c++libraries")` - 

## custom functions/macros

* add_all_successors_of_current_directory() - apply add_subdirectory() to each subfolder of current path (where the running cmake file located)

## import external remote library

* [Including external header library from github using cmake](https://stackoverflow.com/questions/44318262/including-external-header-library-from-github-using-cmake)