# 20260911
## 一、总览

1. 安装 Python、VS Code、Git
2. 创建项目文件夹和虚拟环境
3. 安装依赖（requests、ollama）
4. 写 Python 脚本调用本地 Ollama 模型
5. 配置 Git 身份
6. 初始化本地仓库，提交代码
7. 在 Gitee 创建远程仓库并推送
8. 在 GitHub 创建远程仓库并推送
9. 解决了 PowerShell 策略、SSL 证书、Pylance 导入警告等问题

---

## 二、环境搭建命令

### 1. 验证安装
```bash
python --version          # 查看 Python 版本
pip --version             # 查看 pip 版本
git --version             # 查看 Git 版本
```

### 2. 创建项目文件夹
```bash
D:\Projects\ollama-python
```

### 3. 创建虚拟环境
```bash
python -m venv venv
```
解释：在项目目录下创建名为 `venv` 的虚拟环境，隔离项目依赖。

### 4. 激活虚拟环境
- **PowerShell**（如果执行策略受限，先运行下面命令）：
```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
```
然后：
```powershell
.\venv\Scripts\Activate.ps1
```
- **cmd**：
```cmd
venv\Scripts\activate
```
激活后终端前面会出现 `(venv)`。

### 5. 安装依赖
```bash
pip install requests ollama -i https://pypi.tuna.tsinghua.edu.cn/simple
```
安装 `requests`（发送 HTTP 请求）和 `ollama`（官方 Python 库），使用清华源加速下载。

---

## 三、Python 代码

### 1. `hello.py`
```python
print("Hello, Python!")
```
运行：
```bash
python hello.py
```

### 2. `chat_ollama.py`
```python
import ollama

response = ollama.chat(
    model="qwen2.5:1.5b",
    messages=[
        {"role": "user", "content": "你好，请用一句话介绍你自己。"}
    ]
)
print(response["message"]["content"])
```
运行：
```bash
python chat_ollama.py
```
解释：
- `ollama.chat()` 调用本地 Ollama 的聊天接口。
- `model` 指定模型名称。
- `messages` 是对话列表，`role` 可以是 `user` 或 `assistant`。
- `response["message"]["content"]` 取出模型回答。

---
