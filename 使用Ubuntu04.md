# 使用 Linux 03 -- VS Code

[上一篇文章](/使用Ubuntu03.md)中我们介绍了 gcc 编译器，并且尝试了在 Ubuntu 中使用 Vim 编辑器创建 c 语言文件。

命令行形式的编辑器毕竟太古老了。这次我们来介绍如何配合 Ubuntu 系统来使用 VS Code 编辑器。

## 安装 VS Code

首先，在 Windows 环境中安装 VS Code。

从官网下载最新版本，直接安装。具体步骤就不赘述了。

官网地址：https://code.visualstudio.com/

注意这是在 Windows 上安装的应用，现在看来跟我们在 WSL 中的 Ubuntu 系统毫无关系。

## Remote WSL

打开 VS Code，注意左下角是不是又绿色的 '><' 图标。

![PNG01](/doc/illustrations/linuxuse04/win11vscode-10.png)

如果没有，打开左侧导航中的 'Extensions'，搜索 'remote-wsl'。安装该插件后，就会出现上图中的界面。

![PNG02](/doc/illustrations/linuxuse04/win11vscode-11.png)

点击该绿色图标，就可以 Remote 之前安装的 WSL 系统了。

注：或者 'F1' 之后，搜索 'Remote-WSL'。

![PNG03](/doc/illustrations/linuxuse04/win11vscode-12.png)

图中有好几个选项。

Remote-WSL: New Window 是在新的 VS Code 窗口中 Remote WSL。

Remote-WSL: New Window using Distro 如果我们安装了多个 WSL 系统，这里可以选择。

我们这次选择 'Open Folder in WSL...'，弹出文件夹选择对话框。就像[之前介绍文件目录中](/使用Ubuntu03.md)说的那样，这里直接指向了 Ubuntu 所对应的目录。

![PNG04](/doc/illustrations/linuxuse04/win11vscode-13.png)

选择上一篇文章创建的 'clang' 目录然后确定。

![PNG05](/doc/illustrations/linuxuse04/win11vscode-14.png)

回到 VS Code 我们先着重注意一下左下角绿色的图标，已经变成了 '>< WSL:Ubuntu'，表示我们已经 Remote 到了 Ubuntu 中。

随意修改一个该目录中的文件，然后选择另存为 'Save As ...'。

![PNG06](/doc/illustrations/linuxuse04/win11vscode-15.png)

可以看到文件的保持路径是 Ubuntu 系统的文件目录。

## VS Code 中直接打开 Ubuntu 终端

在终端菜单 Terminal 中选择 'New Terminal'，或者使用快捷键 'Ctrl+Shift+`'。

![PNG07](/doc/illustrations/linuxuse04/win11vscode-16.png)

我们打开了一个新的 Ubuntu 命令行，这跟之前在 [Linux 准备]（/使用Ubuntu01.md）一文中所使用的终端是一样的。

![PNG08](/doc/illustrations/linuxuse04/win11vscode-17.png)

## Ubuntu 终端打开 VS Code

可以在 Ubuntu 终端使用下面的命令，直接打开 VS Code

```cmd
code .
```

![PNG09](/doc/illustrations/linuxuse04/win11vscode-18.png)

打开的 VS Code 就已经 Remote 到这个 WSL 中了。

## c 语言文件的代码格式化

VS Code 是一个更现代的代码编辑器，我们来试试其中一个功能——代码格式化。

打开一个 c 语言文件时，VS Code 会提示安装一个插件 'C/C++'。如果没有安装，可以在 'Extensions' 中搜索。

![PNG10](/doc/illustrations/linuxuse04/win11vscode-02.png)

注意插件名称下方的一行小字 'Extension is enabled on WSL:Ubuntu'，说明这是 Linux 版本的插件，从安装过程中的输出也可以看出来。

安装完插件后，使用快捷键 **'Shift+Alt+F' (或者 Ctrl+K+F)** 就可对输入的 c 语言进行格式化。

既然已经使用了先进的编辑器，那么我们接下来就试试如何在 vs code 中进行 debug 吧。

## 参考资料

[1] https://code.visualstudio.com/docs/remote/wsl#_getting-started

[2] https://code.visualstudio.com/docs/remote/wsl-tutorial