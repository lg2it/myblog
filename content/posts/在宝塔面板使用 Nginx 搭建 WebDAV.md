---
title: "在宝塔面板使用 Nginx 搭建 WebDAV"
date: 2023-04-28
slug: "2023-029"
draft: false
tags: ["tech"]
summary: "在 VPS 上搭建 WebDAV，为 DEVONthink 打造多端同步。"
---

{{< alert >}}
以下部分内容可能已过期。
{{< /alert >}}

最近 Dropbox 快到期了，面对高昂的续费价格，我流下了贫穷的泪水😭。

但是如果不续费，iCloud 又经常性抽风，DEVONthink 的同步就成为了问题。

看了一眼我在腾讯云仅存的一个轻量应用服务器，还是 70GB 的空间，那为什么不搭建一个 WebDAV 服务把空间利用起来呢？

说干就干💪

## 确认模块

因为 WebDAV 是基于 Nginx 搭建的，需要 `http_dav_module` 模块支持。

可以在 SSH 中使用 `nginx -V` 命令查询是否有安装 `http_dav_module` 模块。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/oJy6Rg.png)

如果没有看到 `http_dav_module` 模块，就需要卸载 Nginx 后重新选择编译安装并添加自定义模块。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/hwYfW9.png)

按照下面的内容填写自定义模块：

- 模块名称：`http_dav_module`
- 模块描述：`webdev`
- 模块参数：`-with-http_dav_module --add-module=/root/nginx-dav-ext-module`
- 前置脚本：`git clone https://github.com/arut/nginx-dav-ext-module.git /root/nginx-dav-ext-module`

填写完后点击提交，等待编译安装完成后用`nginx -V`命令查看模块是否已经成功安装。

## 搭建

在宝塔面板新建一个网站， `PHP 版本` 选择`纯静态`即可。

然后在网站目录中开启密码访问，设置好自己的账户及密码。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/ohv1oE.png)

最后前往网站设置选择配置文件，在最后面 `}` 符号之前粘贴以下设置代码：

```php
location / {
root     /www/wwwroot/xxx; # WebDAV目录路径(请自行修改)
client_max_body_size 102400M; # 大文件支持参数
charset utf-8; # 编码参数（不设定可能导致中文乱码）
autoindex on;
dav_methods PUT DELETE MKCOL COPY MOVE;
# 需要 nginx-dav-ext-module 才有下面的选项
dav_ext_methods PROPFIND OPTIONS LOCK UNLOCK;
create_full_put_path  on;
}
```

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/Bsf9yU.png)

修改完成后保存即可。

然后前往网站目录删除 `index.html` 文件。

至此 WebDAV 就搭建完毕了。

## 效果展示

在 DEVONthink 中设置了 WebDAV 同步。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/uZGnSk.png)

在浏览器中打开搭建好的 WebDAV 网站。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/V5W4y2.png)
