# 基础

编译源文件：`CMakeLists.txt`
CMake里面变量默认都是字符串
# 宏

+ `CMAKE_CXX_STANDARD`：C++编译标准
+ `EXECUTABLE_OUTPUT_PATH`：可执行程序输出路径
+ `PROJECT_SOURCE_DIR`：执行cmake命令时后面跟随的路径
+ `PROJECT_BINARY_DIR`：执行cmake命令时所在的路径
+ `CMAKE_CURRENT_SOURCE_DIR`：当前CMakeLists.txt文件所在路径
+ `LIBRARY_OUTPUT_PATH`：库文件生成路径

# 命令

编译
+ `cmake 路径`：使用CMake编译指定的路径，生成的各种文件在执行该命令的地方 
	+ `-D宏名=值`：将CMake中的宏的值指定为等号后面的值
+ `make`：使用make去编译CMake生成的makefile

文件内命令
+ `# 注释`：注释
	+ `#[[注释]]`：块注释
+ `cmake_minimum_required(VERSION 3.0)`：指定使用CMake的最低版本为3.0
+ `project(工程名)`：定义工程名字为工程名
	+ `PROJECT-NAME`：项目名称
	+ `VERSION`：项目版本
	+ `DESCRIPTION`：项目描述
	+ `HOMEPAGE_URL`：博客网址
	+ `LANGUAGES`：开发语言
+ `add_excutable(可执行程序名 源文件)`：指定可执行程序名和参与编译的源文件
+ `set(变量名 变量值)`：定义或指定一个变量名，值为变量值
	+ 第一个变量名为宏，则是设置宏的值
+ `${变量名}`：获取变量名的值
+ `aux_source_directory(文件的路径 变量名)`：将文件的路径中的文件添加到变量名中
+ `file(选项 变量名 文件的路径/后缀)`：将文件路径中的文件，根据选项赋值给变量名
	+ 选项：
		+ `GLOB`：当前的指定的目录的所有文件
		+ `GLOB_RECURSE`：递归搜索当前指定的目录及以内的所有文件
	+ 后缀：
		+ 如：`*.cpp`：所有的cpp后缀的文件
+ `include_directories(文件路径)`：添加头文件的包含路径
+ `add_library(库名称 选项 源文件)`：指定生成库的名字和源文件，根据选项生成不同的库文件
	+ 选项
		+ `STATIC`：静态库
		+ `SHARED`：动态库
+ `link_libraries(库文件)`：添加需要链接的库文件
+ `target_link_libraries(需要链接的文件 库文件)`：给需要链接动态库的文件添加动态库文件
+ `link_directories(路径)`：添加链接库的文件路径
+ `message(选项 "日志")`：打印日志
	+ 选项
		+ `无`：重要信息
		+ `STATUS`：非重要信息
		+ `WARNING`：CMake警告，会继续执行
		+ `AUTHOR_WARNING`：CMake警告（dev），会继续执行
		+ `SENO_ERROR`：CMake警告，继续执行，但是会跳过生成的步骤
		+ `FATAL_ERROR`：CMake警告，终止所有处理过程
+ `list(选项 值1 值2 值3)`：对值123操作
	+ 选项
		+ `APPEND`：值23追加给值1
		+ `REMOVE_ITEM`：值2移除值3给值1
		+ `LENGTH <list> value`：获取列表长度
		+ `GET <list> [index] output`：读取列表中指定索引的元素
		+ `JOIN <list> <glue> output`：将列表中的元素用连接符连接起来
		+ `FIND <list> <value> output`：查找list中有无value，没有返回-1
		+ `APPEND <list> element`：element追加到list
		+ `INSERT <list> <index> element`：element添加到list
		+ `PREPEND <list> element`：element添加到头节点
		+ `POP_BACK <list> value`：移除最后一个元素并赋值到value
		+ `POP_FRONT <list> value`：移除第一个元素并赋值到value
		+ `POP_FRONT <list> value`：移除第一个元素并赋值到value
		+ `REMOVE_ITEM <list> value`：移除指定元素
		+ `REMOVE_AT <list> index`：移除指定位置
		+ `REMOVE_DUPLICATES <list>`：移除列表中发重复元素
		+ `REVERSE <list>`：列表翻转
		+ `SORT <list> [COMPARE] [CASE] [ORDER]`：列表排序
			+ COMPARE
				+ STRING：按照字母顺序进行排序，为默认的排序方法
				+ FILE_BASENAME：如果是一系列路径名，会使用basename进行排序
				+ NATURAL：使用自然数顺序排序
			+ CASE
				+ SENSITIVE: 按照大小写敏感的方式进行排序，为默认值
				+ INSENSITIVE：按照大小写不敏感方式进行排序
			+ ORDER
				+ ASCENDING：按照升序排列，为默认值
				+ DESCENDING：按照降序排列
+ `add_definitions(-D宏)`：添加宏定义