#要求cmake的最低版本
cmake_minimum_required (VERSION 3.0)
#工程名称
project(opencv_test)
#将头文件包含到搜索路进
include_directories(include)
#设置一个变量，其值为之后的源文件路进，多个文件时用空格割断。
set(NEED yolo.cpp)
#寻找第三方库，如果第三方库附有Find<LIB_NAME>.cmake文件，则可以直接倒入，如果没有，则需要link_directories()完成链接。
find_package(OpenCV REQUIRED)
#将第三方库加入到搜索路进
include_directories(${OpenCV_INCLUDE_DIRS})
#生成可执行文件，将所需源文件链接。
add_executable(aa ${NEED})
#链接第三方库文件
link_directories(${OpenCV_LIBRARY_DIRS})
target_link_libraries(aa ${OpenCV_LIBS})