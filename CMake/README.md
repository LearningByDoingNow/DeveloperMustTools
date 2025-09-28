# CMake Learning

## make 操作
> 我新建了几个文件夹 用于测试 cmake and make
![alt text](/CMake/images/1.png)

1. 构建好`源文件` `头文件` 以后 编写 `CMakeLists.txt`
2. `cmake_minimum_required(VERSION 3.15) `表示`cmake`最低版本
3. `project(test)` 表示项目名
4. `add_executable(app add.cpp div.cpp main.cpp sub.cpp)` 表示构建可执行文件 也就是预编译 编译 
5. 准备好以后 新建一个`build` folder
6. 在build中 `cmake ..`
7. 然后直接`make`即可 

