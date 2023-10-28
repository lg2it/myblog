---
title: "Prompt 和 Claude-instant-100k"
date: 2023-05-17
slug: "2023-039"
draft: false
tags: ["tech"]
summary: "GPT-4 给出的 20 个常用 prompt，和 Claude 分析论文后总结的 16 个 prompt 框架。"
---

![数字艺术，少年在樱花满山的道路上行走，古寺庙在远方，光线透过樱花树洒在少年身上，动漫风格，鲜艳的粉色与深蓝色调，--ar 4:3](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/qsRigQ.png)

数字艺术，少年在樱花满山的道路上行走，古寺庙在远方，光线透过樱花树洒在少年身上，动漫风格，鲜艳的粉色与深蓝色调，--ar 4:3

## 一

GPT-4 自己列出了 20 个常用 prompt。

| No. | 模式名称 | Prompt 示例 |
| --- | --- | --- |
| 1 | Generate Ideas
生成创意 | List 10 potential solutions to the problem at hand
列出10个可能的解决方案 |
| 2 | Summarize Information
概括信息 | Summarize the key points from this article in one paragraph.
用一段话总结这篇文章的关键点 |
| 3 | Brainstorm Names
集思广益命名 | Generate 5 possible names for this new product.
为这个新产品生成5个可能的名称 |
| 4 | Proofread
校对 | Proofread this document for errors and suggest corrections.
校对此文档的错误并建议修改 |
| 5 | Generate Headlines
生成标题 | Come up with 3 catchy headlines for this blog post.
为这篇博客文章想出3个吸引人的标题 |
| 6 | Paraphrase
改述 | Rewrite this paragraph in your own words.
用你自己的话重写这一段 |
| 7 | Write Descriptions
编写描述 | Write a short description of this product for the website.
为网站编写该产品的简短描述 |
| 8 | Create Outlines
创建大纲 | Create an outline for this research paper.
为这篇研究论文创建大纲 |
| 9 | Translate
翻译 | Translate this document from English to Spanish.
将此文档从英语翻译成西班牙语 |
| 10 | Generate Questions
生成问题 | List 5 questions that you would ask in an interview with this candidate.
列出你将在这个候选人的面试中提出的5个问题 |
| 11 | Generate Social Media Posts
生成社交媒体帖子 | Create 3 social media posts to promote this event.
创建3个社交媒体帖子来推广这个活动 |
| 12 | Generate ProductDescriptions
生成产品描述 | Write a product description for each of these 5 items.
为这5个项目各写一个产品描述 |
| 13 | Generate Taglines
生成标语 | Create 2 taglines for this advertising campaign.
为这个广告活动创建2个标语 |
| 14 | Generate Email Templates
生成电子邮件模板 | Create an email template to respond to customer inquiries.
创建一个响应客户询问的电子邮件模板 |
| 15 | Generate Blog Posts
生成博客文章 | Write a 500-word blog post on this topic.
写一篇关于这个主题的500字博客文章 |
| 16 | Generate Product Reviews
生成产品评论 | Write a review of this product for the website.
为网站写一篇这个产品的评论 |
| 17 | Generate Ad Copy
生成广告文案 | Write a short ad for this product.
为这个产品写一份简短的广告 |
| 18 | Generate Job Descriptions
生成工作描述 | Write a job description for this position.
为这个职位写一份工作描述 |
| 19 | Generate Website Copy
生成网站文案 | Write the copy for the homepage of this website.
为这个网站的主页写文案 |
| 20 | Generate News Articles
生成新闻文章 | Write a news article on this current event.
写一篇关于这个当前事件的新闻文章 |

## 二

