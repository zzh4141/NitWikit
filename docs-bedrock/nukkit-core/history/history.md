---
title: Nukkit 核心介绍
sidebar_position: 1
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

:::tip
在《我的世界：基岩版》中，Nukkit 作为最早的服务器软件之一，开启了多人服务器的先河。它凭借高性能、稳定性和可定制性，为玩家和开发者提供了全新体验，推动了技术进步和社区繁荣。然而，随着网易《我的世界》的出现，Nukkit 逐渐成为历史的遗憾。但它的精神和贡献激励着后继开发者继续探索和创新，为基岩版社区注入新活力，书写新的未来。
:::

![Nukkit logo](https://wiki.mcbe-dev.net/w/thumb.php?f=Nukkit.png&width=96)

<div align="center">Nukkit：核能驱动的 Minecraft 基岩版服务器软件。</div>

## 什么是 Nukkit

Nukkit（简称 NK）是由 MagicDroidX 发起的，使用 Java 编写的基岩版服务端核心。初版 Nukkit 的 GitHub 仓库于 2015 年 5 月 23 日首次提交，现已停止维护。NukkitX 是被原 Nukkit 团队官方认可并由 CloudburstMC 团队积极维护的分支版本。

Nukkit 拥有相当丰富的社区分支，例如 PM1E、PowerNukkit 和 PowerNukkitX 等。它们自携带版 0.12 更迭至今，共同成就了灿烂辉煌的 Nukkit 社区。

## 服务端特点

### 优势

- 作为老牌开源服务端，Nukkit 拥有强大的社区支持和良好的社区生态；
- Nukkit 提供完善、便捷、强大的插件支持，目前公开发布的插件已多达数万个；
- Nukkit 适于大型服务器的搭建，其可靠地支撑了诸如花雨庭、EaseCation 等玩家众多的知名基岩版服务器；
- Nukkit 的大多数分支仍在迅速更新维护，庞大的社区帮助开发者及时有效解决问题，第一时间跟进游戏版本；
- Nukkit 提供 PocketMine 风格 API，却有更大的性能优势；
- 相较于其他服务端，在 Linux 上使用 Nukkit 有极大的性能优势，在 Windows 上同样表现优异。

### 劣势

- Nukkit 最初为小游戏服务器设计，抛弃了很多原版游戏特性；
- Java 虚拟机（jvm）环境版本兼容性差；
- Java 多线程的优势并未得到充分利用；
- 传统的石山代码和一些过时的架构影响着服务端的性能。

## 服务端分支

### 主流服务端
<!--markdownlint-disable line-length-->

<Tabs queryString="nukkit-history">
<TabItem value="NukkitX" label="NukkitX">

| NukkitX | 别名：NKX |
| --- | --- |
| 相关链接 | [NukkitX 官网](https://cloudburstmc.org/)、[Github 仓库](https://github.com/CloudburstMC/Nukkit) |
| 作者 | [CloudburstMC](https://github.com/CloudburstMC) |
| 介绍 | NukkitX（原为 Nukkit2.0）是一个基于 Java 开发的高性能、开源的 Minecraft Bedrock Edition 服务端软件，继承了 Nukkit 的代码并不断优化，支持多种平台和丰富的插件扩展，为玩家和开发者提供了更稳定、更灵活的多人游戏体验 |
| 下载 | [构建站](https://ci.opencollab.dev/job/NukkitX/job/Nukkit/job/master/) |
| 支持的 MC 版本 | 1.14.x-最新版 (目前保持更新) |

</TabItem>
<TabItem value="Nukkit-MOT" label="Nukkit-MOT">

| Nukkit-MOT | 别名：NMOT |
| --- | --- |
| 相关链接 | [Nukkit-MOT 官网](https://www.nukkit-mot.com/)、[Github 仓库](https://github.com/MemoriesOfTime/Nukkit-MOT) |
| 作者 | [MemoriesOfTime](https://github.com/MemoriesOfTime) |
| 介绍 | Nukkit-MOT 是基于 NukkitPetteriM1Edition 开发的 Minecraft Bedrock Edition 服务器软件，支持 1.2 至 1.21.50 版本，内置生物 AI 和原版命令，支持多版本协议和丰富的游戏特性 |
| 下载 | [构建站](https://motci.cn/job/Nukkit-MOT/job/master/) |
| 支持的 MC 版本 | 1.18.x-最新版 (目前保持更新) |

</TabItem>
<TabItem value="PowerNukkitX" label="PowrNukkitX">

| PowerNukkitX | 别名：PNX |
| --- | --- |
| 相关链接 | [PowerNukkitX 官网](https://www.powernukkitx.cn/)、[Github 仓库](https://github.com/PowerNukkitX/PowerNukkitX) |
| 作者 | [PowerNukkitX](https://github.com/PowerNukkitX) |
| 介绍 | PowerNukkitX（简称 PNX）是基于 PowerNukkit 和 Nukkit 的修改优化版本，修复了其 bug，添加了 BlocklyNukkit，LiteLoaderBDS 插件等更多功能的支持，内置了 Java 版服务端插件史诗地形生成器 (Terra) |
| 下载 | [Github](https://github.com/PowerNukkitX/PowerNukkitX/releases/download/snapshot/powernukkitx-run.zip) |
| 支持的 MC 版本 | 1.17.x-最新版 (目前保持更新) |

</TabItem>
</Tabs>

### 受争议的服务端

:::info
此类服务端是因为其发生了一些令人抽象的事情，亦或者是某些原因导致名气变差 or 暂缓更新，但不代表他们不会更新
:::

<Tabs queryString="nukkit-history">
<TabItem value="NukkitPetteriM1Edition" label="NukkitPetteriM1Edition">

| NukkitPetteriM1Edition | 别名：PM1ENK、Nukkit-PM1E、PM1E |
| --- | --- |
| 相关链接 | [Github 仓库](https://github.com/PetteriM1/NukkitPetteriM1Edition) |
| 作者 | [PetteriM1](https://github.com/PetteriM1/) |
| 介绍 | Nukkit PetteriM1 Edition 是一个基于 Java 开发的 Minecraft Bedrock Edition 服务器软件的定制版本，由 Nukkit 核心开发者 PetteriM1 制作，支持从 1.2 到 最新版版本 的多客户端，并内置生物 AI 和生成功能 |
| 下载 | [Github Releases](https://github.com/PetteriM1/NukkitPetteriM1Edition/releases) |
| 支持的 MC 版本 | 1.13.x-最新版 (目前保持更新) |
| **争议问题** | **2022 年 11 月 15 日，PetteriM1 删除了 PM1E 仓库下的所有代码，并表示接下来只会发布混淆过的 jar 文件供使用。此举引起了社区的强烈不满，据知情人士透露，这么做的原因是为了防止"别人抄袭他的代码"。而在闭源后，PM1ENK 又被指控在接下来的更新中存在对 PowerNukkitX 的抄袭。在此期间，一位名为 sora-kawaii 的 Github 用户成功反混淆了 PM1ENK 并公布了源码，公开的代码显示了 PM1ENK 对开源项目的抄袭。2023 年 1 月 18 日，PM1ENK 发布了更新，此次更新被认为使用了业内最贵的付费混淆器 ZKM 以加强混淆效果，这一违背开源协议的行为立刻掀起了社区中抵制 PM1ENK 的浪潮，随后社区推出了基于 PM1ENK 最后一个开源版本开发的 Nukkit-MOT 核心。*（参考文章：刀哥《[为什么你不应该使用 PM1ENK - 细说 PM1ENK 的罪状](https://www.minebbs.com/threads/pm1enk-pm1enk.16912/)》*）** |

</TabItem>
</Tabs>

### 寿终正寝的服务端

<Tabs queryString="nukkit-history">
<TabItem value="Nukkit" label="Nukkit">

| Nukkit | 别名：NK |
| --- | --- |
| 相关链接 | [Github 仓库](https://github.com/Nukkit/Nukkit) |
| 作者 | [Nukkit Project](https://github.com/Nukkit) |
| 介绍 | 第一代 Nukkit，现已停止更新并转移到 Nukkit2.0（项目重命名为 NukkitX） |
| 下载 | 无 |
| 支持的 MC 版本 | 携带版 0.12-1.14.x |

</TabItem>
<TabItem value="PowerNukkit" label="PowerNukkit">

| PowerNukkit | --- |
| --- | --- |
| 相关链接 | [PowerNukkit 官网](https://powernukkit.org/)、[Github 仓库](https://github.com/PowerNukkit/PowerNukkit) |
| 作者 | [PowerNukkit](https://github.com/PowerNukkit/) |
| 介绍 | PowerNukkit 是一个基于 Nukkit 的 Minecraft Bedrock Edition 服务器软件分支，支持几乎所有单机方块和物品，增加了大量新特性（如含水方块、红石、副手槽等），并修复了众多在 Nukkit 上出现的 Bug |
| 下载 | [Github Releases](https://github.com/PowerNukkit/PowerNukkit/releases) |
| 支持的 MC 版本 | 1.12.x-1.18.0 |

</TabItem>
<TabItem value="NukkitPetteriM1Edition-MOT" label="NukkitPetteriM1Edition-MOT">

| NukkitPetteriM1Edition-MOT | --- |
| --- | --- |
| 相关链接 | [Github 仓库](https://github.com/MemoriesOfTime/NukkitPetteriM1Edition) |
| 作者 | [MemoriesOfTime](https://github.com/MemoriesOfTime) |
| 介绍 | NukkitPetteriM1Edition 事件发生后，MemoriesOfTime 团队第一时间保存了该项目的最后一次更新的代码，并结合了 sora-kawaii 反编译开源出来的代码进行续写并转移仓库为 **Nukkit-MOT** |
| 下载 | 无 |
| 支持的 MC 版本 | 1.18.x |

</TabItem>
</Tabs>

<!--markdownlint-enable line-length-->
