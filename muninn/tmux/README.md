# 让 Tmux 读取现代路径下的配置文件

## 在 Tmux 里面

按下 Ctrl+a，松开，再按 :（冒号），在底部输入：
```Plaintext
source-file ~/.config/tmux/tmux.conf
```
然后回车即可。

## 在 Tmux 外面

直接输入下面的命令强行刷新：
```Bash
tmux source-file ~/.config/tmux/tmux.conf
```


# 使用 tmux-resurrect
这个插件的用法非常简单，只有两个核心快捷键：

## 保存当前的环境（存档）
当你辛辛苦苦分好了屏、打开了各种代码和日志，准备下班时：
按下 Ctrl+a，松开，然后按下 Ctrl + s（s 代表 Save）。
你会看到终端底部闪过一行提示：Tmux environment saved!，说明当前的“工作现场”已经成功存档。

## 恢复之前的环境（读档）
万一遇到服务器重启、或者你误杀了自己的 Tmux 进程，当你再次输入 tmux 进去时，发现里面是一个空空如也的新窗口。别慌：
按下 Ctrl+a，松开，然后按下 Ctrl + r（r 代表 Restore）。
见证奇迹的时刻：你之前所有的分屏布局、甚至你刚刚正在编辑的文件路径，都会在 1 秒钟内瞬间复原。

## 自动存档读档
如果你觉得每次都要手动 Ctrl+s 存档太麻烦，容易忘，你还可以顺手把它的兄弟插件 tmux-continuum 也装上。
只需要在 .tmux.conf 里的 set -g @plugin 'tmux-plugins/tmux-resurrect' 下面添加：
```
set -g @plugin 'tmux-plugins/tmux-continuum'
set -g @continuum-restore 'on' # 开启自动恢复
```
保存后同样在 Tmux 里按 Ctrl+a + I 安装。这样它就会每隔 15 分钟在后台悄悄帮你存一次档，并且在你登录服务器时自动帮你“读档”，彻底实现无感灾备！
