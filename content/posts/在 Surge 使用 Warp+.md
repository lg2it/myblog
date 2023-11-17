---
title: "在 Surge 使用 Warp+"
date: 2023-04-19
slug: "2023-025"
draft: false
tags: ["tech"]
summary: "文介绍了如何在 Surge 中使用 Warp+，并分享了具体的操作步骤。"
---

Warp+ 是 CloudFlare 推出的可以用来保护使用者隐私的一款服务，基于 wireguard 协议，使用 UDP 来传输数据，因其 IP 地址较为纯净，可以用来解锁流媒体，谷歌学术等。

Surge 是 macOS 和 iOS 上的一款网络代理工具。

今天尝试了在 Surge 中配置 Warp+，成功实现代理。

下面就分享我的具体操作步骤。

---

## 步骤一：安装 Homebrew

{{< alert >}}
要在 Surge 上使用 Warp+，因为要通过 [Homebrew](https://brew.sh/index_zh-cn) 调用 GitHub 上的 [wgfc](https://github.com/ViRb3/wgcf) 这个项目，所以要确认 macOS 已经安装了 Homebrew。
{{< /alert >}}

首先，在 macOS 中打开 Terminal （终端），然后输入以下代码，查看电脑上的 Homebrew 版本。

```bash
brew --version
```

如下图红框中所示，我的电脑上 Homebrew 的版本为 4.0.14。如果没有显示红框中的内容，则正面您的电脑上没有安装 Homebrew。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/cLbI8x.png)

安装 Homebrew，是在 Terminal 中输入如下代码：

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

然后等待安装完毕即可。

如果安装完毕后出现如下代码，是因为虽然 Homebrew 已经成功安装在您的 macOS 上了。但是，由于 **`/opt/homebrew/bin`** 目录尚未添加到您的 PATH 环境变量中，因此您需要按照以下步骤配置您的 shell 以使用 Homebrew。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/UJ8rDT.png)

此时您需要在 Terminal 中输入如下代码：

```bash
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/username/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

{{< alert >}}
请将代码中的 `username` 替换成您的电脑用户名。
{{< /alert >}}

之后，Homebrew 就已经在您的 macOS 中完成安装，并可以正常运行了。

## 步骤二：获取 Warp+ Key

您可以通过在 Telegram 上通过 `Warp+ Bot`  [https://t.me/generatewarpplusbot](https://t.me/generatewarpplusbot) 获取赠送的流量总计为 24 PB 的 Key。

若需验证获取的 Key 是否可用，则需要在 macOS 上安装 [Cloudflare WARP](https://developers.cloudflare.com/cloudflare-one/connections/connect-devices/warp/download-warp/) 或者在 iOS 上安装 [1.1.1.1](https://apps.apple.com/us/app/id1423538627)，之后就可以在 app 中验证获取的 Key 是否有效，流量余额是多少。

## 步骤三：**通过 wgcf 获取配置**

打开 Terminal（终端），然后输入 `brew install wgcf` 开始安装 wgcf。

等待代码运行，安装完毕后输入 `wgcf register` 获取文件名为 `wgcf-account.toml` 的文件。该文件可以在 `/Users/username/` 中找到（快捷键：shift+cmd+h）。

接下来用文本编辑器打开这个文件，将其中的 license key 替换成您在步骤二中申请到的 Key，并保存文件。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/JOCvpQ.png)

保存好后，再到 Terminal 中输入 `wgcf update` 并运行，此时配置文件就更新了。

## 步骤四：**生成 Surge 可用的配置文件**

退出 Surge、AdGuard 等相关影响网络的软件，然后在 Terminal（终端）中运行 `wgcf generate`，此时 `/Users/username/` 中会新生成一个名为 `wgcf-profile.conf` 的文件。

## 步骤五：在 Surge 中配置 Warp+

打开 Surge，并使用文本编辑器打开步骤四中生成的名为 `wgcf-profile.conf` 的文件。

根据下图将 `wgcf-profile.conf` 中的内容按照下图所示填入 Surge 中即可。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/zUflhd.png)

## Reference

- [https://pepcn.com/surge/warp-liu-liang-da-pei-surge](https://pepcn.com/surge/warp-liu-liang-da-pei-surge)
- [https://www.jkg.tw/p3630/](https://www.jkg.tw/p3630/)
