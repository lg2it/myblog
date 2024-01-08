---
title: "利用 NotionNext 快速部署博客系统"
date: 2022-07-17
slug: "2022-005"
draft: false
tags: ["tech"]
summary: "NotionNext是一个开源的博客生成器，可以将Notion笔记渲染成静态博客并托管在Vercel云服务中。它具有快速秒开、自动增量式更新、全功能、美观自定义、多主题切换等特点，同时支持自定义域名和Hexo主题封面文字修改。NotionNext的部署方式简便易行，只需要通过Vercel一键部署即可。"
---

{{< alert >}}
以下部分内容可能已过期。
{{< /alert >}}

NotionNext是Tangly1024开源在[GitHub](https://github.com/tangly1024/NotionNext)的**博客生成器**。目的是帮助写作爱好者们通过Notion笔记免费、快速搭建独立站，从而专注于写作、不需要操心网站的维护。

只需要几分钟的时间，您就可以获得一个美观的博客界面👇：

![](https://cos.justgoidea.com/justgoidea/uPic/2022/07/17/62d3c59f117c1.png)

Tangly1024一直在对这个开源项目进行维护，从2021年下半年截至本篇发稿时已经至少维护了35个版本，可见作者的用心。

## NotionNext是什么

NotionNext将您的[Notion笔记](https://tangly1024.com/article/notion)渲染成静态博客、托管在[Vercel](https://tangly1024.com/article/vercel)云服务中。与[Hexo静态博客](https://tangly1024.com/article/vercel)相比较不同的是，NotionNext会自动同步您的笔记至博客站点，而无需每次写好文章都要推送到GitHub。

所有的博文和页面的编写及发布都只在您的Notion笔记中完成**。**[依托于Notion强大的编辑功能](https://tangly1024.com/article/notion)，您可以随时随地撰写文章、记录创意与灵感。

NotionNext是基于[craigary](https://github.com/craigary/nobelium)的[Nobelium项目](https://github.com/craigary/nobelium)二次开发，继承了[Nobelium功能特点](https://tangly1024.com/article/notion-nobelium-vercel)，例如快速秒开、设备全配适等。

## NotionNext的特色

**🚀 秒开，设备全适配**

- 快速的页面渲染和响应式设计
- 高效编译器的快速静态页面生成

**🤖 自动，无需重新部署**

- 部署在免费、高速的 Vercel 平台
- 支持增量式更新，更新文章后无需重复部署

**🚙 全功能，完全不操心**

- 评论、搜索、标签、分类
- 订阅、网站统计
- 本地化多语言
- 服务端渲染、优秀的SEO

**🎨 美观，轻松自定义**

- 丰富的配置项，更支持多语言
- 使用 Tailwind CSS，轻松实现二次开发

🙉 **更多的功能**

- 文章分类、标签、归档页面
- 首页大图、问候语
- [支持快速添加单页栏目](https://docs.tangly1024.com/zh/features/singlePage)
- [在Notion中换头像、换背景](https://nextjs-docs-notion-next-ep367chmr-tlyong1992.vercel.app/zh/features/personality)

👀 **阅读体验优化**

- 文章目录、字数统计、阅读时间统计
- 阅读量访客量展示
- 手动切换夜间模式

📶 **更好的SEO**

- 文章关联推荐
- 文章版权声明©️
- 网站 h1、h2 标题优化
- 自动生成 sitemap.xml

👭 **交互优化**

- [文章支持加锁](https://docs.tangly1024.com/zh/features/articleLock)🔏,[示例文章](https://preview.tangly1024.com/article/example-2)
- 文章分享💌
- [看板宠物](https://docs.tangly1024.com/zh/features/live2D)😾
- 支持 [waline](https://waline.js.org/guide/get-started.html)、[valine](https://valine.js.org/)、[giscus](https://giscus.app/zh-CN) 等 6 种评论插件

🎨 **支持多主题切换**

- [Next 主题](https://preview.tangly1024.com/?theme=next)

    ![](https://cos.justgoidea.com/justgoidea/uPic/2022/07/17/62d3c5ad16327.png)

- [Medium 主题](https://preview.tangly1024.com/?theme=medium)

    ![](https://cos.justgoidea.com/justgoidea/uPic/2022/07/17/62d3c5b4d4037.png)

- [Hexo 主题](https://preview.tangly1024.com/?theme=hexo)

    ![](https://cos.justgoidea.com/justgoidea/uPic/2022/07/17/62d3c5ba882bd.png)

- [Fukasawa 主题](https://preview.tangly1024.com/?theme=fukasawa)

    ![](https://cos.justgoidea.com/justgoidea/uPic/2022/07/17/62d3c5c3a4d27.png)

- [Example 主题](https://preview.tangly1024.com/?theme=example)

    ![](https://cos.justgoidea.com/justgoidea/uPic/2022/07/17/62d3c5c9cdc76.png)


## 开始部署

NotionNext的部署方式有很多，在这里我推荐通过Vercel一键部署的方式，简便易行。

### 前期准备

1. 注册 [GitHub](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home) 账号
2. 打开[这个 Notion 模板](https://www.notion.so/02ab3b8678004aa69e9e415905ef32a5?pvs=21)后点击页面右上方的 `Duplicate` 将这个页面拷贝到您的Notion中，并打开 `Share to web`。

    ![](https://cos.justgoidea.com/justgoidea/uPic/2022/07/16/62d291858c486.png)


### 快速部署

1. 点击[快速部署链接](https://vercel.com/new/clone?demo-description=Notion)
2. 选择用 `GitHub` 方式创建仓库，然后点击 `create` 确认部署。系统将自动部署完成，约 2 mins。

    ![](https://cos.justgoidea.com/justgoidea/uPic/2022/07/17/62d3c5d46e09f.png)

    ![](https://cos.justgoidea.com/justgoidea/uPic/2022/07/17/62d3c5dc7a34c.png)

    ![](https://cos.justgoidea.com/justgoidea/uPic/2022/07/17/62d3c5e228d46.png)

3. 进入到 `Vercel` 的 `notion-next` 项目中，选择 `Settings`，点击 `Enviroment Variables`，填入环境变量。`NAME` 中输入 `NOTION_PAGE_ID`，`VALUE` 中填写前期准备第二步中 Notion 页面分享链接中 `site/` 之后，`?` 之前的三十二位编码（e.g https://xxx.notion.site/80c301f9f7264a4aa5dfc1f8b9841222?v=37fe9de07b164c27a9cc3a7c5614a7c4）。输入完后点击 Add。
4. 进入到您的 `GitHub` 仓库，找到**您自己的** `NotionNext` 项目，打开 `blog.config.js`，按照文件中的注释开始编辑您的网站信息。

    <aside>
    ⚠️ 第5行，网站地址先使用您在准备工作第二步中的Notion页面地址

    </aside>

    <aside>
    ⚠️ 第20行，可以修改主题

    </aside>

    <aside>
    ⚠️ 第62-79行，需要到https://giscus.app/中设定，设定完成后把数值相应填写即可

    </aside>

5. 在Notion页面中更改您的页面标题、页面描述、页面图标，相对应的网站名称、网站描述、网站图标会自动修改。

## 自定义域名

1. 如果您还没有购买域名，推荐您到[腾讯云](https://cloud.tencent.com/act/cps/redirect?redirect=10010&cps_key=dd8807b176686762f8bfc44f59eba859)购买，如果您是第一次注册域名还可以享受新手福利。
2. 在腾讯云[DNSPod](https://console.dnspod.cn/)中为您的域名添加解析：
    1. 主机记录 `@`，记录类型 `A`，记录值 `76.76.21.21`
    2. 主机记录 `www`，记录类型 `CNAME`，记录值 `cname.vercel-dns.com`
3. 进入到 `Vercel` 中的 `notion-next` 项目，点击 `Setting`，选择 `Domains`，将您的域名输入后添加即可。
4. 进入到您的 `GitHub` 仓库，找到**您自己的** `NotionNext` 项目，打开 `blog.config.js`，将第 5 行的域名改为您自己的域名。

### 修改 Hexo 主题封面文字

进入到您的 `GitHub` 仓库，找到**您自己的** `NotionNext` 项目，在 `themes` 文件夹中打开 `config_hexo.js`，进行修改即可。
