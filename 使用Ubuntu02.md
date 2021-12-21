# 使用 Linux 02 -- 访问文件目录

在[上一篇文章](/使用Ubuntu01.md)中我们安装了 gedit 应用。通过该应用，可以快速地浏览 Ubuntu 系统中的目录结构。

点击左上角的 Open

![PNG01](/doc/illustrations/linuxuse01/win11wsl-40.png)


快速查看文件目录结构

![PNG02](/doc/illustrations/linuxuse02/win11wsl-24.png)

可以看到这就是 Linux 系统的标准目录结构，跟当前 Windows 系统中的文件夹没有什么关系。

## 在 Windows 中如何访问 Ubuntu 中的目录结构

虽然 Ubuntu 是安装在 Windows 中的子系统，看上去也像是 Windows 中的一个应用。但 Ubuntu 和这个 Windows 的关系，仍然是两个不同系统之间的关系，这种关系跟在 Windows 中通过 VMWare 安装一个 Ubuntu 系统是类似的。

所以想通过 Windows 访问 Ubuntu 中的目录结构，可以通过共享文件夹的方式来进行。

WSL 为这种访问方式提供了两种便利的入口。

1. 通过命令行

```cmd
explorer.exe .
```

在命令行中输入 `explorer.exe .` (注意最后面的小点)，就会在Windows 中弹出文件资源管理器，访问 Ubuntu 中的目录。

![PNG03](/doc/illustrations/linuxuse02/win11wsl-26.png)

2. 文件资源管理器中直接打开

通过 WSL 安装好 Ubuntu 系统之后，在 Windows 的文件资源管理器中可以看到，在左侧导航的最下放有一个 Linux 图标。

![PNG04](/doc/illustrations/linuxuse02/win11wsl-31.png)

点击后也可以访问 Ubuntu 中的目录。

## 测试：在 Windows 和 Ubuntu 中修改同一份文件

1. Windows 中创建文件

既然可以在 Window 的文件资源管理器中打开 Ubuntu 的目录，我们就测试一下在 Windows 和 Ubuntu 中同时修改一份文件。

首先，通过 Windows 系统在 '/home/terry' 目录下创建一个文件 'test.txt'。

![PNG05](/doc/illustrations/linuxuse02/win11wsl-28.png)

2. Ubuntu 中修改文件

然后在 Ubuntu 的命令行中确认该文件是否存在。

```cmd
ls
```

![PNG06](/doc/illustrations/linuxuse02/win11wsl-29.png)

`ls` 命令将显示指定工作目录下之内容，可以看到只有一个文件'test.txt'，其他以 `.` 开头的文件或者文件夹都不显示。

输入以下命令，通过 gedit 打开 'test.txt' 文件。

```cmd
sudo gedit text.txt
```

直接使用 `gedit text.txt` 命令，会显示没有权限保存，所以前面加上 `sudo` ，表示使用管理员权限打开。

![PNG07](/doc/illustrations/linuxuse02/win11wsl-32.png)

在文件中输入 “from ubuntu.” 后保存。

3. Windows 中修改同一份文件

在 Windows 中用笔记本打开 'test.txt' 文件，可以看到上一步输入的 “from ubuntu.”。

在文件中输入  “from windows.” 后保存。

![PNG08](/doc/illustrations/linuxuse02/win11wsl-36.png)

4. Ubuntu 中确认 

通过 gedit 打开文件，确认结果。

![PNG09](/doc/illustrations/linuxuse02/win11wsl-38.png)


## 在 Ubuntu 中如何访问 Windows 中的目录结构

上面介绍了如何在 Windows 中访问 Ubuntu 的目录结构，那么反过来，如何在 Ubuntu 中访问 Windows 中的文件夹呢？

之前看过 Linux 系统根目录下面的文件夹。

![PNG03](/doc/illustrations/linuxuse02/win11wsl-26.png)

其中有一个文件夹叫做 `mnt`，点开后就可以看到如下目录结构：

![PNG04](/doc/illustrations/linuxuse02/win11wsl-41.png)

这里的 `c` 就是指 Windows 系统中的 C 盘，如果机器中有其他盘符，这里就会看到对应的 `d`，`e`等等。

![PNG05](/doc/illustrations/linuxuse02/win11wsl-42.png)

这种访问方式太神奇，可以直接通过 Linux 命令管理 windows 文件系统。

## 本文中使用的命令

1. ls 
 
    英文全称：List Files
 
    作用：显示指定工作目录下之内容。