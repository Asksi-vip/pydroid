cmake_minimum_required(VERSION 3.4.1)

add_library(jep SHARED IMPORTED)
set_target_properties(jep PROPERTIES IMPORTED_LOCATION
        ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/jep.so)

add_library(
        native-lib
        SHARED
        src/main/cpp/native-lib.cpp)

find_library(
        log-lib
        log)

target_link_libraries(
        native-lib
        jep
        ${log-lib})