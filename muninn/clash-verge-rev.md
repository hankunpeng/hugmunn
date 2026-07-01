# Clash Verge


## 配置文件

```
ls -l /Users/alex/Library/Application\ Support/io.github.clash-verge-rev.clash-verge-rev/
```

各个 .yaml 文件分别承担客户端自身设置、订阅管理以及 Clash 内核运行配置的作用。


### 客户端主程序配置

- verge.yaml
  - 作用：Clash Verge Rev 客户端自身的主配置文件。
  - 内容：存储软件界面设置（如语言、主题、窗口大小）、开机自启、系统代理开关状态、选中的内核类型（如 Mihomo/Clash Meta）以及延迟测试 URL 等应用层面的选项。
- profiles.yaml
  - 作用：配置文件的管理索引。
  - 内容：记录当前客户端中导入的所有订阅链接、本地文件的元数据（名称、更新时间、更新周期）以及当前正在激活使用的是哪一个配置文件。对应的具体配置文件内容存储在 profiles/ 文件夹中。

### Clash 内核运行与校验配置
- config.yaml
  - 作用：最终传递给 Clash 内核并直接生效的运行配置文件。
  - 内容：当启动代理时，客户端会读取当前激活的订阅文件，合并用户的自定义扩展规则（Merge / Script），生成这个最终的 config.yaml 供内核消费。
- clash-verge.yaml
  - 作用：客户端内部的全局基础配置模板。
  - 内容：包含软件默认的通用混合配置，作为生成最终 config.yaml 的基础框架。
- clash-verge-check.yaml
  - 作用：配置合规性校验文件。
  - 内容：在用户刷新订阅或切换配置时，客户端会先生成该文件并调用内核进行语法和格式检查。校验通过后，才会将其应用到实际运行中，以防止因订阅内容报错导致内核崩溃。

### DNS 独立配置
- dns_config.yaml
  - 作用：用户自定义的 DNS 配置文件。
  - 内容：如果在软件的 DNS 界面中开启了独立 DNS 设置或内置脚本，相关的 DNS 服务器（Nameserver、Fallback）及 Fake-IP 过滤等规则会保存在此文件中。
- bak_dns_config.yaml
  - 作用：DNS 配置的历史备份文件。
  - 内容：在修改或重置 DNS 设置时自动生成的旧版本备份，供系统恢复使用。

