# how-to-push
# Git 本地到 GitHub 最简流程

## 1. 初始化仓库（只需要做一次）

```bash
cd D:\stm32_dev_env      # 进入你的项目目录
git init                 # 初始化 Git 仓库
git branch -M main       # 把默认分支改名为 main
2. 绑定远程仓库
如果是第一次绑定：

bash
编辑
git remote add origin https://github.com/你的用户名/仓库名.git
如果之前绑定过，需要改地址：

bash
编辑
git remote set-url origin https://github.com/你的用户名/仓库名.git
3. 添加并提交代码
bash
编辑
git add .                        # 添加所有文件
git commit -m "first commit"     # 提交
4. 推送到 GitHub（第一次会弹出浏览器登录，之后会自动保存）
bash
编辑
git push -u origin main
后续更新代码只要三步
bash
编辑
git add .
git commit -m "update: 修改说明"
git push
