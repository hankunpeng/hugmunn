# LiteParse


## 从零安装

```
curl https://sh.rustup.rs -sSf | sh

cargo install liteparse
……
Finished `release` profile [optimized] target(s) in 1m 51s
Installing /Users/alex/.cargo/bin/lit
Installed package `liteparse v2.1.1` (executable `lit`)
```

`liteparse` 已成功安装，其在终端中的可执行文件命令为 **`lit`**。


## 查看帮助

在终端中运行以下命令以确认环境正常，并查看完整的命令行参数：

```
lit --help
OSS document parsing tool (supports PDF, DOCX, XLSX, images, and more)

Usage: lit <COMMAND>

Commands:
  parse        Parse a document file (PDF, DOCX, XLSX, PPTX, images, etc.)
  screenshot   Generate screenshots of document pages (PDF, DOCX, XLSX, images, etc.)
  batch-parse  Parse multiple documents in batch mode
  help         Print this message or the help of the given subcommand(s)

Options:
  -h, --help     Print help
  -V, --version  Print version
```


## 常见操作

* **将 PDF 解析为结构化 Markdown**
```
lit parse input.pdf -o output.md
```

* **包含边界框（Bounding Boxes）的空间文本解析**
```
lit parse input.pdf --bbox
```

* **将 PDF 页面渲染为高质量图片（用于多模态 Agent 工作流）**
```
lit screenshot input.pdf --output-dir ./output_images
```


## 注意事项

如果系统提示 `command not found: lit`，请确保当前终端已执行过 `source "$HOME/.cargo/env"`，或者直接关闭并重新打开一个新的终端窗口。