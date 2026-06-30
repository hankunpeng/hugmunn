# Understanding `git clone --recurse-submodules`

The `git clone --recurse-submodules` command lets you clone a Git repository and automatically initialize and clone all its associated submodules. This guide explains how the `--recurse-submodules` option works, why you need it, and how it simplifies working with multi-repository projects.

---

## English explanation

The `--recurse-submodules` option is a flag used during cloning to retrieve nested repositories. Without this flag, a standard clone operation only downloads the main repository and leaves any submodule directories empty.

### How it works

When you clone a repository that contains submodules, Git requires specific instructions to handle those nested repositories.

1. Git clones the main repository to your local system first.
2. Git reads the `.gitmodules` file in the root of the main repository to find the paths and URLs of all registered submodules.
3. Git automatically initializes and clones each submodule repository into its designated directory.
4. Git checks out the specific commit of each submodule that is recorded in the main repository's history.

This single command combines `git clone`, `git submodule init`, and `git submodule update --recursive` into one step.

### Why you use it

If a project relies on external libraries or shared code hosted in separate repositories, those dependencies are often configured as submodules. Using this option ensures that your local workspace is complete and ready to build or run immediately after the clone completes. If you clone without this option, you must run additional commands to populate the empty submodule folders.

---

# 理解 `git clone --recurse-submodules`

`git clone --recurse-submodules` 命令让你在克隆一个 Git 仓库时，自动初始化并克隆其关联的所有子模块。本指南解释了 `--recurse-submodules` 选项的工作原理、使用它的原因以及它如何简化多仓库项目的协作。

---

## 中文说明

`--recurse-submodules` 选项是克隆时用于获取嵌套仓库的标记。如果没有这个标记，标准的克隆操作只会下载主仓库，而子模块对应的目录会保持为空。

### 工作原理

当你克隆一个包含子模块的仓库时，Git 需要获取明确的指示以处理这些嵌套的仓库。

1. Git 首先将主仓库克隆到你的本地系统。
2. Git 读取主仓库根目录下的 `.gitmodules` 文件，以获取所有已注册子模块的路径和 URL。
3. Git 自动将每个子模块仓库初始化并克隆到指定的目录中。
4. Git 签出主仓库历史记录中所记录的每个子模块的具体提交（commit）。

这行命令将 `git clone`、`git submodule init` 和 `git submodule update --recursive` 合并为一个步骤。

### 为什么使用它

如果一个项目依赖于托管在其他仓库的外部库或共享代码，这些依赖通常会被配置为子模块。使用此选项可以确保在克隆完成后，你的本地工作区是完整且可以直接构建或运行的。如果你在克隆时没有使用这个选项，你必须运行额外的命令来填充那些空的子模块文件夹。
