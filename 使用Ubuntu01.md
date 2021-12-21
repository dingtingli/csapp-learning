# Linux 使用 01 -- GUI APP



在[前面一篇文章](/准备Linux环境.md)中，我们已经介绍了如何通过 WSL 安装 Ubuntu。

接下来我们就来探讨如和使用这个系统。

## 测试命令

安装完成之后，会出现一个命令行。

![PNG01](/doc/illustrations/linuxuse01/win11wsl-12.png)

这就是 Ubuntu 的使用界面，这里可以输入任何有效的 Linux 命令。

比如，我们输入以下命令，用来查看当前所在的目录。

```cmd
pwd
```

![PNG02](/doc/illustrations/linuxuse01/win11wsl-13.png)

可以看到 `/home/terry`，说明是在 home 下面叫 terry 的文件夹下。

## 打开 Ubuntu

当前所在的这个窗口就是 Ubuntu 系统的入口。**我们在 Windows 中如何打开这个窗口呢？**

在 Windows 中，把安装后的 WSL 子系统当作一个应用程序来看待，因此我们可以在开始菜单中找到它。

![PNG03](/doc/illustrations/linuxuse01/win11wsl-17.png)

点击该应用图标就可以打开命令行窗口。

*注意：使用 windows 终端也可以打开该系统的命令行。

## 测试 GUI

这样的使用体验和在虚拟机中直接安装一个 Ubuntu 还是很不一样的。

1. 首先，我们只能看到 Ubuntu 的命令行入口，这个系统内部的图像界面应用如何安装和使用？

2. 其次，这个系统很像是 Windows 中的一个应用，上面看到的文件目录 `/home/terry` 在哪？它跟 Windows 系统中的文件夹有什么关系？

我们先来看第一个问题，关于第二个问题，下一篇文章再回答。

### 1. Ubuntu 中如何安装 GUI 应用

在 Ubuntu 中，使用命令 `apt` 来管理前端软件包（Advanced Packaging Tool）

该命令需要以系统管理员的身份运行，而命令 `sudo` (Super User do) 允许以系统管理员的身份运行命令。

所以我们可以组合这两个命令 `sudo apt`——以系统管理员的身份运行 `apt`命令。

为了测试 GUI，我们选择了 gedit 这个应用，该应用类似于 windows 中的系统应用 notepad （记事本）。

通过下面命令来安装 gedit 应用

```cmd
sudo apt install gedit -y
```

其中 `-y` 的意思是，安装过程中的提示全部选择“yes”。

![PNG04](/doc/illustrations/linuxuse01/win11wsl-18.png)

图中该命令上面的显示，是命令 `sudo apt update` 的结果（列出所有可更新的软件清单）。

开始安装 gedit，命令行中先是显示一堆 Get 信息

![PNG05](/doc/illustrations/linuxuse01/win11wsl-19.png)

然后显示进度条

![PNG06](/doc/illustrations/linuxuse01/win11wsl-20.png)

安装完成后，回到命令行

![PNG07](/doc/illustrations/linuxuse01/win11wsl-21.png)

gedit 应用就安装完成了。

### 2. Ubuntu 中如何打开 GUI 应用

通过上面的步骤，我们在 Ubuntu 中安装了一个图形界面应用 gedit。

**如何打开这个应用？**

在命令行中输入

```cmd
gedit
```

*如果觉得之前的命令使得命令行显示的信息太多，可以使用 `clear` 命令来清空所有信息。下面的截图，在输入 gedit 之前，就使用 clear 清空过。

![PNG08](/doc/illustrations/linuxuse01/win11wsl-22.png)

神奇的事情发生了，在 Windows 系统中弹出了 gedit 的图形界面。

注意是在 Windows 系统中，这就跟你在 windows 中打开记事本的感觉是一样的。

![PNG09](/doc/illustrations/linuxuse01/win11wsl-40.png)

除了通过命令行来打开 gedit 之外，我们甚至可以在开始菜单中找到打开该应用的入口。

![PNG09](/doc/illustrations/linuxuse01/win11wsl-39.png)

可以发现 WSL 的设计者，不仅仅希望子系统 Ubuntu 看起来像是一个 windows 应用，还希望该系统下的应用看起来也像一个 windwos 应用。太魔性了！

这让我对之前的第二个问题更感兴趣了——**两个系统的文件目录是如何在一起工作的？**

## 本文中使用的命令

1. pwd 
 
    英文全称：Print Work Directory
 
    作用：显示工作目录。

2. clear
 
    作用：清除屏幕。

3. sudo
 
    英文全称：Super User do
 
    作用：以系统管理者的身份执行指令

4. apt
 
    英文全称：Advanced Packaging Tool
 
    作用：前端软件包管理工具（ Debian / Ubuntu 中使用）

