---
title: "Cookie 的备份和有效期的修改"
date: 2022-09-10
slug: "2022-010"
draft: false
tags: ["tech"]
summary: "本文介绍了备份 Cookie 的重要性以及如何利用浏览器插件 EditThisCookie 进行 Cookie 的备份和有效期修改。通过备份 Cookie，可以在某些特殊情况下正常访问需要登录的网站。"
---

您是否也遇到过因为某些特殊原因无法正常打开正常网站（拒绝游客访问），或者登录被阻挡的情况？

这是因为网站被管理员进行了特殊的访问机制设置，如果我们没有网站的 Cookie，几乎是不可能在管理员解除访问限制之前访问网站的。

这也就体现出了定期对某些网站进行 Cookie 备份的重要性。

## Cookie 是什么？

Cookie 也就是我们常说的「饼干」，没错，就是我们吃的那个饼干，只是在网络中被用来指代网站为了辨别用户身份而存储在用户本地浏览器上的加密数据。

当我们通过浏览器打开某网站后，浏览器会访问该网站的服务器，服务器会自动传输一段数据给浏览器进行保存，之后每一次浏览器访问该网站的时候都必须带上这段数据。

所以，Cookie 有两个作用，一是识别用户的身份，二是记录访问历史。

比如，我们需要登录 A 网站，无论是用电脑端还是移动端，都要通过浏览器来进行。我们在浏览器中输入了登录 A 网站的账号密码，A 网站就会自动下发包括了 uid 和 expirationDate 等在内的加密数据到我们的浏览器上。只要我们不清除浏览记录，这段数据就会一直保存在我们的浏览器中。保存的这段数据就是 Cookie。

## 为什么要备份 Cookie？

如前所述，所谓的 Cookie 就相当于是管理员给我们发的一张带有有效期的通行证，之所以需要有效期，当然是出于安全需要。一旦过期了，我们就需要重新输入账号密码，等于是更换了一张新的通行证。

正常情况下，我们并不需要备份 Cookie，有效期过了重新登录一遍就行了。然而，某些网站因为其特殊性，网站页面或者登录页面会经常性不允许游客打开，可能是被某些 Authorities 阻断了，也可能是网站管理员主动阻断。这个时候，只要我们保留着有效期内的 Cookie，就还是可以正常访问网站的。

## 如何备份 Cookie？

说到这里，是不是您想问，怎么能保证 Cookie 一直在有效期内呢？

这就需要我们利用电脑端的浏览器插件 [EditThisCookie](https://chrome.google.com/webstore/detail/editthiscookie/fngmhnnpilhplaeedifhccceomclgfbg) 了。

在您的浏览器中（最好是 Chromium 内核的浏览器，如 Chrome，Edge，Vivaldi 等，不推荐国产 Chromium 内核的浏览器）下载 EditThisCookie 插件，安装好后，打开您需要备份 Cookie 的网站。这里我以 Google 为例。

打开 Google 并登录，然后点击 EditThisCookie 插件，就会看到这个界面

![](https://cos.justgoidea.com/justgoidea/uPic/2022/09/10/631c72b6cca3a.png)

我们往下拉，找到 Expiration，可以看到里面显示的是中国标准时间的 Cookie 过期日期。

![](https://cos.justgoidea.com/justgoidea/uPic/2022/09/10/631c73341fbcf.png)

我们只需要在输入框内修改日期后，按 ✅ 就完成了 Cookie 有效期的修改。（这里建议以1年为限，也就是直接把2022改成2023即可。）

之后我们点击输出按钮，更改好的 Cookie 就自动保存在我们的剪切板中，我们只需要在电脑中新建一个 txt 文档粘贴进去后保存即可。

![](https://cos.justgoidea.com/justgoidea/uPic/2022/09/10/631c7416b5b5e.png)

当下次遇到需要使用 Cookie 去打开网站的时候，将保存在 txt 文档中的内容粘贴到导入窗口后按 ✅ 即可。

![](https://cos.justgoidea.com/justgoidea/uPic/2022/09/10/631c74e329b65.png)

![](https://cos.justgoidea.com/justgoidea/uPic/2022/09/10/631c7507206c9.png)

之后刷新一下网站页面，就可以看到网站可以正常打开，并显示已登陆的状态了。
