# Conventional Commits 规范指南

**Conventional Commits（约定式提交）** 是一种基于提交消息的轻量级约定。它提供了一套简单的规则来创建清晰的提交历史，这使得编写基于提交的自动化工具（如自动生成 Changelog、自动语义化版本升级等）变得更加容易。

---

## 1. 提交消息的基本结构

约定式提交的格式非常结构化，主要由以下三部分组成（其中 **Header** 是必需的，**Body** 和 **Footer** 是可选的）：

```text
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### 译读各个组成部分：

* **Header (标题行)**:
  * **`type` (类型)**: 必须，用于说明本次提交的意图或性质（详见下文常用类型）。
  * **`scope` (作用域)**: 可选，用括号包裹，指明本次修改影响的范围（如 `auth`, `parser`, `api` 等）。
  * **`description` (描述)**: 必须，简短概括本次修改内容。建议使用祈使句（如用 `add` 而非 `added`）。
* **Body (正文)**:
  * 可选。如果描述较为复杂，可以在正文里写明详细动机、对比方案以及设计决策等。与标题行之间需要空一行。
* **Footer (脚注)**:
  * 可选。主要用于关联 Issue 追踪系统（如 `Fixes #123`），或声明重大变更（`BREAKING CHANGE`）。与正文或标题行之间需要空一行。

---

## 2. 核心与常用类型 (Type)

约定式提交将修改划分为了不同的类型，以便于快速筛选历史以及自动化分析：

| 类型 | 说明 | 示例 | 对应的语义化版本变化 |
| :--- | :--- | :--- | :--- |
| **`feat`** | 引入全新的功能 | `feat(auth): add google login` | **Minor (次版本)** |
| **`fix`** | 修复已有的 Bug | `fix(api): resolve timeout issue` | **Patch (修订号)** |
| **`docs`** | 仅修改文档、说明文件等 | `docs: update conventional commits guide` | 无（通常不升级版本） |
| **`style`** | 不改变代码逻辑的格式调整（空白、格式化、分号缺失等） | `style: run prettier formatter` | 无 |
| **`refactor`**| 既不增加新功能也不修复 Bug 的代码重构 | `refactor: optimize database query` | 无 |
| **`perf`** | 提升系统性能、运行速度或资源利用率的修改 | `perf: lazy load image components` | 无（或 Patch） |
| **`test`** | 增加缺失的测试或修正现有的测试 | `test: add unit tests for user service` | 无 |
| **`build`** | 修改构建系统、打包配置或外部依赖（如 Webpack, Maven, npm 等） | `build(deps): bump lodash from 4.0.0 to 4.17.21`| 无 |
| **`ci`** | 修改持续集成/部署的脚本和配置文件（如 GitHub Actions, Travis 等） | `ci: add lint check before push` | 无 |
| **`chore`** | 其他不修改源代码和测试文件的日常琐事（如辅助工具配置等） | `chore: update gitignore` | 无 |
| **`revert`**| 撤销之前的某个 Commit | `revert: feat(auth): add google login` | 无 |

---

## 3. 重大变更 (Breaking Changes)

如果你的修改会导致向后不兼容（例如删除了已有的 API 或改变了核心逻辑），必须将其标记为 **BREAKING CHANGE**。

在约定式提交中，有两种方式来声明重大变更：

### 方式 A：在 Header 的类型或作用域后加感叹号 `!`
这是最直观的方式，适合简短的破坏性修改：
```text
feat(api)!: remove support for older version v1
```

### 方式 B：在 Footer 声明 `BREAKING CHANGE:` 开头的段落
这是最完整的方式，可用于正规详细阐述破坏性变更的内容和迁移指南：
```text
refactor(auth): simplify session token generation

This changes the structure of encryption keys used for sessions.

BREAKING CHANGE: The older session tokens are no longer valid. Users must re-login.
```

> [!NOTE]
> 无论是感叹号 `!` 还是 Footer 里的声明，它们都会强制触发语义化版本中的 **Major (主版本号/大版本)** 升级。

---

## 4. 提交消息示例

### 示例 1：包含 Scope 和感叹号重大变更的提交
```text
feat(api)!: send an email to the customer when a product is shipped
```

### 示例 2：标准 Feat 提交（带 Body 和 Footer）
```text
feat(parser): add support for JSON Lines format

The parser can now parse multi-line JSON structures separated by newlines.
This optimizes parsing speeds for large analytical logs.

Closes #842, #845
```

### 示例 3：纯 Bug 修复提交
```text
fix: resolve database connection leakage on server restart
```

---

## 5. 约定式提交的优势

1. **自动生成 CHANGELOG**：工具（例如 `standard-version`）可以自动解析 commits 记录，一键提取所有 `feat` 和 `fix` 类型的提交，分类并自动生成结构优美的更新日志。
2. **自动判断版本号**：基于语义化版本 (SemVer)，系统在部署时可以根据提交内容自动升版：
   * 包含 `BREAKING CHANGE` / `!` 👉 **Major 升级**（如 `1.2.3` ➡️ `2.0.0`）
   * 包含 `feat` 👉 **Minor 升级**（如 `1.2.3` ➡️ `1.3.0`）
   * 仅包含 `fix` 👉 **Patch 升级**（如 `1.2.3` ➡️ `1.2.4`）
3. **更具可读性的提交历史**：让团队成员、开源贡献者一眼就能看出项目历史的脉络，方便进行 Code Review 和回滚追踪。
