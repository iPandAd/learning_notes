# Miniconda Installation and Configuration on Ubuntu

## 安装

Ubuntu 下可以选择安装 Miniconda/Anaconda/Miniforge 中的一个，安装 Miniconda 可以节省硬盘空间（约 400MB，Anaconda 需要 3GB），大部分需要的包自行安装。

安装教程：[Installing on Linux](https://conda.io/projects/conda/en/latest/user-guide/install/linux.html)

```bash
mkdir -p ~/miniconda3
cd miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh
```

1. [下载安装包](https://docs.anaconda.com/free/miniconda/)

2. 验证哈希值`sha256sum filename`

3. 安装程序`bash <conda-installer-name>-latest-Linux-x86_64.sh`

4. 修改环境变量

   ```shell
   sudo gedit ~/.bashrc
   # 最后一行添加 export PATH=~/miniconda3/bin:$PATH
   source ~/.bashrc
   ```

5. `conda init`激活环境

## 常用命令

[conda-cheatsheet](https://conda.io/projects/conda/en/latest/_downloads/843d9e0198f2a193a3484886fa28163c/conda-cheatsheet.pdf)

```shell
# 验证 conda 安装，检查版本
conda info
# 基本环境中更新 conda
conda update -n base conda
# 创建指定 Python 版本的新环境
conda create -n ENVNAME python=3.10
# 激活环境
conda activate ENVNAME
# 列出已安装的包及源信息
conda list --show-channel-urls
# 更新所有安装的包
conda update --all
# 安装特定版本的包
conda install PKGNAME=X.X.X
# 卸载安装的包
conda uninstall PKGNAME
# 列出所有虚拟环境
conda env list
# 在虚拟环境中安装包
conda install -n ENVNAME PKG1 PKG2
# 克隆环境
conda create --clone ENVNAME -n NEWENV
# 帮助文档
conda COMMAND --help
# 删除环境
conda remove -n ENVNAME --all
# 记录环境微调版本
conda install -n ENVNAME --revision NUMBER
```

## 卸载

卸载教程：[Ubuntu 彻底删除 Anaconda/Miniconda](https://blog.csdn.net/weixin_43152331/article/details/133804224)

```shell
# 删除安装文件夹
rm -rf ~/miniconda
# 删除.bashrc 中 conda 相关配置
sudo gedit ~/.bashrc
# 刷新环境变量
source ~/.bashrc
# 删除配置文件
rm -rf ~/.condarc ~/.conda ~/.continuum
# 删除残余文件
sudo rm /etc/apt/sources.list.d/anaconda.list
```
