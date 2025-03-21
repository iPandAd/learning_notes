# Git Configuration and Command

## 配置密钥对

```bash
ssh-keygen -t ed25519 -C "email@example.com"
cat ~/.ssh/id_ed25519.pub
```

将生成的公钥文件添加到 GitHub 个人账户下 SSH and GPG keys 即可

## 常用指令

```bash
# 克隆项目
git clone
# 拉取最新提交
git pull
```
