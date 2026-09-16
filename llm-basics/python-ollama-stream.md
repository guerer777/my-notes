# Python 调用 Ollama：流式输出

日期：2026-09-16  
项目：ollama-python  
文件：chat_stream.py

## 目标

让模型回答像打字一样逐字显示，而不是等整段生成完再一次性打印。这样等待感更低，也是聊天机器人的标准做法。

## 代码

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

    print("模型：", end="", flush=True)

    stream = ollama.chat(
        model="qwen2.5:1.5b",
        messages=messages,
        stream=True
    )

    reply = ""
    for chunk in stream:
        piece = chunk["message"]["content"]
        print(piece, end="", flush=True)
        reply += piece

    print()

    messages.append({"role": "assistant", "content": reply})
```