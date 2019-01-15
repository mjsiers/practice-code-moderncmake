# initially following this example to see if I can get things working properly
# https://github.com/pabloariasal/modern-cmake-sample/tree/master/libjsonutils

cmake_minimum_required(VERSION 3.13)
project(libjsonutils VERSION 1.0.0 LANGUAGES CXX)

#Make sure that custom modules like FindRapidJSON are found
list(INSERT CMAKE_MODULE_PATH 0 ${CMAKE_SOURCE_DIR}/cmake)

##############################################
# Declare dependencies
find_package(Boost 1.69 REQUIRED COMPONENTS regex)
find_package(RapidJSON 1.1 REQUIRED MODULE)

##############################################
# Create target and set properties

add_library(jsonutils
    src/json_utils.cpp
)

#Add an alias so that library can be used inside the build tree, e.g. when testing
add_library(JSONUtils::jsonutils ALIAS jsonutils)

#Set target properties
target_include_directories(jsonutils
    PUBLIC
        $<INSTALL_INTERFACE:include>
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/src
)

target_compile_features(jsonutils PRIVATE cxx_auto_type)
target_compile_options(jsonutils PRIVATE $<$<CXX_COMPILER_ID:GNU>:-Wall>)

target_link_libraries(jsonutils
    PUBLIC
        Boost::boost RapidJSON::RapidJSON
    PRIVATE
        Boost::regex
)

