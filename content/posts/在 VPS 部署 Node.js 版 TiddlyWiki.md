---
title: "在 VPS 部署 Node.js 版 TiddlyWiki"
date: 2023-10-14
slug: "2023-060"
draft: false
tags:
  - "tech"
summary: "通过宝塔面板快速部署 TiddlyWiki"
---
![feature](https://cos.justgoidea.com/justgoidea/uPic/2023/10/14/DALL-E%20Digital%20Workspace.png)

部署 Node.js 版 TiddlyWiki 并不复杂。不过在部署之前，需要完成一些准备工作。

## 准备工作

1. 准备一台 VPS，并安装[宝塔面板](https://www.bt.cn/new/index.html)。
2. 在 VPS 上安装 PM2。
3. 准备一个域名。

## 步骤一：安装 TiddlyWiki

完成准备工作后，就可以着手在 VPS 上安装 TiddlyWiki 了。

首先，通过 SSH 登录到 VPS；

然后输入 `sudo npm install -g tiddlywiki`，进行全局安装。

## 步骤二：创建网站

打开 VPS 上的宝塔面板后台，点击宝塔面板左侧的「网站」，新建一个网站，输入您的域名（该域名以后用来访问 TiddlyWiki），其他的配置如下：

![img](https://cos.justgoidea.com/justgoidea/uPic/2023/10/14/CleanShot%202023-10-14%20at%2012.21.23@2x.png)

## 步骤三：部署 TiddlyWiki 服务

首先，在 SSH 中输入 `cd /www/wwwroot/您的域名` 。

然后输入 `tiddlywiki mywiki –init server`。

这样，就在 `/www/wwwroot/您的域名` 中新建了一个 `mywiki` 文件夹，并部署了 TiddlyWiki。

## 步骤四：配置 PM2 管理器

首先，在 SSH 中输入 `cd/www/wwwroot/您的域名/mywiki`；

然后输入 `pm2 start "tiddlywiki --server"`；

此时，可以输入 `pm2 list` 查看 TiddlyWiki 服务器是否已经正常运行；

接着再依次输入 `pm2 startup` 和 `pm2 save`。

## 步骤五：配置防火墙和反向代理

首先，在宝塔面板的安全中放行 `8080` 端口。

![img](https://cos.justgoidea.com/justgoidea/uPic/2023/10/14/CleanShot%202023-10-14%20at%2012.46.52@2x.png)

然后，在网站的设置中配置反向代理。

![img](https://cos.justgoidea.com/justgoidea/uPic/2023/10/14/CleanShot%202023-10-14%20at%2012.48.44@2x.png)

此外，还需要配置域名证书。

## 更安全的访问

此时，就已经可以通过域名打开您的 TiddlyWiki，开始记笔记了。

但是这时所有人都能够通过域名打开您的 TiddlyWiki，并不安全。

想要更安全的部署，有两种方式，第一种方式是只能自己打开 TiddlyWiki；第二种方式是所有人都能打开，但只有自己可以编辑。

### 方式一

其他的部署步骤不变，仅对 `步骤四：配置 PM2 管理器` 进行修改。

首先，在 SSH 中输入 `cd/www/wwwroot/您的域名/mywiki`；

然后输入 `pm2 start tiddlywiki --name "mywiki" -- --listen host=127.0.0.1 port=8080 username=username password=password`；

此时，可以输入 `pm2 list` 查看 TiddlyWiki 服务器是否已经正常运行；

接着再依次输入 `pm2 startup` 和 `pm2 save`。

这样就只能通过输入用户名和密码访问您的 TiddlyWiki 了，提高了安全性。

### 方式二

打开宝塔面板，在网站的根目录（`/www/wwwroot/您的域名`）中新建一个文件并命名为 `start-wiki.sh`，然后在文件中输入以下内容：

```
 #!/bin/bash
 tiddlywiki /www/wwwroot/您的域名/mywiki/ --listen host=127.0.0.1 port=8080 "readers=(anon)" writers=your_username username=your_username password=your_password
```

这里的 `your_username` 和 `your_password` 都需要修改为您自己的用户名和密码。

接下来，其他的步骤保持不变，仅对`步骤四：配置 PM2 管理器`进行修改。

首先，在 SSH 中输入 `chmod +x /www/wwwroot/您的域名/start-wiki.sh`，为 `start-wiki.sh`添加执行权限。

然后输入 `pm2 start /www/wwwroot/您的域名/start-wiki.sh --name "tiddlywiki"`

此时，可以输入 `pm2 list` 查看 TiddlyWiki 服务器是否已经正常运行；

接着再依次输入 `pm2 startup` 和 `pm2 save`。

这样，之后就可以通过 `https://您的域名/login-basic`，使用管理员的身份使用 TiddlyWiki，同时其他访客也可以正常访问而不能修改您的笔记内容和配置。
