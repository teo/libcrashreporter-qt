project(libcrashreporter-qt)
cmake_minimum_required(VERSION 2.8.11)
cmake_policy(SET CMP0020 OLD)

if(CMAKE_COMPILER_IS_GNUCXX AND CMAKE_CXX_FLAGS)
    # Breakpad uses GNU compiler extensions like typeof.
    # Luckily these features are not used on OSX, so we can build the
    # crashreporter there with the normal C++11 standard.
    string(REPLACE "-std=c++11" "-std=gnu++11" CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS})
    string(REPLACE "-std=c++14" "-std=gnu++14" CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS})
endif()

add_subdirectory(3rdparty)
add_subdirectory(src)

