---
title: "我使用的 AI 工具"
date: 2023-05-02
slug: "2023-033"
draft: false
tags: ["tech"]
summary: "本文介绍了我使用的一些 AI 工具，包括 Notion AI，New Bing，OpenCat，ChatHub，ChatGPT 和 Poe 等。"
---

{{< alert >}}
本文于 5 月 6 日更新部分内容
{{< /alert >}}

从 11 月 17 日，Notion 宣布开始内测 Notion AI 开始，我就被慢慢训练的开始接受要想使用新产品、新工具就要先加入 waitlist。也不知道是人类在训练 AI 还是 AI 在训练人类。

去年 11 月 30日，ChatGPT 横空出世，如海啸般迅速席卷全球。在 Twitter 上，人们在用各种语言热议着 ChatGPT 将对世界、对人类做出何种改变。

农历新年刚过不久，ChatGPT 终于在国内掀起高潮，各种利用 OpenAI API 的 AI 工具如雨后春笋般冒了出来。软件开发者们争先恐后的推陈出新，使用者们也紧追不舍的持续跟进，大家都不愿意落后于时代。很惭愧，我也是个不例外的俗人。

不完全统计，我目前已经体验过的 AI 模型和工具包括 Craft AI，Notion AI，Lex，ChatGPT，Invoke Ghostreader， Writeathon AI，New Bing，Midjourney，Poe，Claude，OpenCat，MacGPT，ChatGPT for Google，ChatHub，Stable Diffusion，Bard，Image Creator from Microsoft Bing 等十余个。目前依然在频繁使用的是 Notion AI，ChatGPT，Readwise Ghost，New Bing，Poe，OpenCat，ChatGPT for Google 和 ChatHub。

## Notion AI

Notion AI 基于 OpenAI 提供的 GPT-3 模型，经过 Notion 专门的训练后它可以为用户提供自动化的数据分析、文本处理和自然语言处理等功能。核心功能包括：写作、改写、总结、修正、提问、翻译等。

我主要用 Notion AI 帮我修正错别字和标点符号，润色文章，撰写英文邮件和英文 Tweets，翻译和总结 Inoreader 中订阅的外语文章等。

## Inovke Ghostreader

这是一个内置于 Readwise Reader 的功能，模型据悉也是基于 GPT-3，可以向正在浏览的文章提问，总结文章，生成需要深入思考的问题，根据高亮内容生成抽认卡，还可以进行自定义。

现在使用 Readwise Reader 阅读我并不是那么感兴趣的文章时，就会先用这个功能生成文章的摘要，再根据摘要决定读还是不读。有一些重要的文章，则会让其生成问题，作为我阅读笔记的主题。

## New Bing

记得 Satya Nadella 就任微软 CEO 的时候，好友就断言微软会焕发新的活力。从 2014 年到今年，已经过去了 9 年，似乎真的被朋友言中了，至少无论是 Edge Browser 还是 New Bing，抑或 Microsoft 365 Copilot 都在让人们看到微软还是生机勃勃的表象。

和以前的 Bing 比起来，New Bing 好用了很多很多，内置的 GPT-4 + Bing 的搜索引擎积淀，使得一时间 Google 不行了的言论甚嚣尘上。梦总是会醒的，从数据上来看，New Bing 的市场份额还是那样，Google 在搜索引擎赛道上的霸主地位依旧是无可撼动的。

我觉得 New Bing 好用的地方在于，它比 ChatGPT 一本正经的胡说八道和胡编乱造引用链接、论文题目要靠谱很多。现在需要使用搜索引擎搜索的时候，我会有意识的先使用 New Bing，当我对结果不满意时才会用 Google。