今天，在 Poe 尝试了 Claude-instant-100k，粘贴给他一篇一万七千多字的论文 *[A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT](https://arxiv.org/pdf/2302.11382.pdf)*，Claude 以很快的速度进行了阅读理解和阅读分析。

> 提示模式的概念是一个有用的框架，用于解决大型语言模型常见问题的输入结构。记录和编目这些模式可以帮助用户开发更有效的提示。
>

> 提示的形式类似于软件模式，但进行了适应以适合大型语言模型。用于描述模式结构的基本上下文语句方法运作良好，对用户来说直观易懂。
>

> 16 种 prompt 的目录覆盖了从定制输出到改进输入和交互的广泛目标。组合模式可以产生更强大的能力。
>

> 有效应用提示模式需要考虑其结果和限制，例如过度过滤输出或无意中去除有用的上下文。组合模式可以帮助解决一些问题。
>

> 随着大型语言模型能力的发展，对模式的进一步细化和扩展以及对大型语言模型的新用途的探索可能会持续进行。将模式扩展为完整的语言可能会更有效地指导用户。
>

> 这些模式对不同领域的通用性表明，可以开发特定领域的模式目录，以共享特定领域的提示解决方案。
>

> 总的来说，这项工作为思考和构建大型语言模型的提示提供了一个有用的起点。提示模式的概念有可能系统地改善与大型语言模型的交互并利用其能力。
>

然后，Claude 给出了使用不同 prompt 的一些提示：

- 在指示中要具体明确。提供的细节越多，语言模型遵循您的意图的可能性就越大。
- 从广泛的方面开始，逐步细化。先从基本提示开始，看输出，然后使用更多限制进行细化。
- 结合模式以实现更复杂的目标。多种模式组合在一起可以创建新颖的功能。
- 监控输出以发现错误或偏差。语言模型仍然容易出错，因此要仔细检查输出。
- 实践负责任和道德的使用。确保您的提示不会违反政策或伤害他人。
- 实验！尝试不同的提示、模式和语言模型，找到最适合您需求的方法。

| No. | 模式名称 | 解释 | Prompt 示例 |
| --- | --- | --- | --- |
| 1 | 元语言创建 | 提供规则来定义语言模型可以理解的自定义语言。 | 当我使用符号 → 时，我意味着两边的两样东西之间有连接。 |
| 2 | 输出自动化 | 指导语言模型从其输出中生成脚本或自动化工件。 | 当你提出多个步骤时，生成一个 Python 脚本，它将自动执行这些步骤。 |
| 3 | 翻转交互 | 告诉语言模型向你提问以实现特定目标。 | 向我提出问题以收集足够的信息以将我的网络应用部署到 AWS。 |
| 4 | 角色设定 | 指导语言模型在生成输出时扮演某个角色或身份。 | 扮演安全专家。重点关注代码中的任何漏洞。 |
| 5 | 可视化生成器 | 要求语言模型生成可用于可视化工具的文本输入。 | 生成一个 Dot 文件，我可以将其输入到 Graphviz 中以可视化网络拓扑。 |
| 6 | 步骤 | 提供目标和已知/未知的"成分"来制定步骤序列。 | 我想将 Docker 容器部署到 AWS。生成一个使用我的 EC2 实例的分步步骤。 |
| 7 | 模板 | 给语言模型一个需要填充内容的模板。 | 生成符合此 JSON 模板的 API 响应：{ "name": "", "job": ""} |
| 8 | 事实核查清单 | 要求语言模型在其输出中生成事实列表。 | 在你的输出结束时，生成一个需要验证的事实列表。 |
| 9 | 反思 | 指导语言模型解释其输出背后的原因。 | 解释你建议的代码更改背后的原因。 |
| 10 | 问题改进 | 要求语言模型提出对你的问题的改进建议。 | 建议一个更好的版本的我的问题，排除无关的细节。 |
| 11 | 替代方法 | 提供限制条件并要求提供替代解决方案。 | 提供两种替代方式将应用程序部署到云端。 |
| 12 | 认知验证器 | 要求语言模型将问题分解为更多的问题。 | 将我的问题分解成3个子问题，并合并答案。 |
| 13 | 拒绝破坏者 | 要求语言模型重述它拒绝回答的问题。 | 建议我可以回答的问题的另一种表述。 |
| 14 | 上下文管理器 | 为语言模型指定需要考虑或忽略的上下文。 | 忽略所有以前的讨论。从新的上下文开始。 |
| 15 | 游戏玩法 | 要求语言模型围绕指定主题生成一个游戏。 | 创建一个关于网络安全的风险类测验游戏。 |
| 16 | 无限生成 | 要求语言模型无限地生成输出。 | 生成5个随机名称和职称，然后再生成5个。 |

从我使用的感受来看，Claude-instant-100k 表现的非常好，应该说可以和 ChatGPT 中的 AskYourPDF 这个插件的效果是相同的了。当然，因为 AskYourPDF 是使用的 URL，而 Claude-instant-100k 是复制粘贴进去的，不可能像 AskYourPDF 那样给出页码。

我对于二者没有进行具体的对比，所以询问了 Bard，他给出的答案是这样的**（真实性请自行判断）**：

> Claude-instant-100k 和 ChatGPT 都是大型语言模型，可用于生成文本，翻译语言，编写不同类型的创意内容，并以信息丰富的方式回答您的问题。然而，这两种模型之间存在一些关键区别。
>
>
> Claude-instant-100k 是一个生成式预训练变换器模型，它在大量的文本和代码数据集上进行了训练。它能够生成既流畅又具有信息量的文本，可以用于各种任务，如写文章，翻译语言，和生成创意内容。
>
> ChatGPT AskYourPDF plugin 是运行在 ChatGPT 上的一个插件，它在与 PDF 文件相关的文本和代码数据集上进行了训练。它专门设计用于回答有关 PDF 文件的问题，可以用于从 PDF 文件中提取信息，生成 PDF 文件的摘要，并将 PDF 文件翻译成其他语言。
>
> 总的来说，Claude-instant-100k 是一个比 ChatGPT AskYourPDF plugin 更强大的语言模型。然而，ChatGPT AskYourPDF 插件对于与 PDF 文件相关的任务更加专业。
>
