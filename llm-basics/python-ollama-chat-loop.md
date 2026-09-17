# 20260915
## Python 调用 Ollama：从单轮问答到连续对话

### 目标

把最初只能问一句的脚本，升级成可以连续聊天、记住上下文、清空历史的命令行工具。

### 最终代码

```python
import ollama

messages = []
print("输入 exit 退出，输入 clear 清空对话历史。")

while True:
    user_input = input("你：")

    if user_input.lower() == "exit":
        break

    if user_input.lower() == "clear":
        messages.clear()
        print("对话历史已清空。")
        continue

    messages.append({"role": "user", "content": user_input})

    response = ollama.chat(
        model="qwen2.5:1.5b",
        messages=messages
    )

    reply = response["message"]["content"]
    print("模型:", reply)

    messages.append({"role": "assistant", "content": reply})
```