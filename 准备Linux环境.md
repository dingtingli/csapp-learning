# 准备 Linux 环境

我们可以在物理机上直接安装 Linux 发行版，也可以在 VMWare 或者 Hyper-V 等虚拟机软件上安装。

但自从微软发布 WSL（Windows SubSystem for Linux）之后，我一直希望尝试一下，所以这次将使用 WSL 来安装 Linux。

WSL 本身也是基于虚拟机技术的，它最大的优势大概是可以方便地在 Windows 中使用 Linux。

我自己对 Linux 没有任何使用经验，所以这篇文章是以一个初学者的视角，记录每一步安装配置的过程。

## 升级 Windows 11

为了可以使用 GUI，也就是 Linux 中的图形界面，我们需要先将操作系统升级到 Windows 11。

详情需求可以参考如下链接：
https://docs.microsoft.com/zh-cn/windows/wsl/tutorials/gui-apps

### 1. 检查是否可以升级

微软目前还没有全面推送 Windows 11 的更新，所以需要手动将 Windows 10 更新到 11。

首先需要检查当前的机器是否可以升级到 Windows 11。从下面的链接下载一个应用。

https://www.microsoft.com/zh-cn/windows/windows-11?r=1#pchealthcheck

安装后运行，就可以确实是否可以升级。

![PNG01](/doc/illustrations/linuxpre/win11Update-01.png)

### 2. 安装升级包

手动下载 Windows 11 更新包。

https://www.microsoft.com/zh-cn/software-download/windows11

直接安装即可，整个过程大概需要 30 分钟。

![PNG02](/doc/illustrations/linuxpre/win11Update-02.png)

## 安装 WSL

现在我们已经将系统升级到 Windows 11，接下来就可以安装 WSL 了。

### 1. 升级显卡驱动

首先我们需要升级适用于 WSL 的虚拟显卡驱动。这一步主要是为了使用 Linux 中的图像界面，如果不需要，可以跳过这一步。

下面链接中提供了 Intel ，AMD 和 NVIDIA 的相关显卡驱动的下载地址。
https://docs.microsoft.com/zh-cn/windows/wsl/tutorials/gui-apps

我这里安装的是 Intel 的驱动。

![PNG03](/doc/illustrations/linuxpre/win11wsl-01.png)

### 2. 安装 WSL

打开 Windows 命令行，或者 Windows 终端，输入命令

```cmd
wsl --list --online
```

![PNG04](/doc/illustrations/linuxpre/win11wsl-03.png)

就会列出所有可以安装的 Linux 发行版本，默认是 Ubuntu。

通过下面的命令直接安装 Ubuntu。

```cmd
wsl --install
```

![PNG05](/doc/illustrations/linuxpre/win11wsl-05.png)

从命令提示中也可以看到 GUI 相关的内容。

![PNG06](/doc/illustrations/linuxpre/win11wsl-07.png)

下载完成后需要重启电脑。重启后会直接弹出 Ubuntu 的命令行界面。

![PNG07](/doc/illustrations/linuxpre/win11wsl-08.png)

按照提示输入用户名和密码。
![PNG08](/doc/illustrations/linuxpre/win11wsl-11.png)

*注意：1，该用户为系统管理员。 2. Linux 默认系统用户 root 的密码是随机的，每次开机都有一个新的密码，如果希望修改可以参考[这篇文章](https://www.jianshu.com/p/e43e11d6ba09)。

安装完成后，如下图所示，出现命令行。

![PNG09](/doc/illustrations/linuxpre/win11wsl-12.png)

到这一步，WSL 就已经安装好了。我们已经在 Windows 中安装了一个 Linux 子系统 Ubuntu。

接下来就开始一步步探索如何使用这个 Linux 系统吧。