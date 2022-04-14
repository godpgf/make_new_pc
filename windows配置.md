# 配置

## 一、c++环境

### 1、shell环境

下载([MSYS2](https://www.msys2.org/))

打开快捷方式"MSYS2 MSYS"执行以下语句配置gcc环境
```shell
pacman -Syu # 更新一下库
# 下载c++环境，也可以手动选择：pacman -S mingw-w64-x86_64-toolchain
pacman -S mingw-w64-x86_64-gcc mingw-w64-x86_64-gdb mingw-w64-x86_64-make
# 然后我们测试一下，添加环境变量
# export PATH=$PATH:/mingw64/bin/
# 配置环境变量PATH=C:\msys64\mingw64\bin
gcc -v #如果这一步成功显示版本，这次真就恭喜你了
# 注意，clion里面也会有一个mingw64，不要使用它，在clion的settings--toolchains把默认的mingw64干掉
```

### 2、安装cmake

下载安装([cmake](https://cmake.org/download/))

### 3、编译protobuf

下载([protobuf release](https://github.com/protocolbuffers/protobuf/releases/download/v3.20.0/protobuf-all-3.20.0.zip))

配置cmake
```text
配置cmake路径：protobuf路径\cmake
配置输出路径：protobuf路径\mingw-build
点击config，选择:MinGW Makefiles
点击Specify native compilers
设置编译器：
C编译器：C:/msys64/mingw64/bin/gcc.exe
C++编译器：C:/msys64/mingw64/bin/g++.exe
设置输出目录：CMAKE_INSTALL_PREFIX=C:/lib/protobuf
不编译测试程序：protobuf_BUILD_TEST=OFF
protobuf_MSVC_STATIC_RUNTIME=OFF
protobuf_BUILD_PROTOC_BINARIES=ON
DCMAKE_BUILD_TYPE=Release
# CMake_CXX_FLAGS中填入-std=gnu++11
改完点击：Configure、Generate
```

编译：
```shell
cd protobuf路径\mingw-build
mingw32-make
mingw32-make install
```

### 4、安装opencv

下载([opencv](https://opencv.org/releases/))
安装到D:\\opencv
下载对应版本的人家编译好的库（不用自己编译了）([opencv_mingw64](https://github.com/huihut/OpenCV-MinGW-Build/releases))
将库放到安装路径下，设置环境变量：OpenCV_DIR=D:\\opencv


### 5、编译ncnn
下载([ncnn源码](https://github.com/Tencent/ncnn/archive/refs/tags/20220216.zip))

配置cmake
```text
配置cmake路径：ncnn路径
配置输出路径：ncnn路径\mingw-build
点击config，选择:MinGW Makefiles
点击Specify native compilers
设置编译器：
C编译器：C:/msys64/mingw64/bin/gcc.exe
C++编译器：C:/msys64/mingw64/bin/g++.exe
设置输出目录：CMAKE_INSTALL_PREFIX=C:/lib/ncnn
CMAKE_BUILD_TYPE=Release
Protobuf_INCLUDE_DIR=C:/lib/protobuf/include
Protobuf_LIBRARIES=C:/lib/protobuf/lib/libprotobuf.a
Protobuf_PROTOC_EXECUTABLE=C:/lib/protobuf/bin/protoc.exe
NCNN_VULKAN=OFF
NCNN_AVX2=OFF
NCNN_SSE2=OFF
NCNN_BUILD_EXAMPLES=OFF
# NCNN_SIMPLEOMP=ON
# 不使用openmp
NCNN_OPENMP=OFF
Protobuf_MSVC_STATIC_RUNTIME=OFF
点击：Configure、Generate
```
安装
```shell
cd ncnn路径\mingw-build
mingw32-make
mingw32-make install
# 运行以下语句就可以生成ncnn格式文件了
onnx2ncnn version-slim-640.onnx version-slim-640.param version-slim-640.bin
```
