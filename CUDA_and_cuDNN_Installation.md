# CUDA and cuDNN Installation

CUDA 和 cuDNN 是开展深度学习相关项目的必备基础，本文主要记录了在 Windows、WSL 下的安装过程

## Windows

1. 在终端内输入 `nvidia-smi` 查看支持的最高 CUDA 版本
2. 在[CUDA Toolkit Archive](https://developer.nvidia.com/cuda-toolkit-archive)中选择对应版本的 CUDA。这里选择安装 CUDA 12.4
3. 安装 CUDA 时选择自定义安装，只勾选 CUDA 选项
4. 安装完毕后检查系统环境变量中是否有添加 CUDA 路径，在终端内输入 `nvcc -V` 查看 CUDA 版本
5. 若需要使用 TensorRT，则需要安装 cuDNN。这里选择安装 cuDNN 9.1.1 [cuDNN Downloads](https://developer.nvidia.com/cudnn-9-1-1-download-archive)。双击安装保持默认选项即可
6. 确认系统环境变量中 Path 变量是否有添加 cuDNN 路径。若无则手动添加 `C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4\bin`、`C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4\libnvvp`、`C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4\include`、`C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4\lib`
7. 进入 `C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4\extras\demo_suite` 分别将 `bandwidthTest` 和 `deviceQuery` 拖拽到终端并回车，显示 PASS 说明安装成功

安装完毕 CUDA 和 cuDNN 后，可以安装 GPU 版本的 PyTorch。安装与校验的指令如下：

```bash
# 安装指令
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu124

# 校验指令
python
import torch
torch.cuda.is_available()  # True
torch.cuda.get_device_name(0)  # 'NVIDIA GeForce RTX 2060'
torch.version.cuda  # '12.4'
torch.backends.cudnn.is_available()  # True
torch.backends.cudnn.version()  # '90100'
torch.__version__  # '2.6.0+cu124'
exit()
```

参考博客：

- [安装Cuda和cudnn，以及Pytorch的GPU版本](https://zhuanlan.zhihu.com/p/27577871722)
- [Nvdia CUDA 12+CuDNN 9 安装教程（上）](https://zhuanlan.zhihu.com/p/686877981)

## WSL

1. `wsl cat /proc/version` 查看内核版本，若低于 `5.10.43.3`，执行 `wsl --update`
2. 参考 [CUDA Toolkit 12.4 Downloads](https://developer.nvidia.com/cuda-12-4-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=WSL-Ubuntu&target_version=2.0&target_type=deb_local) 执行安装指令
3. 把 CUDA 加入环境变量并刷新
4. 安装 cuDNN 9.1.1 [cuDNN Downloads](https://developer.nvidia.com/cudnn-9-1-1-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=deb_local)

```bash
# 安装 CUDA Toolkit
wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pin
sudo mv cuda-wsl-ubuntu.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/12.4.0/local_installers/cuda-repo-wsl-ubuntu-12-4-local_12.4.0-1_amd64.deb
sudo dpkg -i cuda-repo-wsl-ubuntu-12-4-local_12.4.0-1_amd64.deb
sudo cp /var/cuda-repo-wsl-ubuntu-12-4-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cuda-toolkit-12-4

# CUDA 加入环境变量并刷新
vim ~/.bashrc
export CUDA_HOME="/usr/local/cuda-12.4"
export PATH="${CUDA_HOME}/bin:$PATH"
export LD_LIBRARY_PATH="${CUDA_HOME}/lib64:${LD_LIBRARY_PATH}"
export CPATH="${CUDA_HOME}/include:${PATH}"

source ~/.bashrc

# 检查是否成功安装
nvcc -V

# cuDNN 安装
wget https://developer.download.nvidia.com/compute/cudnn/9.1.1/local_installers/cudnn-local-repo-ubuntu2004-9.1.1_1.0-1_amd64.deb
sudo dpkg -i cudnn-local-repo-ubuntu2004-9.1.1_1.0-1_amd64.deb
sudo cp /var/cudnn-local-repo-ubuntu2004-9.1.1/cudnn-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cudnn-cuda-12

# 检查是否安装成功
whereis cudnn_version.h
cat /usr/include/cudnn_version.h | grep CUDNN_MAJOR -A 2
```

参考博客：

- [在 WSL 中启用 NVIDIA CUDA](https://learn.microsoft.com/zh-cn/windows/ai/directml/gpu-cuda-in-wsl)
- [Windows下安装WSL2并配置Cuda、Miniconda和 Torch](https://zhuanlan.zhihu.com/p/663817616)
