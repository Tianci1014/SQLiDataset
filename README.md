# SQL注入检测数据集

这个仓库包含用于训练大型语言模型(LLM)识别和理解SQL注入攻击的数据集。该数据集旨在提高模型在网络安全领域的能力，特别是在SQL注入漏洞检测方面的表现。

## 数据集说明

数据集包含以下文件：
- `sqli1.jsonl`: SQL注入训练数据集文件 (15MB)
- `sqli2.jsonl`: SQL注入训练数据集文件 (22MB)
- `sqli3.jsonl`: SQL注入训练数据集文件 (8.2MB)
- `sqli4.jsonl`: SQL注入训练数据集文件 (14MB)
- `sqli1.json`: SQL注入原始数据文件 (36MB)
- `test.py`: 测试脚本
- `jsl2js.py`: 数据处理脚本

总计包含超过95MB的SQL注入相关训练数据。数据集采用JSONL格式，每行包含一个独立的JSON对象，适合用于大规模机器学习模型的训练。

## 数据格式

每个训练样本以JSONL格式存储，采用对话形式组织数据。每条记录包含一个完整的SQL注入相关对话，包括：
- 漏洞发现过程
- 注入技术讨论
- 漏洞验证步骤
- 数据提取方法
- 安全建议

示例格式：
```json
{
    "conversations": [
        {
            "from": "human",
            "value": "我在测试一个登录页面，输入用户名和密码后，页面返回了一个数据库错误信息。这可能是SQL注入点吗？"
        },
        {
            "from": "gpt",
            "value": "是的，返回数据库错误信息通常表明存在SQL注入漏洞。你可以尝试在用户名字段中输入一个单引号（'），看看是否会导致类似的错误。这可以帮助确认是否存在注入点。"
        },
        {
            "from": "human",
            "value": "我输入了单引号，页面确实返回了SQL语法错误。接下来我该怎么做？"
        },
        {
            "from": "gpt",
            "value": "既然确认了注入点，你可以尝试使用联合查询注入来提取数据。首先，你需要确定查询中的列数。可以尝试输入 `' UNION SELECT NULL, NULL, NULL --`，并逐步增加NULL的数量，直到页面不再报错。"
        }
        // ... 更多对话内容 ...
    ]
}
```

## 使用目的

1. 训练模型识别SQL注入攻击模式
2. 提高模型对SQL注入漏洞的理解
3. 增强模型在网络安全领域的应用能力

## 注意事项

⚠️ 本数据集仅用于教育和研究目的。请勿将其用于任何非法或恶意的活动。

## 使用方法

1. 克隆本仓库
2. 使用支持JSONL格式的数据加载器加载数据
3. 将数据集整合到您的模型训练流程中

## 许可说明

本数据集仅供学术研究使用。在使用本数据集时，请遵守相关法律法规和道德准则。

## 贡献

欢迎通过Issue或Pull Request提供建议和改进。
