# WSL Installation and Configuration

## WSL 安装

参考微软官方教程[如何使用 WSL 在 Windows 上安装 Linux](https://learn.microsoft.com/zh-cn/windows/wsl/install)

```PowerShell
# 管理员模式下运行
wsl --install
# 若执行上述指令提示WslRegisterDistribution failed with error: 0x800701bc，则更新 WSL
wsl --update
```

执行完成上述操作后重启电脑，重启后在终端中打开 Ubuntu 标签页。标签页中会显示正在安装，安装完成后指定用户名和密码即可开始使用

安装完成后可以通过 `lsb_release -a` 确认安装的 Ubuntu 版本。如果想要更换安装版本可以重新安装新的发行版

## WSL 软件安装

软件安装与直接在 Ubuntu 系统下安装软件有相似之处。在安装软件之前，可以先执行小鱼一键换源[小鱼的一键安装系列](https://fishros.org.cn/forum/topic/20/%E5%B0%8F%E9%B1%BC%E7%9A%84%E4%B8%80%E9%94%AE%E5%AE%89%E8%A3%85%E7%B3%BB%E5%88%97)加快软件安装速度。此外，还可以使用小鱼一键安装 Docker

```PowerShell
wget http://fishros.com/install -O fishros && . fishros
# 选择 5 更换系统源 - 1 仅更换系统源 - 2 不添加 ROS/ROS2 源
# 选择 8 一键安装 Docker
# 选择 13 更换 Python 源
```

### Miniconda

Miniconda 的安装与配置可以参考[Miniconda Installation and Configuration on Ubuntu](Miniconda_Installation_and_Configuration_on_Ubuntu.md)

### CUDA 和 cuDNN

CUDA 和 cuDNN 的安装与配置可以参考[CUDA and cuDNN Installation](CUDA_and_cuDNN_Installation.md)

### Git

Git 的安装与配置可以参考[Git Configuration and Command](Git_Configuration_and_Command.md)

### 开发环境搭建

C++ 环境的配置可以参考[C++ Development Environment Configuration](C++_Development_Environment_Configuration.md)

## WSL 卸载

如果不想再使用 WSL 了，可以卸载 WSL。

1. 终端内执行 `wsl --unregister <发行版名称>`
2. 在 `设置 - 应用 - 应用与功能` 中搜索 Ubuntu 并卸载相关软件
3. 在控制面板中点击 `程序 - 程序和功能 - 启用或关闭 Windows 功能`
4. 取消勾选 `适用 Linux 的 Windows 子系统`，重启后即完成卸载
