# 服务器工具

## 图形化界面

参考`VS Code`的[教程](https://code.visualstudio.com/docs/remote/ssh)。

## tldr

`tldr`是一个命令行工具，可以查看常用命令的简单用法。


## fish（可选）

建议使用`fish`作为 shell，`oh-my-fish`作为`fish`的插件管理器。

将`fish`设置为默认 shell：

```bash
chsh -s /usr/bin/fish
```

安装`oh-my-fish`：

```bash
curl https://raw.githubusercontent.com/oh-my-fish/oh-my-fish/master/bin/install | fish
```

## tmux

`tmux`是一个终端工具，最常用的场景是，在因为网络等原因断开与服务器连接后，保持正在执行的进程继续执行。使用教程可以参考[这里](https://www.redhat.com/en/blog/introduction-tmux-linux)。

如果忘记了指令，可以使用`tldr tmux`查看。

## git

`git`是一个版本控制工具，使用教程可以参考[这里](https://docs.github.com/en/get-started/using-git)。然后尝试[这个](https://docs.github.com/en/get-started/start-your-journey/hello-world)教程。

如果忘记了指令，可以使用`tldr git`查看。

在掌握了基本 `git` 操作后，请学习 `Github` 的[协作流程](github.md)。
