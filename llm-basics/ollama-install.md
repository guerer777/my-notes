# 20260910
## 一、系统重装与恢复（20260910）

1. **重装前备份**
   - 项目代码（Vue + SpringBoot）
   - MySQL 数据库 SQL
   - VMware 虚拟机文件夹
   - IDE 配置（VS Code、IDEA、Navicat）
   - 环境版本说明

2. **重装 Windows 11**
   - 用微软官方媒体创建工具制作 U 盘启动盘
   - 全盘删除分区，全新安装 Windows 11 家庭中文版
   - 联网自动激活
   - 安装华硕官方驱动、MyASUS，设备管理器无黄色感叹号

3. **分盘与用户目录**
   - C 盘 200GB，D 盘约 265GB
   - 新建英文账户，避免中文路径问题
   - 把桌面、下载、文档等用户文件夹移到 D 盘
   - 关闭 OneDrive，避免干扰

---

## 二、开发环境恢复

- JDK、Node.js、MySQL、IDEA、VS Code、Navicat、VMware 等，等确定要用时再装，全部装到 D 盘。
- 项目、数据库、虚拟机、大模型文件都放 D 盘，C 盘保持干净。

---

## 三、本地大模型部署

### 1. Ollama
- 安装 Ollama，设置 `OLLAMA_MODELS=D:\Ollama\Models`
- 跑通 `qwen2.5:1.5b`、`llama3.2:3b`
- GPU 加速正常，`nvidia-smi` 能看到 `llama-server.exe`
- 体验：1.5B 快但浅，3B 平衡

### 2. LM Studio
- 安装 LM Studio，模型目录改到 `D:\LMStudio\Models`
- 下载 `DeepSeek-Coder-7B-Instruct-v1.5-GGUF` 的 Q4_K_M
- GPU Offload 拉满，Context Length 4096
- 显存占用约 5.8GB，速度较慢，但代码质量明显更高

### 3. 核心权衡
- 参数量越大 → 显存占用越高 → 质量越好，速度越慢
- RTX 4060 8GB，7B Q4 合适，再大就吃力
- 日常聊天用 3B，写代码用 7B，快速草稿用 1.5B

---

## 四、关键经验

- 所有大文件、模型、项目、虚拟机都放 D 盘
- 用户目录用英文，避免开发工具报错
- 跑模型时不要同时开两个，会抢显存
- `nvidia-smi` 是确认 GPU 加速的好工具
- 模型下载慢时，可用 hf-mirror.com 或迅雷/IDM 手动下载

---