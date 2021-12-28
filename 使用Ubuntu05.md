# WSL 06 -- gdb

[上一篇文章](/使用Ubuntu04.md)中介绍了如何通过 VS Code Remote 到 WSL 的 Ubuntu 系统中，通过这种形式我们就在 Windows 系统中配置了一个 Linux 开发环境。

这篇文章，我们接着来看看如何在 VS Code 中调用安装在Ubuntu中 c 语言的调试工具 gdb，从而实现在 VS Code 中实现调试功能。

## 安装 gdb

我们先用下面的命令来检查一下 Ubuntu 中是否已经安装有 gdb。

```cmd
gdb --version
```

![PNG01](/doc/illustrations/linuxuse05/win11vscode-03.png)

命令结果显示并没有安装，因此通过下面的命令来安装 gdb。

```cmd
sudo apt install gdb
```

注意：有些文章中会用 `sudo apt-get install gdb` 命令来安装，`apt` 命令是 `apt-get` 命令的新版本，具体二者有什么不同，可以参考文章：https://zhuanlan.zhihu.com/p/350690109

安装完成后，可以使用 `gdb --version` 检查一下。

![PNG02](/doc/illustrations/linuxuse05/win11vscode-06.png)

## 测试 gdb 功能

在介绍 [gcc 的文章](/使用Ubuntu03.md)中，我们创建了一个 c 语言文件 printtest.c

```c
#include <stdio.h>

int main()
{
    long i = 1;
    printf("i = %ld \n", i);
    return 0;
}
```
并且使用 gcc 命令，生成了一个二进制文件 printtest

```cmd
gcc printtest.c -o printtest
```

这次我们就用这个二进制 printtest 文件来测试一下 gdb 的反编译功能。

进入到文件所在目录后，使用如下命令。

```cmd
gdb printtest
```

![PNG03](/doc/illustrations/linuxuse05/win11gdb-01.png)

然后在 (gdb) 中输入

```cmd
disassemble main
```

![PNG04](/doc/illustrations/linuxuse05/win11gdb-02.png)

main 函数的汇编代码就直接打印在屏幕上。

如果需要退出，可以在 (gdb) 后面输入 `quit`，直接退回到命令行。

## VS code 中使用 gdb

从上面的测试中我们可以看到 gdb 是一个命令行模式的调试工具，使用起来比较麻烦。但是它功能很强大，如果可以结合 VS Code 窗口功能，将会非常方便。

通过[上一篇介绍 VS Code 的文章](/使用Ubuntu04.md)所讲的方法，在 VS Code 中 打开 clang 目录，然后创建一个新的 c 语言文件 msstore.c 并保存。

```c
#include <stdio.h>

long mult2(long a, long b)
{
    long s = a * b;
    return s;
}

void multstore(long x, long y, long *dest)
{
    long t = mult2(x, y);
    *dest = t;
}

int main()
{
    long d;
    multstore(2, 3, &d);
    //printf("2 * 3 --> %ld\n", d);
    return 0;
}
```

在语句 `multstore(2, 3, &d);` 前设置断点（点击语句左侧的行标）。

![PNG05](/doc/illustrations/linuxuse05/win11gdb-03.png)

然后选择菜单 'Run' -> 'Start Debuging' (或者按快捷键 F5)。

![PNG06](/doc/illustrations/linuxuse05/win11gdb-04.png)

因为已经安装了 'c/c++'插件，此时 VS Code 会自动生成一个 .vscode 的目录，目录下有两个配置文件 launch.json 和 task.json。

其中 launch.json 就是 debug 在 VS Code 中的配置文件。

![PNG07](/doc/illustrations/linuxuse05/win11gdb-05.png)

从中可以看到 gdb 的安装路径 '/usr/bin/gdb'，这也是为什么需要先安装 gdb 的原因，否则会因为在相应路径下将找不到 gdb 而报错。

因为我们已经准备就绪，所以此刻就直接进入 debug 模式

![PNG08](/doc/illustrations/linuxuse05/win11gdb-06.png)

跟大多数编译器一样，此时使用 'F11' 可以跳入相应函数，'F10' 可以一步一步地跟踪代码的执行。

同时，VS Code 的左侧还有程序运行时的各种状态。

![PNG09](/doc/illustrations/linuxuse05/win11gdb-07.png)

比如我们可以看到函数中各个变量的值，以及CPU 寄存器中状态等等。

这样，我们就在 Windows 系统中配置了一个 Linux 开发环境，无缝地使用 Linux 带来的开发工具。

## 参考资料

[1] https://code.visualstudio.com/docs/cpp/config-wsl

[2] https://code.visualstudio.com/docs/languages/cpp