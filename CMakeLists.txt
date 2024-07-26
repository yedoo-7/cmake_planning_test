cmake_minimum_required(VERSION 2.8.3)
project(planning)
set(CMAKE_CXX_STANDARD 17)

#变量和目录设置
#把动态库和可执行文件都指定到bin下面
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)
#CMAKE_ARCHIVE_OUTPUT_DIRECTORY 静态库 只会指定库的位置，而不考虑可执行文件


#动态库
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS)
add_library(common
SHARED
${SRC_LISTS}
)


target_include_directories(common
PUBLIC
${PROJECT_SOURCE_DIR}/include
)

#可执行文件
add_executable(planning_main planning_main.cpp)


target_include_directories(planning_main
PUBLIC
${PROJECT_SOURCE_DIR}/include
)

#链接
target_link_libraries(planning_main
PUBLIC
common
)
