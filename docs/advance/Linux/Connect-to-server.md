---
title: 连接服务器
sidebar_position: 2
---

# 连接服务器

Linux 系统上有一个工具被业界广泛使用，它就是 `ssh`。它虽然不能远程控制桌面，但是可以远程登录服务器的命令行，并让服务器执行一些命令。由于 `ssh` 非常常用，现在很多 Linux 发行版都已经默认集成了这个命令。
目前使用最广的提供 ssh 命令的软件是 **OpenSSH**。

## 开启 ssh 服务

为了让客户能顺利连接服务器，云服务器的 sshd 服务一般默认开启。如果你使用的是家里云，或者云服务器的 sshd 服务确实没有开启 (比如你是只能通过服务商提供的 VNC 或者第三方远控软件连接的服务器，无法使用 ssh)，那么你可能需要先开启 sshd 服务才能连接到服务器。
在主流的使用 Systemd 的 Linux 发行版中，执行`systemctl enable --now sshd`命令即可开启 sshd 服务，如果这些命令都报错，证明 sshd 服务存在问题，你可以把报错复制粘贴到搜索引擎上查询怎么修复这个问题。
开启 sshd 服务后，你就可以连接到这台服务器了。

成功开启 ssh 服务后，如果要从公网连接，你还需要把 ssh 服务的端口`22`开放到公网。开放的方法与开放 Windows 的远程桌面端口的方式完全相同，但是协议只需要 TCP 即可。

::: warn

为了安全请不要在服务器上允许 root 用户登录 ssh！如果 ssh 被暴力破解的话会产生非常严重的后果！

最好可以禁用密码登录，仅允许密钥登录

关于配置你服务器的 ssh 使其更安全，可以查看[Arch Linux Wiki 的这篇文章](https://wiki.archlinuxcn.org/wiki/OpenSSH#%E4%BF%9D%E6%8A%A4)

:::

:::danger

配置直接在公网使用 22 端口连接服务器 ssh**会导致严重的安全性问题**，详见[如何抵御网络攻击](../../process/maintenance/how-to-defend-against-cyber-attacks.md)。

另外除非有明确需求，不要随意配置 UDP 协议端口映射，包括上文中提到的**不需要 UDP 协议**的 ssh，否则可能导致你的服务器被 DDoS！详见[如何抵御网络攻击](../../process/maintenance/how-to-defend-against-cyber-attacks.md)。

:::

## 连接 ssh 服务

### Linux 的 ssh 命令

就像 Windows 不用安装任何软件就能连接 Windows 的远程桌面一样，Linux 也内置了连接 ssh 的方式，直接执行 ssh 命令即可连接。它的语法如下：

```shell
ssh <username>@<address> [-p port]
```

如何要指定端口，你需要指定端口参数。在一些操作系统上这个参数是`-p`，例如`ssh root@8aka.org -p 48291`，有一些工具上则是直接在后面输入端口。
例如 Xshell 是`ssh root@8aka.org 48291`。
你需要根据不同的工具的使用方式来确定 ssh 的命令格式。比如，你可以仅执行 `ssh` 命令 (等价于 `ssh --help`)，然后让 ssh 工具提示你如何使用当前工具的这个命令，如果需要更详细的说明可以输入命令 `man ssh`

在输入完这行命令后，服务器通常会要求你输入该用户的密码。

如果你不想手动输密码，可以使用**密钥登录**，这种方法更安全且通常更难以被破解，其步骤为：

1. 使用 `ssh-keygen` 命令生成你的 ssh 密钥。

2. 使用如 `cat .ssh/id_xxxx.pub` 命令来获取你生成的 ssh 公钥 (此命令中`xxxx`的值通常取决于你生成密钥对时选择的算法)

3. 在服务器对应用户的家目录下创建 `./ssh/authorized_keys`，编辑它，将你的公钥粘贴进去，每个公钥独占一行

4. 执行上面的命令，你会发现连接时不再需要密码而是直接弹出 shell

### 使用工具连接

其他操作系统也可以使用工具连接至服务器，在这里举出几个工具：

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs>
  <TabItem value="Powershell" label="Powershell" default>

![](_images/Linux开服/连接服务器/1.png)

Windows 系统自带的 Powershell

按下 `Win + R` 输入 `powershell` 即可 (如果安装了新版的 Powershell 那么你应该输入`pwsh`)

随后在其中输入 `ssh -p <port> <username>@<hostname>` 即可连接 Linux 服务器。

此时会弹出是否保存服务器密钥，选择接受并保存，之后就不会再弹出。

:::tip

port 输入服务器的 ssh 端口

username 为登录服务器的用户名

hostname 为服务器的域名或者 IP

:::

  </TabItem>
  <TabItem value="windterm" label="WindTerm">

![WindTerm](_images/Linux开服/连接服务器/WindTerm.png)

一个开源的 SSH/Telnet/Serial/Shell/Sftp 客户端工具

https://github.com/kingToolbox/WindTerm

  </TabItem>
  <TabItem value="finelshell" label="FinelShell">

![finalshell 终端](_images/Linux开服/连接服务器/2.png)

FinalShell 是一体化的的服务器，网络管理软件，不仅是 ssh 客户端，还是功能强大的开发，运维工具，充分满足开发，运维需求。

  </TabItem>
  <TabItem value="xshell" label="Xshell">

![xshell 终端](https://www.xshell.com/wp-content/uploads/2020/10/p-xshell7-top-zh.png)

他称自己是 业界最强大的 SSH 客户机

  </TabItem>
  <TabItem value="termux" label="安卓手机 (termux)">

你需要安装 termux 这个软件。你可以去 Google Play 下载，也可以去[它的开源地址](https://github.com/termux/termux-app)下载。

安装好之后，打开软件就是命令行，随后直接使用 ssh 命令即可连接。

![termux 终端](_images/Linux开服/连接服务器/termux_screenshot.jpg)

  </TabItem>

  <TabItem value="zsh" label="macOS(zsh)">

macOS 内置 ssh 命令，我们可以用终端来执行它。要打开 macos 上的终端，可以使用以下方式：

- (如果终端 app 没有被移动过) 打开启动台，打开第一页的其他文件夹，点击终端。或者你也可以在应用文件夹 (入口默认固定在访达侧边栏上) 里找到它。

- 按下 command+ 空格或键盘上的搜索键唤起 spotlight，输入“终端”，然后它就会显示在下面。

![macos 终端](_images/Linux开服/连接服务器/macOS_terminal.png)

打开终端后，使用上文中提到的 ssh 命令即可连接到服务器。
  </TabItem>
</Tabs>

除了用 ssh 连接服务器之外，还有可以使用远程桌面。比如 VNC 和 RDP。服务器上一般不配备桌面环境和远程桌面环境，除非是非常需要，否则不建议在服务器上使用远程桌面。
关于桌面环境和远程桌面服务器的搭建，本文档不给予详细阐释，需要者可自行上网搜索相关内容。