目前微软把 New Bing 和 Edge Browser 绑定在一起营销，国内的使用者就算是下载了 Edge，也有极大的概率会因为网络 IP、DNS 等原因不能使用 New Bing。如果您出现了这种情况，或者不想使用 Edge，那么可以下载 [New Bing Anywhere](https://github.com/haozi/New-Bing-Anywhere) 这款插件，让您在任何浏览器（IE 和 Safari 除外）上使用 New Bing 和 Image Creator from Microsoft Bing。

## OpenCat

[OpenCat](https://apps.apple.com/cn/app/opencat/id6445999201) 是独立开发者 [Baye aka 威力狈](https://twitter.com/waylybaye)的作品，它是一个 OpenAI 和 ChatGPT 的原生客户端，提供比 ChatGPT web 版更流畅、更快速的体验。

目前 OpenCat 提供三个版本，免费版和 Pro 版均需要提供 OpenAI 的 API Key，Cloud 订阅版则无需。具体功能可见下图。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/9FMxiY.png)

## [ChatGPT for Google](https://github.com/wong2/chatgpt-google-extension) 和 [ChatHub](https://github.com/chathub-dev/chathub)

这两款浏览器拓展都来自于同一开发者 [wong2](https://twitter.com/wong2_x)，前者可以为 Google、Baidu、Bing、DuckDuckGo、Brave、Yahoo、Naver、Yandex、Kagi、Searx 等十个搜索引擎提供 ChatGPT 支持，后者则实现了 ChatGPT、New Bing、Claude、Bard 等四个模型在同一处使用。

只需要在拓展中添加 OpenAI API Key，经过简单设置，就能够使用了。

我的建议是（土豪请忽略）把 ChatGPT for Google 的 `Trigger Mode` 设置为 Manually（手动）或 Question Mark (只有在句末输入问号才会启动)，节省 API 的使用量。

在 ChatHub 中使用 New Bing 需要先在 [https://www.bing.com/](https://www.bing.com/) 中登录已开通 New Bing 使用权限的账号，使用 Claude 需要先登录 [https://poe.com](https://poe.com)，需要使用 Bard 需在 [https://bard.google.com/](https://bard.google.com/) 登录已开通 Bard 权限的账号。

{{< alert "lightbulb">}}
**5 月 6 日更新：**
ChatHub 现在支持三合一和四宫格模式了。

- 如果习惯用中文写 prompt，可以用三合一模式，ChatGPT、New Bing 和 Claude 都支持中文。

    ![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/CYQpTQ.png)

- 如果习惯用英文写 prompt，可以选四宫格模式。

    ![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/YFm9VI.png)

{{< /alert >}}

## ChatGPT Plus

从 ChatGPT Plus 推出时我就订阅了，真的是非常好用。比起非 Plus 版本响应速度快了很多，而且比起使用 GPT-4 的 API，还不需要担心费用问题。虽然每 3 个小时只能和 GPT-4 进行 25 次对话，勉强够用了。最近，又推出了 GPT-4 with browsing 的 Alpha 版，可以联网了。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/32ScS5.png)

然而，这个联网功能和早先推出的 GPT-3.5 with browsing 一样，都不好用。

这个月不准备续费 ChatGPT Plus 了，转换成 Poe。

## Poe

[Poe](https://poe.com/) 是由美版知乎 Quora 构建的 AI 产品，提供实时在线与 AI 机器人交流。目前自带了 7 个 AI 机器人，包括基于 OpenAI gpt-3.5-turbo 的 `Sage` 和 `ChatGPT`，基于 OpenAI gpt-4 的 `GPT-4`，基于 OpenAI text-davinci-003 的 `Dragonfly`，基于 Anthropic 自研模型的 `Claude+` 和 `Claude-instant`，基于 Neeva 自研模型的 `NeevaAI`。

除了这些自带的机器人，还可以向 OpenCat 那样基于 ChatGPT 或 Claude-instant 建立自己的 AI 机器人，且不需要提供 API。

今天 Poe 宣布网页版也可以订阅了，刚好趁着 ChatGPT Plus 即将到期，「叛变」到了 Poe。理由有三点：

- 同样是 $20 USD 一个月，Poe 不仅可以使用 ChatGPT 和 GPT-4，还可以使用 Claude+ 和 Claude-instant，性价比要比 ChatGPT Plus 高。
- 与 ChatGPT Plus 使用 GPT-4 的限制不同，在 Poe 使用 GPT-4 是每月 600 条，而使用 Claude+ 则是每月 1,000 条。超过了则是进行降速，并不会不能使用。
- 其他的机器人随便使用，没有任何限制。
-

以上就是我使用的 AI 工具介绍，希望对您有所帮助。
