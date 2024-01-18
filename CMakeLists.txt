#cmake最低版本
cmake_minimum_required(VERSION 3.5)     

#工程名字
project(Hello_World)            

#打印信息
message(STATUS "-----------------------cmake start [${PROJECT_NAME}]--------------------------------")

#设置c c++编译器
set(CMAKE_C_COMPILER "gcc")
set(CMAKE_CXX_COMPILER "g++")

#库文件路径
set(LIB_A_PATH "${PROJECT_SOURCE_DIR}/lib/lib_a")
set(LIB_SO_PATH "${PROJECT_SOURCE_DIR}/lib/lib_so")

#设置编译模式   Debug(断点有效)/Release
set(CMAKE_BUILD_TYPE "Release")

#设置链接库路径
set(LIB ${LIB_A_PATH}
        ${LIB_SO_PATH}
    )
link_directories(${LIB})

#设置头文件路径
include_directories(${PROJECT_SOURCE_DIR}/test1
                    ${PROJECT_SOURCE_DIR}/test2
                    )

#设定源文件路径,获取路径下所有源代码
#aux_source_directory(${PROJECT_SOURCE_DIR} SRC_LIST)
aux_source_directory(${PROJECT_SOURCE_DIR}/test1 SRC_LIST)
#aux_source_directory(${PROJECT_SOURCE_DIR}/test2 SRC_LIST)

#设置可执行文件路径
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR})

#生成可执行文件
add_executable(${PROJECT_NAME} ${SRC_LIST})

#链接的库
target_link_libraries(${PROJECT_NAME}
                        #-lpthread
                        #可连续写入    
                    )


