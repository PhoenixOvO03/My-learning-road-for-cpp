# 基础

编译源文件：`CMakeLists.txt`
CMake里面变量默认都是字符串
# 宏

+ `CMAKE_CXX_STANDARD`：C++标准

# 命令

+ `cmake xxx xxx...`：使用CMake编译一系列需要参与CMake编译的源文件
	+ `-D宏名=值`：将CMake中的宏的值指定为等号后面的值
+ `cmake_minimum_required(VERSION 3.0)`：使用CMake的最低版本
+ `project(TEST)`：定义工程名字为TEST
	+ `PROJECT-NAME`：项目名称
	+ `VERSION`：项目版本
	+ `DESCRIPTION`：项目描述
	+ `HOMEPAGE_URL`：博客网址
	+ `LANGUAGES`：开发语言
+ `add_excutable(app xxx.h xxx.cpp)`：生成可执行程序app，源文件为xxx.h和xxx.cpp
+ `set(xxx_list xxx.h xxx.cpp)`：定义一个变量xxx_list，值为xxx.h和xxx.cpp
	+ 第一个变量名为宏，则是设置宏的值
+ `${变量名}`：获取变量名的值