---
title: "利用 Notion 搭建个人站点"
date: 2022-07-16
slug: "2022-004"
draft: false
tags: ["tech"]
summary: "本文介绍了如何使用Cloudflare的Web Workers为Notion的公开页面进行域名的自定义，从而实现利用Notion搭建个人站点。"
---

All-In-One笔记类软件`Notion`不只有强大的database，我们还可以将一个页面设置为公开显示，也就是可以将页面链接分享给任何人浏览，哪怕他们并没有注册或者登录`Notion`。

不过，目前`Notion`官方还并没有支持公开页面的自定义域名功能。所以，我们可以用「曲线救国」的方法为`Notion的公开页面`进行域名的自定义。通过简单的12个步骤，就可以使用[Cloudflare](https://www.cloudflare.com/zh-cn/)的`Web Workers`为`Notion`的`HTTP`请求进行手动改写，让我们实现利用Notion搭建个人站点。

## 准备工作

1. 注册一个域名，这里我推荐使用[腾讯云](https://cloud.tencent.com/act/cps/redirect?redirect=10010&cps_key=dd8807b176686762f8bfc44f59eba859)，如果您是第一次注册域名还可以享受新手福利。
2. 注册一个[Cloudflare](https://www.cloudflare.com/zh-cn/)的账号，Cloudflare有中文版，点击网页右上角的🌐图标即可选择语言。
3. 在Notion上选择一个页面（Page）点击右上方的Share，选择Share to Web。

## Cloudflare设置

1. 登录Cloudflare后，我们进入了仪表盘页面，在输入框内输入您的域名后点击蓝色按钮`添加站点`就可以了。
2. 之后进入到选择计划页面，选择0美元的计划即可。
3. 接下来是配置DNS解析，到[腾讯云域名注册控制台](https://console.cloud.tencent.com/domain/)，进入我的域名页面，然后选择管理。
4. 之后选择修改DNS。
5. 在弹出的页面中选择自定义DNS，将Cloudflare给的两个DNS地址分别填进去。
6. DNS修改需要等几分钟，几分钟后Cloudflare会发一份邮件给你，通知已经成功，或者你回Cloudflare的仪表盘页面刷新一下。
    
    之后，我们就点击左侧边栏的`Workers`，进入概述。
    
7. 然后点击创建服务。
    
    <aside>
    ⚠️ 这里需要选择HTTP路由器
    
    </aside>
    
8. 在浏览器新建一个标签页，进入到 [fruitionsite](https://fruitionsite.com/)，直接到页面的中部，找到 Step 2 填写完后，点击`COPY THE CODE`。
9. 回到cloudflare，点击`快速编辑`
10. 将里面的代码都给删除，把刚刚从 [fruitionsite](https://fruitionsite.com/) 复制过来的代码给粘贴进去后点击`保存并部署`即可。
11. 之后回到Works，点击`添加路由`，在输入框填入`您的域名/*`，在选择框选择`您的域名`。
12. 在浏览器中输入您的域名，如果显示您的Notion页面，则大功告成！