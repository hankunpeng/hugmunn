# ~/.gitconfig

```
[alias]
  # 基础操作简化
  st = status
  co = checkout
  br = branch
  cp = cherry-pick
    
  # 提交修改
  cm = commit -m
  amend = commit --amend --no-edit
    
  # 安全的强制推送（防止覆盖他人代码）
  pf = push --force-with-lease
    
  # 清理本地存在但远程已删除的分支映射
  prune = fetch --prune
    
  # 结构化且美观的图形化提交日志
  lg = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```