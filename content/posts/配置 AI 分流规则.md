---
title: "配置 AI 分流规则"
date: 2023-05-28
slug: "2023-043"
draft: false
tags: ["tech"]
summary: "适用于 OpenAI, ChatGPT, Bing, Google Bard, Poe, Notion, Pi 的节点分流策略，基于 Surge 编写."
---

## 说明

下面列出的分流规则是我在网络上收集到汇总而成，可能并不完整，欢迎补充。

因为我使用的是 Surge，所以是按照 Surge 的格式编写。共有 29 条规则（我知道有一些是没必要的），其中 DOMAIN-SUFFIX 25 条，DOMAIN 3 条，REJECT 1 条。

**若代码块未显示，请刷新网页。**

## 需设置为 AI 策略组的规则

```
// 关于 OpenAI, ChatGPT 的
DOMAIN-SUFFIX,ai.com
DOMAIN-SUFFIX,auth0.openai.com
DOMAIN-SUFFIX,chat.openai.com
DOMAIN-SUFFIX,chat.openai.com.cdn.cloudflare.net
DOMAIN-SUFFIX,challenges.cloudflare.com
DOMAIN-SUFFIX,featuregates.org
DOMAIN-SUFFIX,identrust.com
DOMAIN-SUFFIX,intercom.io
DOMAIN-SUFFIX,invoice.stripe.com
DOMAIN-SUFFIX,ios.chat.openai.com
DOMAIN-SUFFIX,js.intercomcdn.com
DOMAIN-SUFFIX,openai.com
DOMAIN-SUFFIX,pay.openai.com
DOMAIN-SUFFIX,platform.openai.com
DOMAIN-SUFFIX,stripe.com
DONAIN-SUFFIX,statsigapi.net
DOMAIN,cdn.auth0.com
DOMAIN,openaiapi-site.azureedge.net
DOMAIN,challenges.cloudflare.com

// 关于 Google Bard 的
DOMAIN-SUFFIX,bard.google.com

// 关于 Bing 的
DOMAIN-SUFFIX,bing.com

// 关于 Pi 的
DOMAIN-SUFFIX,heypi.com

// 关于 Poe 的
DOMAIN-SUFFIX,poe.com

// 关于 Notion 的
DOMAIN-SUFFIX,notion-static.com
DOMAIN-SUFFIX,notion.com
DOMAIN-SUFFIX,notion.new
DOMAIN-SUFFIX,notion.site
DOMAIN-SUFFIX,notion.so
```

## 需设置为（广告）拦截的规则

ChatGPT 网页版在使用过程中，js 会向 Sentry 发送跨域请求，其中包含一个 key，[http://Sentry.io](https://t.co/Nfuap4ss1g) 是一个提供日志收集的第三方平台，原则上也可以将这条规则合并到 AI 的策略组里。

```
// REJECT
DOMAIN_SUFFIX, sentry.io
```