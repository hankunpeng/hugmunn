# DeepSeek 接入 Claude Code



## Claude Code

### 1. 安装

```bash
curl -fsSL https://claude.ai/install.sh | bash
# 安装结束后，执行以下命令，若显示版本号则安装成功。
claude --version
```

### 2. 配置

先在 [DeepSeek Platform](https://platform.deepseek.com/api_keys) 获取你的 API Key，然后在 Claude Code 的 settings.json 里添加以下内容：

```json
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.deepseek.com/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "<你的 DeepSeek API Key>",
    "ANTHROPIC_MODEL": "deepseek-v4-pro[1m]",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "deepseek-v4-flash",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "deepseek-v4-pro[1m]",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "deepseek-v4-pro[1m]",
    "CLAUDE_CODE_SUBAGENT_MODEL": "deepseek-v4-flash",
    "CLAUDE_CODE_EFFORT_LEVEL": "max"
  },
```

### 3. 使用

```bash
# cd /your/project/path 进入你的项目文件夹
claude
```



## Claude Desktop APP

在使用 Claude Desktop APP 的 developer 模式时，DeepSeek 会对传入的 Claude  模型名进行映射：

- claude-opus 开头的模型，会映射到 deepseek-v4-pro
- claude-haiku、claude-sonnet 开头的模型，会映射到 deepseek-v4-flash

这样可以绕过 Claude Desktop APP 对模型名的限制，只需改动 base_url 和 api_key，即可在其中接入 DeepSeek 模型。