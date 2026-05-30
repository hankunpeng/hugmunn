# 联合署名

禁止 Claude Code 在自动生成 Git 提交（Commit）或拉取请求（PR）时，在说明末尾追加 AI 的联合署名（Co-authored-by）信息。

[Claude Code 的官方技术文档的配置项说明页面](https://code.claude.com/docs/en/settings) 中标注 **includeCoAuthoredBy** 字段的状态为弃用（**Deprecated**: Use `attribution` instead.），因此把

```
  "includeCoAuthoredBy": false,
```
修改为
```
  "attribution": {
    "coAuthoredBy": false
  },
```

