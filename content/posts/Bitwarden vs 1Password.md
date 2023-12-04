---
title: "Bitwarden vs 1Password"
date: 2023-06-10
slug: "2023-046"
draft: false
tags: ["tech"]
summary: "两个顶级密码管理器的比较"
---

## TL;DR

|  | Bitwarden | 1Password |
| --- | --- | --- |
| 特色 | 用户名和密码生成器
|    | 密码、安全笔记、信用卡、身份存储 | 安全的密码生成、存储和自动填写 |
|  |Authenticator|安全的密码生成、存储和自动填写|
||可自我托管|密码共享|
||电子邮件别名整合|密码恢复|
||加密发送（Bitwarden sent）|Authenticator|
||先进的 2FA|Watchtower|
||1GB 的组织存储附件|旅行模式|
||加密的文件附件|暗网监控|
||保险库健康报告 | 活动追踪 |
| 安全性 | 从不妥协|从不妥协|
||端到端加密|256 位 AES 加密|
||强散列算法|PBKDF 2 密码散列|
||多因素认证|128 位密匙|
||数据安全审计|安全审计|
||开放源代码 | 多因素认证 |
| 兼容性 | Windows|Windows|
||macOS|macOS|
||Linux|Linux|
||iOS/iPadOS|iOS/iPadOS|
||Android|Android|
||Chrome|Chrome|
||Edge|Edge|
||Safari|Safari|
||Firefox|FireFox|
||Opera|Opera|
||Vivaldi|Arc |
||Brave|
||Arc|
||Tor | 
| 价格 | Free: $0|Free: Not available|
|| Premium: $10/year |Individual: $2.99/month|
||Family: $40/year|Family: $4.99/month|
||Teams Organization: $3/user/month|Teams: $19.95/month (10 users)|
||Enterprise Organization: $5/user/month | Business: $7.99/user/month |

## 安全性

Bitwarden 和 1Password 都提供了顶级密码管理器中应有的强大安全功能，包括强加密、多因素认证和独立审计等。更重要的是，它们都没有遭受过安全漏洞，这是其他密码管理器目前无法做到的。

两者都利用强大的加密算法，采用端到端的 256 位 AES 加密，被认为是高度安全且几乎无法破解的。由于保护数据的重要性，两者都采用了”zero-knowledge” 模式，这意味着这两家都无法从内部访问私人用户数据。

两者也都需要一个主密码来访问密码库。其中，1Password 采用了一个额外的秘钥，作为额外的保护层。而 Bitwarden 则提供与谷歌认证器等第三方认证应用程序的整合，同时还为高级账户提供了一个内置的认证器。相比较之下，1Password 仅支持各种 MFA 选项，包括 Authy 和 Microsoft Authenticator 的插件。

Bitwarden 和 1Password 都接受了独立的安全审计，以验证其安全实践并确保其系统的完整性。这些审计为这两个服务实现的安全措施提供了额外的信心。

另外，Bitwarden 是开源的，这就意味着它允许公众对其代码进行审查，而 1Password 的代码不能被外部检查是否存在漏洞。

## 特色

Bitwarden 和1Password 作为目前市面上的顶级密码管理器，在提供一系列共享功能的同时，也提供了一些独特的功能。

相同点是，两者都为各种在线账户提供简单直观的密码存储、生成和自动填写功能。它们提供浏览器扩展、移动应用程序和基于网络的界面，保证在不同设备和平台上轻松访问。这两个密码管理器也都通过支持各种类型的双因素认证，将安全放在首要位置，还都提供安全的密码共享选项，允许用户与受信任的人之间安全地共享密码。

不同的是，1Password 的 watchtower 功能（评估密码强度、识别是否在多个网站使用，是否被泄露等）是集成在程序中的，而 Bitwarden 则仅在网页版中提供有限的支持。

1Password 还提供了旅行模式，这是 Bitwarden 没有的功能。

Bitwarden Sent 功能则是 1Password 不具备的，这是一个使用户能够安全地与他人分享密码、安全笔记和身份信息等内容的强大功能，即使接收者并不使用 Bitwarden。在 Bitwarden Sent 中，用户可以控制与共享数据的互动程度，如设置失效日期、查看次数等。

此外，Bitwarden 还为用户提供了输入多个统一资源标识符(URI)作为密码的灵活性，允许用户跨多个网站使用相同的登录凭证。它还提供了在特定站点的自动填充期间重新提示主密码的选项。

得益于开源的代码，Bitwarden 提供了自托管的选项，允许用户通过 Docker 进行部署。

## 兼容性

两者都有很强大的系统与浏览器兼容性，只是 Bitwarden 还提供了网页版，使用户可以通过网页访问密码保险库。

1Password 则在交互上做得更好。

## 价格

在价格方面，Bitwarden 仅有的优势是如果不需要 Authenticator，2FA 等功能，免费版就已经足够使用，并且高级版本仅需 10 美元/年。而 1Password 是不提供免费版本的，每年的价格为 36 美元。但是如果是团队版本，1Password 的价格则更便宜。