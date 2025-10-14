# 这是一个CMake 文件 CMakeLists.txt 
#[[
可以在VScode 安装一个plug 名为 CMake 可以自动补全 描述性脚本语言
]]
cmake_minimum_required(VERSION 3.15)
project(test)
# 设置 源文件变量
set(TEST add.cpp div.cpp main.cpp sub.cpp)
# 设置可执行文件输出文件路径
set(EXECUTABLE_OUTPUT_PATH /mnt/e/DeveloperMustLearnTools/CMake)
add_executable(app ${TEST})


