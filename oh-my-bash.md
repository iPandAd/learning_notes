# 一键换源

```bash
wget http://fishros.com/install -O fishros && . fishros
```

## 安装 oh-my-bash

```bash
bash -c "$(wget https://raw.githubusercontent.com/ohmybash/oh-my-bash/master/tools/install.sh -O -)"
```

## 安装 zoxide

```bash
curl -sS https://raw.githubusercontent.com/ajeetdsouza/zoxide/main/install.sh | bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(zoxide init bash)"' >> ~/.bashrc
```

## 安装 fzf

```bash
sudo apt install fzf
echo 'source /usr/share/doc/fzf/examples/key-bindings.bash' >> ~/.bashrc
echo 'source /usr/share/doc/fzf/examples/completion.bash' >> ~/.bashrc
```

## 安装 lsd

```bash
# 下载 lsd release（选择对应版本）
wget https://github.com/lsd-rs/lsd/releases/download/v1.1.2/lsd-v1.1.2-x86_64-unknown-linux-gnu.tar.gz
tar xzf lsd-*.tar.gz
sudo mv lsd-*/lsd /usr/local/bin/

# 在 ~/.bashrc 中设置别名
echo 'alias ls="lsd"' >> ~/.bashrc
echo 'alias ll="lsd -l"' >> ~/.bashrc
echo 'alias la="lsd -a"' >> ~/.bashrc
```

## 安装 bat

```bash
sudo apt install bat
# 注意：Ubuntu 中可执行文件名为 batcat，可设置别名
echo 'alias cat="batcat --paging=never"' >> ~/.bashrc
```

## 安装 ble.sh

```bash
git clone --recursive --depth 1 https://github.com/akinomyoga/ble.sh.git
make -C ble.sh install PREFIX=~/.local
echo 'source ~/.local/share/blesh/ble.sh' >> ~/.bashrc
```

需要安装字体

```bash
mkdir -p ~/.local/share/fonts
cd ~/.local/share/fonts
wget https://github.com/ryanoasis/nerd-fonts/releases/download/v3.2.1/JetBrainsMono.zip
unzip jetbrainsmono.zip -d JetBrainsMono
rm jetbrainsmono.zip

fc-cache -fv
```

## 安装 miniforge

```bash
wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh
bash Miniforge3-Linux-x86_64.sh
```
