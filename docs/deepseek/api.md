# DeepSeek Api
DeepSeek APi的官方文档 [官方文档链接](https://api-docs.deepseek.com/zh-cn/guides/reasoning_model)

## 使用python来调用deepseek
### 安装ollama
```
pip install ollama
```

### 流式调用
```python
import ollama
from ollama import Client
client=Client(host='10.111.32.151:11434')
stream =client.chat(model='deepseek-r1:32b',stream=True,messages=[
    {
        'role':'user',
        'content':'你是谁?'
    }
])

for chunk in stream:
  print(chunk['message']['content'], end='', flush=True)
```

### 非流式调用
```python
import ollama
from ollama import Client
client=Client(host='10.111.32.151:11434')
response =client.chat(model='deepseek-r1:32b',messages=[
    {
        'role':'user',
        'content':'你是谁?'
    }
])
print(response['message']['content'])
print(response.message.content)
```