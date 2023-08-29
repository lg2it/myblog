---
title: "用 RSSHub 打造专属信息流"
date: 2023-08-14
slug: "2023-054"
draft: false
tags: ["tech"]
summary: "本文介绍了如何使用RSSHub打造自己的信息流。可以通过Zeabur、Vercel或Docker部署RSSHub，然后使用已经制作好的路由订阅各种信息源，如新闻、社交、视频、购物、娱乐等。同时，本文还提供了一个理想化的RSS信息流列表和两篇外链文章，供读者参考。"
---

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/5uJoIm.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/5uJoIm.png)

针对 GFW 的限制，大量网站在中国大陆无法正常访问。这导致许多用户必须使用代理工具上网。然而，如果您某些时候无法方便地使用这些工具，那么如何获取和阅览 GFW 屏蔽的网站内容呢？RSSHub 提供了一种优雅的解决方案。

RSSHub 是由 [DIYgod](https://twitter.com/DIYgod) 领导的开源项目，它能将各种网站内容转换为 RSS 格式，覆盖面广泛，包括新闻网站、社交媒体平台、电商网站等等。通过 RSSHub，用户可以利用 RSS 阅读器获取各大网站的最新更新，无需直接访问这些网站，实现了高效便捷的网络信息接收。

随着 Serverless 技术的发展，部署 RSSHub 已经变得十分简单，仅官网就提供了十种方式。接下来，我从易到难向您介绍通过 Zeabur 部署、通过 Vercel 部署和通过 Docker 部署等三种方式。

## 准备阶段

因为 RSSHub 是托管在 GitHub 上的开源项目，所以无论使用哪种方式，都需要您在部署之前拥有一个 Github 账号。

首先，用浏览器打开 [GitHub 官网](https://github.com/)（如果打不开页面，请先开代理工具后刷新重试），然后点击屏幕右上角的 `Sign UP` 进行注册。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/ienEwp.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/ienEwp.png)

接下来依次输入您的邮箱地址（email）、密码（password）、用户名（username），是否订阅产品信息（填 `y` 表示订阅，填 `n` 表示不订阅）等。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/pWvPR4.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/pWvPR4.png)

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/K8BBTE.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/K8BBTE.png)

接下来点击 `Verify` 进行真人验证（如下图所示，将右侧的照片调整为左图指向的方向），防止通过机器人恶意注册的账号。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/81rgbs.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/81rgbs.png)

完成上述步骤后，就完成了账号的注册步骤。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/o8xSUa.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/o8xSUa.png)

然后，您需要在您的邮箱中找到验证码进行邮箱验证。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/qKeOXD.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/qKeOXD.png)

邮箱验证通过后，就表示您已经完成了注册。不过，您还需要告诉 GitHub 一些信息来制定收费方案，比如您是个人使用还是团队使用，您是不是学生或老师。根据您的真实状况选择即可。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/3cGZNY.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/3cGZNY.png)

之后就来到了收费方案的页面，在这里选择免费方案即可。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/3tsLqF.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/3tsLqF.png)

至此，您的 GitHub 账号就注册完毕了。

## 通过 Zeabur 部署 RSSHub

[Zeabur](https://zeabur.com/zh-CN) 是由国人开发者开发的一个可以帮助您部署服务的平台，无论您使用什么编程语言或开发框架，都只需要通过几个简单的按钮进行部署。

用来部署 RSSHub 时，使用 Zeabur 的免费方案即可。

首先，在 Zeabur 的[登录页面](https://dash.zeabur.com/login)使用 Github 账号进行免密登录。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/dTCZU3.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/dTCZU3.png)

登录后，在屏幕的右上角会有一个红色的标记着 7 天的提醒，点击之后，可以看到如下页面：

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/F5LooB.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/F5LooB.png)

点击 `绑定付款方式` 之后，页面会自动跳转到付款信息的页面。您可以绑定信用卡，也可以选择 `没有信用卡`，然后绑定支付宝。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/UybBsb.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/UybBsb.png)

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/ATlJzz.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/ATlJzz.png)

接下来就是点击[部署到 Zeabur](https://dash.zeabur.com/templates/X46PTP)，您的浏览器会自动跳转到 Zeabur 的部署页面，点击 Deploy 即可部署。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/cZltTJ.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/cZltTJ.png)

部署成功后，您会看到如图所示的页面，表示您的 RSSHub 项目已经部署在 Zeabur。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/e8n8aV.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/e8n8aV.png)

点击项目，进入管理页面后，选择域名。如果您有域名，可以点击`自定义` 添加您自己的域名，然后到您使用的 DNS 服务商处修改 DNS；如果您没有域名，就点击 `生成域名`，Zeabur 将自动生成一个域名给您的项目。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/FhJo7h.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/FhJo7h.png)

无论用哪种域名方式，您都可以在浏览器的新标签页打开域名，如果显示以下页面，就意味着您成功部署了 RSSHub。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/LwBsTI.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/LwBsTI.png)

