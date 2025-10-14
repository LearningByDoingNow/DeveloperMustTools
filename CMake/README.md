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

## CMake 的set使用

如果每次编译可执行文件都这样写`add_executable(app add.cpp div.cpp main.cpp sub.cpp)`会很麻烦  
此时就可以定义一个变量用于存储即将要编译的文件名  在CMake里定义变量要使用`set`  

```cmake
# SET 指令语法：
#[] 中的参数可选 

SET （VAR [VALUE] [CACHE TYPE DOCSTRING [FORCE]]）

VAR : 变量名
VALUE ： 变量值  
```
```CMake
# 方法1 ： 源文件之间使用空格隔开
set (SRC_LIST add.c div.c main.c mult.c sub.c)
# 方法2 ：源文件之间使用;隔开
set(SRC_LIST add.c;div.c;main.c;mult.c;sub.c)
# 编译可执行文件 app为可执行文件名 $引用变量名 
add_executable(app ${SRC_LIST})

```  
**指定使用的c++标准**
1. 可以直接在使用g++编译的时候指定c++编译标准
`g++ *.cpp -std=c++11 -o app`
2. 在cmake中指定c++标准
    - 在CMakeLists.txt中通过set指定
    ```CMake
    # 增加-std=c++11
    set(CMAKE_CXX_STANDARD 11)
    # 增加-std=c++14
    set(CMAKE_CXX_SATANDARD 14)
    #   增加 -std=c++17
    set(CMAKE_CXX_STANDARD 17)
    ```
    - 在执行cmake命令的时候指定宏
    `cmake CMakeLists.txt_path -DCMAKE_CXX_SSTANDARD 17 `

**指定可执行文件输出路径**
在CMake中 有一个宏叫`EXECUTAVBLE_OUTPUT_PATH`可以通过`set`设置:
```CMake
set(HOME /home/cc/Linux/cmake)  # 定义一个存储home路径的变量
set(EXECUTABLE_OUTPUT_PATH ${home}/build) # 拼接好的路径给到宏 推荐相对路径
```  
