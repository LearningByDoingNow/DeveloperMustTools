# 这是一个CMake 文件 CMakeLists.txt
#[[
可以在VScode 安装一个plug 名为 CMake 可以自动补全 描述性脚本语言
]]
cmake_minimum_required(VERSION 3.15)
project(test)
add_executable(app add.cpp div.cpp main.cpp sub.cpp)