请注意：个人正常使用 RSSHub 基本不会产生费用，请不要泄露您部署的域名，以免造成滥用而给您带来经济损失。

## 通过 Vercel 一键部署 RSSHub

Vercel 的部署方式和 Zeabur 大同小异，区别在于您可以不必填写任何付款信息即可正常使用；部署方式分为没有自动更新的一键部署和有自动更新的手动部署两种方式。

没有自动更新的一键部署方式基本和 Zeabur 相同，使用 GitHub 账号免密登录 Vercel 后，点击[一键部署](https://vercel.com/import/project?template=https://github.com/DIYgod/RSSHub)，跳转到部署页面。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/yRMXMr.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/yRMXMr.png)

等待约 1 分钟左右，部署完成后，您会看到这个页面，点击 `Continue to Dashboard` 跳转到后台管理页面。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/JwbFtk.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/JwbFtk.png)

在后台管理页面，您可以看到 Vercel 已经自动为您生成了一个网址，点击这个网站如果显示的是 RSSHub 的页面，就证明已经成功部署。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/9gCx8l.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/9gCx8l.png)

如果您想使用自定义域名，可以在项目的设置中添加。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/viHm9t.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/viHm9t.png)

## 手动部署 RSSHub 到 Vercel （推荐）

虽然没有自动更新的一键部署很方便，但由于 RSSHub 的项目代码经常更新，无法自动更新就可能导致使用时遇到一些 bug 或错误。

手动将 RSSHub 部署到 Vercel 也并不麻烦，部署完成后只需要每隔一段时间在 GitHub 中将 RSSHub 的代码同步一下，Vercel 就会自动重新部署，基本不需要您操心。

首先，打开 RSSHub 在 GitHub 中的[代码仓库](https://github.com/DIYgod/RSSHub)。

然后先点击 `Starred` 收藏这个代码仓库，再点击 `Fork` 创建代码分支到您的账号中。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/z4aIgi.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/z4aIgi.png)

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/2XvhCs.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/2XvhCs.png)

之后，您就会在您自己的账号中看到已经 Fork 的代码。

然后在 GitHub 中安装 [Pull](https://github.com/apps/pull) 应用，点击 `install`，就可自动安装。这个应用会帮助您定期自动更新代码。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/O9UbDV.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/O9UbDV.png)

接着，打开 Vercel，选择 `Add New`，然后选择 `Project`。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/7BvYLP.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/7BvYLP.png)

选择您刚刚 Fork 过的 RSSHub 代码，选择 `import`。剩下的步骤就和之前一键部署时一样了。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/vrZm5G.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/vrZm5G.png)

## 通过 Docker 部署 RSSHub

<aside>
⚠️ 如果没有看到代码，请刷新浏览器。

</aside>

通过 Docker 部署 RSSHub 则意味着您需要有一台 VPS，或者常年开机的电脑。这里，我以安装 Ubuntu 系统的 VPS 为例。

注意：由于需要进行备案，所以不建议使用在中国大陆的 VPS，如果您在阿里云、腾讯云选购云服务器或轻量应用服务器时，请选择香港或国外的。

首先是通过 SSH 登录到您的 VPS：

```bash
ssh username@VPS_IP
```

然后更新包列表：

```bash
sudo apt-get update
```

接下来是安装一些必需的包，以让APT能够通过HTTPS下载：

```bash
sudo apt-get install \\
    apt-transport-https \\
    ca-certificates \\
    curl \\
    gnupg \\
    lsb-release
```

添加Docker的官方GPG密钥：

```bash
curl -fsSL <https://download.docker.com/linux/ubuntu/gpg> | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

设置稳定的仓库：

```bash
echo \\
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] <https://download.docker.com/linux/ubuntu> \\
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

更新apt包索引，并安装最新版本的 Docker Engine 和 containerd：

```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

验证 Docker 是否安装成功：

```bash
sudo docker run hello-world
```

下面开始安装 RSSHub，先是运行命令在 VPS 上拉取 RSSHub 的 Docker 镜像：

```bash
docker pull diygod/rsshub
```

然后，运行 RSSHub：

```bash
docker run -d --name rsshub -p 1200:1200 diygod/rsshub
```

此时，您就可以在标签页打开 `http://VPS_IP:1200` ，如果显示 RSSHub 页面则表示部署成功。

