cmake_minimum_required(VERSION 3.30)
project(BeastApp LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Boost 1.90 REQUIRED CONFIG)
find_package(Threads REQUIRED)

add_executable(beast_app src/main.cpp src/utils.cpp include/utils.hpp)

target_link_libraries(beast_app PRIVATE
    Boost::headers
    Threads::Threads
)

target_compile_definitions(beast_app PRIVATE
    BOOST_ERROR_CODE_HEADER_ONLY
    BOOST_SYSTEM_NO_LIB
)

target_include_directories(beast_app PRIVATE include)
