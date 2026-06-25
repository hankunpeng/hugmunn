# Ubuntu 端口开放与 UFW 防火墙配置指南

在 Ubuntu 24.04 上打开 22、80、443 端口，最常用和推荐的方法是使用 **UFW**（Uncomplicated Firewall），它是 Ubuntu 默认的防火墙管理工具。UFW 是一个基于 iptables 的前端，旨在简化防火墙的配置过程。

---

## 一、 检查 UFW 状态

首先，检查 UFW 是否已经启用：

```bash
sudo ufw status
```

你可能会看到以下两种输出之一：
- **`Status: inactive`**：表示防火墙未启动。
- **`Status: active ...`**（后面跟着规则列表）：表示防火墙已启动。

---

## 二、 启用 UFW（重要注意事项）

如果防火墙是 `inactive` 状态，你需要启用它。

> [!CAUTION]
> **在启用防火墙之前，请务必先允许 SSH（22）端口的访问！**
> 否则一旦启用防火墙，你可能会立即断开与服务器的 SSH 连接，导致无法远程登录！

请按以下顺序执行命令：

```bash
# 1. 首先允许 SSH 端口
sudo ufw allow ssh

# 2. 然后启用 UFW
sudo ufw enable
```

系统会提示你：
`Command may disrupt existing ssh connections. Proceed with operation (y|n)?`
输入 `y` 并回车确认即可。

---

## 三、 开放 22、80、443 端口

现在你可以添加规则来允许指定的端口。以下有两种等价的配置方法：

### 方法一：通过服务名称添加（更易读）
UFW 内置了一些常见服务的默认端口映射（如 `ssh`, `http`, `https`）：

```bash
sudo ufw allow ssh   # 允许 22/tcp 端口 (SSH)
sudo ufw allow http  # 允许 80/tcp 端口 (HTTP)
sudo ufw allow https # 允许 443/tcp 端口 (HTTPS)
```

### 方法二：通过具体端口号添加（更精确）
如果你想明确指定端口号以及传输层协议（通常是 `tcp`）：

```bash
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```

以上两种方法效果完全相同，执行完任一方法后，规则会立即生效。

---

## 四、 验证配置

最后，再次检查 UFW 的状态，确保你的规则已经添加成功且处于激活状态：

```bash
sudo ufw status verbose
```

输出中应当包含类似以下的规则列表，表示对应端口已对外部开放：

```text
To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    Anywhere
80/tcp                     ALLOW IN    Anywhere
443/tcp                    ALLOW IN    Anywhere
```