![https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/9gCx8l.png](https://hhzz-1300713987.cos.na-siliconvalley.myqcloud.com/2023/08/14/9gCx8l.png)

接着，您可以设置反向代理，为其添加域名。

先是安装 Nginx：

```bash
sudo apt-get update
sudo apt-get install nginx
```

然后是创建一个新的Nginx配置文件。例如，如果您的域名是 `yourdomain.com`，您可以创建一个名为 `yourdomain.com` 的文件：

```bash
sudo nano /etc/nginx/sites-available/yourdomain.com
```

在这个文件中添加以下内容：

```bash
server {
    listen 80;
    server_name yourdomain.com;

    location / {
        proxy_pass <http://localhost:1200>;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}

请将`yourdomain.com`替换为您的域名。
```

保存并关闭文件后，创建一个符号链接到 sites-enabled 目录来启用这个网站：

```bash
sudo ln -s /etc/nginx/sites-available/yourdomain.com /etc/nginx/sites-enabled/
```

测试 Nginx 配置文件是否有语法错误：

```bash
sudo nginx -t

如果没有错误，您将看到类似于`nginx: configuration file /etc/nginx/nginx.conf test is successful`的消息。
```

重新加载Nginx以应用新的配置：

```bash
sudo systemctl reload nginx
```

现在，RSSHub 的 Docker 服务就可以通过您的域名访问了。不过，此时您的网站并没有添加 SSL 证书，不能使用 https 的网址链接。如何添加 SSL 证书就留待您自己探索了（RSSHub 的服务不使用 https 也没事儿）。

## 如何使用 RSSHub

在 RSSHub 的[官方文档](https://docs.rsshub.app/social-media.html)中，已经提供了众多已经制作好的路由，您只需要根据说明填写参数即可。

以通过 RSSHub 订阅的新加坡联合早报为例，来说明 RSSHub 的路由参数构成。

使用 RSSHub 抓取联合早报新闻内容的 RSS 地址为 `https://rsshub.app/zaobao/znews/china`。

其中，`https://rsshub.app` 对应着您的 RSSHub 地址，也就是上文的部署教程中提到的你自己添加的域名或者 Vercel/Zeabur 自动生成的域名。

而 `/zaobao/znews/` 是路由，也就是需要抓取这个网站的主体内容是什么，在这里是要抓取新闻。

那么要抓取什么新闻呢？`china` 这个参数表示抓取中国的新闻。其他的参数还包括了 `singapore` 对应着新加坡的新闻，`sea` 对应着东南亚的新闻，`world` 对应着全球新闻，`sports` 对应着体育新闻。

好了，现在已知我的 RSSHub 地址为 `https://rssh-ub-test-three.vercel.app`，如果我想让 RSSHub 帮我抓取联合早报的体育新闻，应该怎样写订阅地址呢？那就是写成  `https://rssh-ub-test-three.vercel.app/zaobao/znews/sports`。

如果我希望订阅 Elon Mask 的 Twitter 时间线，每当 Elon Mask 发了新的推文，我都可以在 RSS 阅读器中看到。这个订阅地址就是 `https://rssh-ub-test-three.vercel.app/twitter/user/elonmusk`。

如果我只想看 Elon Mask 的原创推文和转推，不想看他在时间线上回复的内容，此时就要添加参数，把订阅地址写成 `https://rssh-ub-test-three.vercel.app/twitter/user/elonmusk/excludeReplies=1`。

## 用 RSSHub 建立信息流列表

通过 RSSHub，您能够方便快捷地构建属于自己的定制化 RSS 信息流。

RSSHub 支持订阅包括新闻网站、Twitter、YouTube 频道、Telegram 频道、B站 UP主、微博、小红书在内的多种信息源，甚至包括天气预警、地震速报、软件更新提醒、大麦网票务更新和麦当劳活动资讯等实用信息。无论是新闻、视频，还是日常生活中的衣、食、住、行，用 RSSHub 生成的订阅地址可帮助您在 RSS 阅读器中便捷地获取全面信息。利用 RSSHub，您可以一站式接收各类最新资讯，让信息获取更高效。

那么，我们可以设想一个理想化的 RSS 信息流列表，绝大多数的订阅地址由 RSSHub 生成，它是这样的：

- 📰 新闻
    - 中国新闻
    - 国际新闻
    - 其他的新闻类细分

- ⚠️ 预警
    - 天气
    - 地震

- 🌐 社交
    - Twitter
    - 微博
    - 即刻
    - Telegram Channel

- 📖 阅读
    - 博客
    - 其他的阅读类细分

- 🎥 视频
    - YouTube
    - Bilibili

- 🛒 购物
    - 京东
    - 什么值得买
    - 小红书
    - 大麦网
    - 麦当劳
    - 多抓鱼

- 🎮 娱乐
    - 直播
    - 短视频
    - 图片
    - 游戏

- 🖥️ 软件更新

## 阅读推荐

- [Geek](https://twitter.com/geekbb)有一篇[《618 RSSHub 订阅《什么值得买》榜单分享》](https://geekbb.xlog.app/618_RSSHub)，在文中他介绍了如何通过 RSSHub 随时更新各种购物清单，历史低点和优惠券活动。
- DIYgod 的[《我有特别的 RSS 使用技巧》](https://diygod.cc/ohmyrss)则介绍了怎样充分挖掘 RSS 的价值。

---

您还可以在 Telegram 的[频道](https://t.me/justgoidea)找到我