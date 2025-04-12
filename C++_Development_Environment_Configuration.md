# C++ Development Environment Configuration

## WSL

### 安装必要依赖

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install build-essential -y
sudo apt install gdb -y
sudo apt install git -y
sudo apt install cmake -y
sudo apt install clangd -y
sudo apt install clang-format -y
sudo apt install doxygen -y 
sudo apt install graphviz -y
sudo apt install valgrind -y
```

### 其他常用依赖

```bash
sudo apt install libeigen3-dev -y
sudo apt install protobuf-compiler -y
sudo apt install libprotobuf-dev -y
```

### clang-format 配置

在项目根目录的`.vscode/settings.json`下添加如下字段：

```json
{
    "editor.formatOnSave": true,
    "files.autoSave": "afterDelay",
    "[cpp]": {
        "editor.defaultFormatter": "xaver.clang-format"
    }
}
```

配置完成后按下`Ctrl + S`即可自动格式化
