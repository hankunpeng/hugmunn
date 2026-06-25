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
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "deepseek-v4-flash[1m]",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "deepseek-v4-flash[1m]",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "deepseek-v4-pro[1m]",
    "CLAUDE_CODE_SUBAGENT_MODEL": "deepseek-v4-flash[1m]",
    "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1",
    "CLAUDE_CODE_EFFORT_LEVEL": "max"
  },
```

配置中的这一行 `"CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": “1”,` 是一键隐私/静默开关，它的核心作用是禁用所有非必要的外部网络请求和后台服务，具体会产生以下几个核心影响：

1. 拦截所有遥测与日志上报（Telemetry & Logs）
2. 关闭反馈与质量调研
3. 关闭后台自动更新
4. 可能影响实验室/新功能： 由于它切断了与功能开关（Feature Flags）服务器的连接，部分依赖云端下发或处于灰度测试的特性（例如一些特定的高级模型调用权限或插件频道功能）可能会由于无法获取状态而默认关闭。

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