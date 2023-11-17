---
title: "尝试使用 1Panel"
Date: 2023-10-27
Slug: "2023-061"
Draft: "false"
tags:
  - "tech"
Summary: "将 Linus 面板更换成 1Panel 的体验。"
---

上周在大兴机场候机的时候，看到了 [BuyVM 卢森堡](https://my.frantech.ca/cart.php?gid=39)补货的消息。价格十分便宜，1C1G 不限流量的 VPS 一个月只需 3.5 加元，128G 的块存储每月也只需要 1.25 加元。这个价格比我使用 AWS S3 要节省了不少，因为一直缺一个大硬盘的 VPS 用来存放一些文件，就买了。

为了图省事，安装了宝塔面板。紧接着，问题就出现了。我倒是不在意宝塔存在的后门，有安全隐患，而是宝塔让这个小机器实在是不堪重负。CPU 负载长时间保持在满负荷状态，内存占用倒是还好。

原本这个机器买来，也就是通过 WebDAV 存储一下 DEVONthink 的几个 Database，方便我多端同步；然后在从其他的机器上分流几个 docker 过来。可因为 CPU 满负荷，使得机器运行得很慢，使用 SSH 时总得反应几下。

昨天看到[阿杰 Jack](https://twitter.com/real_veryjack) 在说 [1Panel](https://1panel.cn/)，就干脆重装了系统，尝试使用。

去年，Typecho 煤球小程序的作者给我提到过 1Panel，当时只知道这个面板是在 GitHub 上开源的，国内团队开发的。因为宝塔用得比较熟悉，就没有更换。没想到，兜兜转转，还是用上了。

安装的过程很简单，在 1Panel 的[文档](https://1panel.cn/docs/)中有介绍。我只说一下体验。

首先，CPU 终于不再是满负荷运行了，基本稳定在 10% 左右。

其次，内存占用比宝塔高，宝塔差不多 30%，1Panel 基本维持在 40-50%。

![CleanShot2023-10-27at22.18.24@2x](https://cos.justgoidea.com/justgoidea/uPic/2023/10/27/CleanShot%202023-10-27%20at%2022.18.24@2x.png)

第三，模块化的安装，需要重新适应。

安装宝塔面板后，直接会让选择安装 LAMP 或 LNMP 服务器环境。1Panel 安装完成后，没有让选择，而是有需要的时候在应用商店中去安装一个个容器。

>宝塔是一款被广泛使用的 Linux 面板。与宝塔 Linux 面板相比，1Panel 的特色是开源和现代化。
>- 开源：1Panel 强调开源开放，广泛获取社区使用反馈，并快速迭代。
>- 现代化：一方面，1Panel 采纳最新的前端技术，并通过精心设计的 UX 交互，为用户提供更好的用户使用体验；另一方面，1Panel 采用主流的容器技术，让 Linux 服务器的运维管理更简单、更安全。

比如，我要搭建一个网站，需要使用 web 服务器 Nginx，在宝塔上是安装服务器环境时直接安装了 Nginx，而在 1Panel 中就需要在应用商店中下载 OpenResty。运行环境需要 PHP 或 Node.js，也是在应用商店中去找需要的 PHP 或 Node.js 版本安装。

这样模块化的好处，我觉得是不需要让服务器一下子安装那么多程序，按需安装，便捷管理。

![1panel应用商店](https://cos.justgoidea.com/justgoidea/uPic/2023/10/27/1panel应用商店.png)

第四，网站配置与防火墙设置更符合直觉。虽然宝塔已经比较便于「小白」用户使用，1Panel 则是更加清晰。

![1panel网站设置](https://cos.justgoidea.com/justgoidea/uPic/2023/10/27/1panel网站设置.png)

![1panel防火墙设置](https://cos.justgoidea.com/justgoidea/uPic/2023/10/27/1panel防火墙设置.png)

第五，UI 真的很漂亮，如果说宝塔是老气横秋，1Panel 则是小清新。

总体来说，此次尝试 1Panel 还是比较欣喜的，也打算将另外两台 VPS 的面板替换成 1Panel。不过问题也还是有的。比如机器上挂载了块存储，但是容器没有办法安装到块存储上。