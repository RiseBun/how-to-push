# how-to-push
# Git 本地到 GitHub 最简流程

# 从 0 开始配置 Git，并用 **HTTPS** 方式推送代码（GitHub）

> 适用平台：Windows / macOS / Linux  
> 目标：完成 Git 安装 → 配置用户名邮箱 → 生成并使用 **PAT**（Personal Access Token）→ 通过 **HTTPS** 推送代码到 GitHub


## 1.安装 Git

- **Windows**：到 <https://git-scm.com/download/win> 下载并安装（一路下一步即可）。
- **macOS**：安装 Xcode Command Line Tools 或 `brew install git`。
- **Linux (Debian/Ubuntu)**：
  ```bash
  sudo apt update && sudo apt install -y git
  ```
检查是否安装成功
 ```bash
  git --version
 ```
## 2.初始化配置（用户名与邮箱）

这两项会写入每次提交的作者信息，邮箱建议与 GitHub 绑定邮箱一致。
 ```bash
git config --global user.name  "你的名字"
git config --global user.email "你的邮箱@example.com"
 ```
# 可选：更友好的默认分支名
 ```bash
git config --global init.defaultBranch main
 ```
# 查看全局配置
 ```bash
git config --global --list
 ```
 
## 3.创建 GitHub 个人访问令牌（PAT）

 HTTPS 推送必须使用 Token，而不是 GitHub 密码。
位置：GitHub -> Settings -> Developer settings -> Personal access tokens（建议 Fine-grained token）
权限建议：至少勾选 repo（读写代码）。保存后会得到一串 Token（只显示一次，务必复制好）。

# 首次推送或拉取时，当命令行提示输入：
 ```bash
Username：你的 GitHub 用户名（不是邮箱）

Password：粘贴刚生成的 Token
 ```

设置凭据保存（避免每次输入）
Windows（Git Credential Manager 默认已启用）
 ```bash
git config --global credential.helper manager
 ```
macOS（使用系统钥匙串）
 ```bash
git config --global credential.helper osxkeychain
 ```
Linux（用内置libsecret）

使用 libsecret（不同发行版略有差异）：
 ```bash
git config --global credential.helper store   # 明文存磁盘，不推荐在共享机器
 ```

说明：设置好后，第一次输入用户名+Token 后会保存，下一次无需再输。

## 1. 初始化仓库（只需要做一次）

```bash
cd "项目路径"      # 进入你的项目目录
git init                 # 初始化 Git 仓库
git branch -M main       # 把默认分支改名为 main
```
2. 绑定远程仓库
如果是第一次绑定：

```bash
编辑
git remote add origin https://github.com/你的用户名/仓库名.git
```
如果之前绑定过，需要改地址：

```bash
编辑
git remote set-url origin https://github.com/你的用户名/仓库名.git
```
3. 添加并提交代码
```bash
编辑
git add .                        # 添加所有文件
git commit -m "first commit"     # 提交
```
4. 推送到 GitHub（第一次会弹出浏览器登录，之后会自动保存）
```bash
编辑
git push -u origin main
```
后续更新代码只要三步
```bash
编辑
git add .
git commit -m "update: 修改说明"
git push
```
