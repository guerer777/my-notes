# 20260911
## 一、Git 配置与操作

### 1. 配置身份（只需一次）
```bash
git config --global user.name "英文名"
git config --global user.email "QQ邮箱"
```
查看配置：
```bash
git config --global --list
```

### 2. 初始化仓库
```bash
git init
```
在当前目录创建 `.git` 文件夹，开始版本管理。

### 3. 创建 `.gitignore`
文件内容：
```
venv/
__pycache__/
*.pyc
.env
```
告诉 Git 忽略虚拟环境、缓存等不需要提交的文件。

### 4. 第一次提交
```bash
git add .
git commit -m "第一个 Ollama Python 脚本"
```
解释：
- `git add .` 把所有改动加入暂存区。
- `git commit` 生成一次提交记录。

### 5. 查看状态和历史
```bash
git status        # 查看当前状态
git log           # 查看提交历史
```

### 6. 关联远程仓库
```bash
# Gitee
git remote add origin https://gitee.com/用户名/ollama-python.git

# GitHub
git remote add github https://github.com/用户名/ollama-python.git
```
查看远程：
```bash
git remote -v
```

### 7. 设置主分支并推送
```bash
git branch -M main
git push -u origin main      # 推送到 Gitee
git push -u github main      # 推送到 GitHub
```
解释：
- `git branch -M main` 把当前分支重命名为 `main`。
- `-u` 记住远程分支，以后直接 `git push` 即可。

### 8. 以后每次修改
```bash
git add .
git commit -m "说明这次改了什么"
git push origin main
git push github main
```

---

## 二、遇到的问题与解决

### 1. PowerShell 禁止运行脚本
错误：
```
无法加载文件 ... Activate.ps1，因为在此系统上禁止运行脚本。
```
解决：
```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
```

### 2. Pylance 报“无法解析导入 ollama”
原因：VS Code 没选对 Python 解释器。
解决：
- `Ctrl + Shift + P` → `Python: Select Interpreter` → 选择 `venv` 中的 `python.exe`。

### 3. GitHub SSL 证书错误
错误：
```
unable to access ... SSL certificate ... unable to get local issuer certificate
```
解决：
```bash
git config --global http.sslBackend schannel
```
然后重新推送。

### 4. GitHub Token 被覆盖
重新生成 Personal Access Token，勾选 `repo` 权限，复制后立即使用。

---

## 三、远程仓库地址

- Gitee：`https://gitee.com/用户名/ollama-python.git`
- GitHub：`https://github.com/用户名/ollama-python.git`

本地项目目录：`D:\Projects\ollama-python`

---

## 四、以后的工作流

1. 打开项目：VS Code 打开 `D:\Projects\ollama-python`
2. 激活虚拟环境：`venv\Scripts\activate`
3. 写代码、运行测试
4. 提交并推送：
   ```bash
   git add .
   git commit -m "说明"
   git push origin main
   git push github main
   ```

---
