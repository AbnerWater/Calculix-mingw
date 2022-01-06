# Calculix-mingw

## 项目介绍

使用MINGW64在Windows环境下编译CalculiX

## 编译环境

- [MSYS2][0]
- [MINGW64][1] 下载解压后放入MSYS2安装目录下
- [MINGW32][2] 下载解压后放入MSYS2安装目录下

[0]:https://github.com/msys2/msys2-installer/releases/download/2021-11-30/msys2-x86_64-20211130.exe
[1]:https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win64/Personal%20Builds/mingw-builds/8.1.0/threads-win32/sjlj/x86_64-8.1.0-release-win32-sjlj-rt_v6-rev0.7z
[2]:https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win32/Personal%20Builds/mingw-builds/8.1.0/threads-win32/sjlj/i686-8.1.0-release-win32-sjlj-rt_v6-rev0.7z

## 编译命令

- ARPACK 

    打开ARPACK/ARmake.inc,做如下修改：

    ```
    #home修改为ARPACK目录当前绝对路径
    home = C:/000_STUDY/Calculix-mingw/ARPACK
    ```

    打开mingw64命令行执行编译指令：

    ```
    cd ARPACK
    make all
    ```

- SPOOLES.2.2

    ```
    cd SPOOLES.2.2
    make lib
    ```

- Calculix

    ```
    cd ccx_2.17/src
    make
    ```