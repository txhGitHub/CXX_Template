set(Target loggerTest)
project(Target C CXX)

# 设置语言标准
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

message("")
message(STATUS "Start building : " ${Target})

# 设置包含路径
include_directories(${ROOT_DIR}/src/include)

# find_package(${This} REQUIRED HINTS "${ROOT_DIR}/cmake")
# include_directories(${${This}_INCLUDE_DIRS})

# 设置依赖动态库、静态库路径
link_directories(
        ${CMAKE_LIBRARY_OUTPUT_DIRECTORY}
        ${CMAKE_ARCHIVE_OUTPUT_DIRECTORY}
        )

# link_directories(${This}_LINK_DIRS)

aux_source_directory(. SRCS)

add_executable(${Target} ${SRCS})

target_link_libraries(${Target} -lpthread ${This})

# target_link_libraries(${Target} ${${This}_LIBRARIES})

message(STATUS "Stop building : " ${Target} "\n")