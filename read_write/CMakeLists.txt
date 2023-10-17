cmake_minimum_required(VERSION 3.15)
project(read_write)

set(CMAKE_CXX_STANDARD 17)

set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_CXX_FLAGS} -Wl,-no-as-needed")

message("CMAKE_SOURCE_DIR : " ${CMAKE_SOURCE_DIR})

include_directories(
  ${CMAKE_CURRENT_SOURCE_DIR}/include/dynamixel_sdk
  DEPENDS system_lib
)
set(COM_LIB 
    -ldxl_x64_cpp 
    -lrt
    )
set(COM_SRC read_write.cpp)

add_executable(${PROJECT_NAME} ${COM_SRC})
target_link_libraries(${PROJECT_NAME} ${COM_LIB})
