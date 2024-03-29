cmake_minimum_required(VERSION 3.21)
project(DataTransfer)

add_subdirectory(modules/json)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_FLAGS "-std=gnu++2a -Wall -Werror -Wpedantic -pthread")

add_executable(DataTransfer main.cpp http_req.hpp data.hpp json_converter.hpp)

find_package( Boost 1.71.0 COMPONENTS date_time)
find_package(fmt)

target_include_directories(DataTransfer PUBLIC ${Boost_INCLUDE_DIRS})

target_link_libraries(DataTransfer fmt::fmt)
target_link_libraries(DataTransfer mysqlcppconn)
target_link_libraries(DataTransfer ${Boost_DATE_TIME_LIBRARY})
target_link_libraries(DataTransfer nlohmann_json::nlohmann_json)