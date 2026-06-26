# Hugmunn

> Where thought meets memory in the age of AI.

渡鸦 **Huginn** 和 **Muninn** 每天破晓时分飞往人间，并在黄昏时飞回，落在 Odin 的肩膀上，低语它们所见闻的一切。

---

## Huginn

> 寓意为「思想」或「理性」。

此部分预留用于记录未来的构想、深度思考、设计规划以及尚未归类归档的随笔与灵感。

- [huginn/i.md](huginn/i.md) —— **思想火花**：关于认知、理性与荒诞的短思。

---

## Muninn

> 寓意为「记忆」或「心智」。

本部分是核心的个人数字知识库，系统整理了我们在环境与工具配置、语言语法辨析、提示词工程等维度的日常积累与实践沉淀。

### 🛠️ 环境与工具配置

- [muninn/anthropic/ds-cc.md](muninn/anthropic/ds-cc.md) —— **DeepSeek 接入 Claude Code 指南**：如何在 Claude Code 终端助手下配置并使用 DeepSeek 语言模型。
- [muninn/anthropic/qwen-cc.md](muninn/anthropic/qwen-cc.md) —— **Qwen 接入 Claude Code 指南**：如何在 Claude Code 下配置使用阿里云百炼 Qwen 模型。
- [muninn/anthropic/co-author.md](muninn/anthropic/co-author.md) —— **Git 联合署名配置**：如何在 Claude Code 设置中禁用自动追加 AI 联合署名。
- [muninn/git-force-with-lease.md](muninn/git-force-with-lease.md) —— **Git force-with-lease 详解**：深入浅出讲解 `--force-with-lease` 的工作原理、与 `--force` 的区别以及为什么它是更安全的强推方式。
- [muninn/gitconfig.md](muninn/gitconfig.md) —— **Git 别名配置**：常用的 Git 快捷命令别名设置，包括状态查看、安全的强制推送、美观的提交树日志等。
- [muninn/antigravity-guide.md](muninn/antigravity-guide.md) —— **Google Antigravity 参考手册**：汇总了 Antigravity CLI (agy)、2.0 桌面端、IDE 插件以及 Python SDK 的核心使用与配置指南。
- [muninn/gfm_tutorial.md](muninn/gfm_tutorial.md) —— **GitHub Flavored Markdown 简明教程**：GFM 语法基础与进阶功能指南（包括任务列表、Alerts、公式块、Emoji 和脚注等特性）。
- [muninn/d2cli/d2cli.md](muninn/d2cli/d2cli.md) —— **D2 CLI 绘图引擎指南**：D2 图表语言的安装、运行、布局引擎（ELK / Dagre）配置以及常见命令行参数表。
- [muninn/rsync.md](muninn/rsync.md) —— **rsync 同步工具指南**：核心参数释义、路径斜杠区别、常见备份用例以及与 `cp` / `scp` 的差异对比。
- [muninn/open-port-on-ubuntu.md](muninn/open-port-on-ubuntu.md) —— **Ubuntu UFW 端口配置指南**：如何检查 UFW 状态、安全放行 SSH（22）、HTTP（80）、HTTPS（443）等端口。
- [muninn/ssh-demote-development.md](muninn/ssh-demote-development.md) —— **Ubuntu 24.04 远程开发指南**：远程开发模式的利弊分析、共享内存段清理、实时线程优先级配置以及 Tmux 避坑指南。
- [muninn/liteparse.md](muninn/liteparse.md) —— **LiteParse 工具说明**：基于 Rust 的 PDF 解析器工具安装与使用说明。
- [muninn/markedit.md](muninn/markedit.md) —— **MarkEdit 快捷配置**：Markdown 编辑器快捷别名的 shell 配置。
- [muninn/font.md](muninn/font.md) —— **字体配置**：FantasqueSansM Nerd Font 的安装指南。
- [muninn/zshrc.md](muninn/zshrc.md) —— **个人配置文件别名**：包括 zshrc 常用别名、本机 / 公网网络查询命令以及希腊字母快速打印别名。
- [muninn/alacritty/alacritty.md](muninn/alacritty/alacritty.md) —— **Alacritty 分屏与窗口管理**：如何配合 Tmux 使用 Alacritty 实现终端分屏 and 窗口管理。
- [muninn/ghostty/ghostty.md](muninn/ghostty/ghostty.md) —— **Ghostty 终端安装说明**：现代化 terminal 仿真器 Ghostty 的基本安装指南。
- [muninn/tmux/README.md](muninn/tmux/README.md) —— **Tmux 终极配置与灾备指南**：如何恢复 Tmux 会话环境（tmux-resurrect）及加载新路径配置文件。
- [muninn/zellij/zellij.md](muninn/zellij/zellij.md) —— **Zellij 终端多路复用器指南**：现代化 Rust 终端工作空间安装、核心杀手锏（提示状态栏、Wasm 插件、布局系统）以及与 Alacritty / Ghostty + Helix 组合使用说明。
- [muninn/cosmographia.md](muninn/cosmographia.md) —— **Cosmographia 4.2 说明**：关于 3D 太阳系与天体物理交互模拟器的说明。

### 📝 英语语法与词汇辨析

- [muninn/changes-to-or-for.md](muninn/changes-to-or-for.md) —— **Changes to vs. Changes for**：介词 to（指向修改对象）与 for（指向修改目的）的用法区别与逻辑解析。
- [muninn/check-review-inspect-proofread.md](muninn/check-review-inspect-proofread.md) —— **Check / Review / Inspect / Proofread 辨析**：这四个在代码评审和文本校对中常用「检查 / 审查」类动词的精细区别与记忆口诀。
- [muninn/us-vs-uk-date-format.md](muninn/us-vs-uk-date-format.md) —— **美式与英式日期表达差异**：月-日-年 (US) 与 日-月-年 (UK) 排列差异对照、口语与书写规则以及防歧义的最佳实践。
- [muninn/words/Tuesday.md](muninn/words/Tuesday.md) —— **Tuesday 词源深度解析**：以独手北欧战神提尔（Týr）为线索，深度剖析 Tuesday 的原始画面、核心意象与打工人战神精神。
- [muninn/words/Thursday.md](muninn/words/Thursday.md) —— **Thursday 词源深度解析**：以手握妙尔尼尔（Mjölnir）神锤的雷神托尔（Thor）为线索，深度解构 Thursday 的原始画面、核心意象与破局之日意志。
- [muninn/words/Saturday.md](muninn/words/Saturday.md) —— **Saturday 词源深度解析**：以手握收割镰刀的罗马农神萨图尔努斯（Saturnus）为线索，深度探寻 Saturday 的原始画面、核心意象与时间循环律动。
- [muninn/words/etymology.md](muninn/words/etymology.md) —— **Etymology 词源深度解析**：以希腊语本源（etymon）为线索，深度剖析 etymology 的原始画面、核心意象以及作为穿透性认知工具的作用。

### 🤖 提示词与 AI 角色

- [muninn/cool-teacher.md](muninn/cool-teacher.md) —— **Cool Teacher 角色卡**：费曼物理教学风格的 AI 导师提示词，擅长用最简单通俗的语言解剖复杂概念。
