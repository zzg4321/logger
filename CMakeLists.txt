cmake_minimum_required(VERSION 3.13)
set(APP_NAME logger)
project(${APP_NAME})
set(CMAKE_CXX_STANDARD 14)


set(APP_SRC main.cpp)

#导入需要使用的boost库，如regex filesystem thread
find_package(Boost REQUIRED COMPONENTS log date_time system thread regex serialization)
if (NOT Boost_FOUND)
    message("Not found Boost")
endif ()
#导入头文件
include_directories(${Boost_INCLUDE_DIRS})
message("xxxxx${Boost_INCLUDE_DIRS}")
#导入库文件
link_libraries(${Boost_LIBRARIES})
message("yyyyyy${Boost_LIBRARIES}")

add_executable(${APP_NAME} ${APP_SRC})