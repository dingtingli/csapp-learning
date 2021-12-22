# 使用 Linux 03 -- gcc

[之前的文章中](/使用Ubuntu01.md)我们介绍了在 Ubuntu 中如何安装图形应用 gedit，以及 [Windows 和 Ubuntu 两个系统之间如何访问各自的文件目录](/使用Ubuntu02.md)。

这次我们来尝试一个实用功能，在 Ubuntu 中安装并其使用 C 语言编译器 gcc。

## 安装 gcc

首先我们先尝试一下，系统中是否已经安装了 gcc

```cmd
gcc --version
```

![PNG01](/doc/illustrations/linuxuse03/win11gcc-01.png)

可以看到并没有安装，而且给出了安装命令 `sudo apt install gcc`。

接下来我们并没有直接使用提示给出的命令进行安装，而是按照下面链接给出的步骤，一次性安装 gcc 相关的所有内容。

https://linuxize.com/post/how-to-install-gcc-on-ubuntu-20-04/

先来检查一下当前 Ubuntu 的版本

```cmd
lsb_release -a
```

![PNG02](/doc/illustrations/linuxuse03/win11gcc-02.png)

`lsb_release`（Linux Standard Base）命令用来查看 Linux 内核的版本信息。

Linux 版本确认后，通过下面的命令来安装开发包。

```cmd
sudo apt install build-essential
```

![PNG03](/doc/illustrations/linuxuse03/win11gcc-05.png)

安装完成后再次检查 gcc 版本信息，一切正常。

![PNG04](/doc/illustrations/linuxuse03/win11gcc-07.png)

## 创建 c 语言代码文件

目标：在当前目录 `/home/terry` 下创建一个新的目录 `clang` ，然后在该目录中创建一个 c 语言文件 `printtest.c`。

我们尝试使用命令行来完成上述目标。

1. 创建新的目录

```cmd
mkdir clang
```

`mkdir` (Make Directory)，用于创建目录。

![PNG05](/doc/illustrations/linuxuse03/win11gcc-08.png)

Windows 文件管理器中可以查看到对应文件夹。

![PNG06](/doc/illustrations/linuxuse03/win11gcc-09.png)

2. 创建文件

```cmd
touch printtest.c
```
`touch` 用于修改文件或者目录的时间属性，如果文件不存在，那么将创建一个新的空白文件。

![PNG07](/doc/illustrations/linuxuse03/win11gcc-10.png)

通过 `ls` 命令发现我们把 printtest.c 这个文件的位置搞错了，需要将这个文件移到 clang 目录下面。

```cmd
mv printtest.c clang
```

`mv`（move file） 用来将文件或者目录改名，或者移入其他位置。
上述命令，将 printtest.c 移入 clang 目录。

```cmd
cd clang
```
同时通过 `cd`（change directory）进入该目录。

![PNG08](/doc/illustrations/linuxuse03/win11gcc-12.png)

![PNG09](/doc/illustrations/linuxuse03/win11gcc-13.png)

## 使用 Vim 编辑 c 语言文件

为了体验 Unix 文件编辑功能，我们将使用 vim 编辑器来编辑 c 语言文件。

Vim 的具体使用方法，可以参考下面这个链接：
https://www.runoob.com/linux/linux-vim.html

```cmd
vi printtest.c
```
通过上述命令进入 vim。进入后按一下字母 `i` 切换到输入模式。

![PNG10](/doc/illustrations/linuxuse03/win11gcc-14.png)

注意，此时左下方显示 `--INSERT--`，表示现在是输入模式。

输入 c 语言代码

```c
#include <stdio.h>

int main()
{
    long i = 1;
    printf("i = %ld", i);
    return 0;
}
```

![PNG11](/doc/illustrations/linuxuse03/win11gcc-15.png)

注意：编辑器对代码进行了高亮显示。

按 `ESC` 退出输入模式，然后输入 `:wq` 保存文件并退出。

![PNG12](/doc/illustrations/linuxuse03/win11gcc-16.png)

## 使用 gcc 编译 c 语言文件

使用 gcc 命令编译该文件：

```cmd
gcc printtest.c -o printtest
```

![PNG13](/doc/illustrations/linuxuse03/win11gcc-17.png)

最终在同一个目录下，会得到一个二进制文件 printtest。

![PNG14](/doc/illustrations/linuxuse03/win11gcc-18.png)

最后通过下面的命令来执行这个文件

```cmd
./printtest
```

![PNG15](/doc/illustrations/linuxuse03/win11gcc-20.png)

可以看到，命令行中输出了c 语言文件运行的结果 `i = 1`。

## 本文中使用的命令

1. lsb_release 
 
    英文全称：Linux Standard Base
 
    作用：查看 Linux 内核的版本信息。

2. mkdir
 
    英文全称：Make Directory

    作用：创建目录。

3. touch
 
    作用：用于修改文件或者目录的时间属性，如果文件不存在，那么将创建一个新的空白文件。

4. mv
 
    英文全称：Move file

    作用：将文件或者目录改名，或者移入其他位置。

5. cd

    英文全称：Change Directory

    作用：进入所选目录。

## 本文中使用的 vi 命令

1. vi filename

    作用：进入 vi 编辑环境，对选定文件进行编辑。

2. i

    作用：进入 vi 编辑环境的输入模式。

3. ESC

    作用：退出 vi 编辑环境的输入模式。

4. :wq

    作用：保存文件并退出 vi。

## 本文中使用的 gcc 命令

1. gcc --version

    作用：检查 gcc 的版本

2. gcc printtest.c -o printtest

    作用：编译 c 语言文件，并输出可执行的二进制文件