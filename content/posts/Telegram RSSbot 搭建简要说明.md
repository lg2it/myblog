---
title: "Telegram RSSbot 搭建简要说明"
date: 2023-08-24
slug: "2023-055"
draft: fasle
tags: ["tech"]
summary: "本文介绍了如何搭建 Telegram RSSbot，包括准备工作、新建机器人、获取基本信息、搭建机器人后端和订阅 RSS 等步骤。同时还介绍了如何搭建 MTPROTO 代理服务。"
---

![](https://cos.justgoidea.com/justgoidea/uPic/2023/08/24/8DUuBX.png)

之前我所有的 RSS 订阅都在 Inoreader，每次打开后都是几十几百条，让我不胜其烦。原本应该简约而不简单的 RSS 阅读体验不应该是这样。

于是今天抽空把我在 Telegram 上的 RSSbot 给更新了，将很多新闻类的订阅都转移到了 RSSbot 上。Inoreader 中保留的是高质量的，或者需要我花时间读的内容；RSSbot 上就只用接收那些即时性的新闻、天气预警、地震速报之类不需要我花太多时间的消息。

在更新之前，RSSBot 收到的消息是这样的：

![](https://cos.justgoidea.com/justgoidea/uPic/2023/08/24/cjY5do.jpg)

更新后，RSSbot 收到的消息就变成了这样：

![](https://cos.justgoidea.com/justgoidea/uPic/2023/08/24/z4MOZ8.jpg)

我可以直接在 Telegram 上看消息的正文了，不像之前还得点击链接，跳转到浏览器去看。太方便了，对不对？

搭建一个 RSSbot 非常简单，只需要简单的几步。

## 准备工作

在搭建 RSSbot 之前，首先需要准备一个 VPS。

然后安装好 Docker 和 Docker compose。

如果不知道该怎样安装，可以看[《用 RSShub 打造专属信息流》](https://www.justgoidea.com/2023-054#4534dce2e3e149c49ffcd3075938c7f2)中「用 Docker 部署 RSShub」的部分，有安装 Docker 的详细介绍。

接下来，有三个步骤来搭建机器人的后端，使用的是 [RSS-to-Telegram-Bot](https://github.com/Rongronggg9/RSS-to-Telegram-Bot/tree/dev) 这个开源项目。

## 步骤一：新建机器人

打开 Telegram，搜索 [@BotFather](https://t.me/BotFather)，然后发送 `/newbot`。

收到 `Alright, a new bot. How are we going to call it? Please choose a name for your bot.` 这条信息后，回复一个名称，作为机器人的名字，如 RSS2TG。

接下来，又会收到一条信息，`Good. Now let's choose a username for your bot. It must end in` bot`. Like this, for example: TetrisBot or tetris_bot.` 需要给机器人再添加一个以 `bot` 结尾的名字，如 RSS2TG_bot。

之后，就会收到一条很长的信息，其中会有一段红色的文字写的是`Use this token to access the HTTP API: 红色字符串 Keep your token secure and store it safely, it can be used by anyone to control your bot.`，是机器人的 API，把这个 API 记下来，步骤三会用到。

另外，这个 API 需要妥善保管，因为任何人只要有了这个 API，就能控制这个机器人。

## 步骤二：获取基本信息

在 Telegram 搜索 [@userinfobot](https://t.me/userinfobot)，然后点击 `start`，获取用户 ID 后记下来，步骤三会用到。

接着在浏览器上，通过 [Get telegraph API acess token](https://api.telegra.ph/createAccount?short_name=RSStT&author_name=Generated%20by%20RSStT&author_url=https%3A%2F%2Fgithub.com%2FRongronggg9%2FRSS-to-Telegram-Bot) 获取至少五个 token （每刷新一次网页会获得一个 token），将获取到的 token 都记录下来，下一步会用到。

## 步骤三：搭建机器人后端

首先，通过 SSH 登录到 VPS。

然后输入 `mkdir rsstt`，创建一个 rsstt 的目录。

接着输入 `cd rsstt` 打开 rsstt 目录。

再然后输入 `wget <https://raw.githubusercontent.com/Rongronggg9/RSS-to-Telegram-Bot/dev/docker-compose.yml.sample> -O docker-compose.yml`，获取 Docker compose 模板。

接下来输入 `vi docker-compose.yml`，进入到 Docker compose 的模板开始编辑环境变量。您会看到以下信息：

```yaml
# Please read <https://github.com/Rongronggg9/RSS-to-Telegram-Bot/blob/master/docs/deployment-guide.md> for more details.
version: '3.6'

services:
  main:
    image: rongronggg9/rss-to-telegram:dev  # stable image: rongronggg9/rss-to-telegram
    container_name: rsstt  # need to be unique
    restart: unless-stopped
    volumes:
      - ./config:/app/config
    environment:
      - TOKEN=1234567890:A1BCd2EF3gH45IJK6lMN7oPqr8ST9UvWX0Yz0  # get it from @BotFather
      - MANAGER=1234567890  # get it from @userinfobot

# ↓------ To disable sending via Telegraph, comment out this area ------↓ #
# Get Telegraph API access tokens: <https://api.telegra.ph/createAccount?short_name=RSStT&author_name=Generated%20by%20RSStT&author_url=https%3A%2F%2Fgithub.com%2FRongronggg9%2FRSS-to-Telegram-Bot>
# Refresh the page every time you get a new token.
# If you have a lot of subscriptions, make sure to get at least 5 tokens.
#                            ↓ Replace with your access tokens ↓
      - TELEGRAPH_TOKEN=
        1a23b456c78de90f1a23b456c78de90f1a23b456c78de90f1a23b456c78d
        1a23b456c78de90f1a23b456c78de90f1a23b456c78de90f1a23b456c78d
        1a23b456c78de90f1a23b456c78de90f1a23b456c78de90f1a23b456c78d
        1a23b456c78de90f1a23b456c78de90f1a23b456c78de90f1a23b456c78d
        1a23b456c78de90f1a23b456c78de90f1a23b456c78de90f1a23b456c78d
# ↑------ To disable sending via Telegraph, comment out this area ------↑ #

# Please read <https://github.com/Rongronggg9/RSS-to-Telegram-Bot/blob/master/docs/advanced-settings.md> for more details.
# ↓------ Advanced settings ------↓ #
      #- MULTIUSER=0  # default: 1
      #- CRON_SECOND=30  # 0-59, default: 0
      #- DATABASE_URL=postgres://username:password@host:port/db_name  # default: sqlite://path/to/config/db.sqlite3
      #- API_ID=1025907  # get it from <https://core.telegram.org/api/obtaining_api_id>
      #- API_HASH=452b0359b988148995f22ff0f4229750  # get it from <https://core.telegram.org/api/obtaining_api_id>
      #- IMG_RELAY_SERVER=https://wsrv.nl/?url=  # default: <https://rsstt-img-relay.rongrong.workers.dev/>
      #- IMAGES_WESERV_NL=https://t0.nl/  # default: <https://wsrv.nl/>
      #- USER_AGENT=Mozilla/5.0 (Android 12; Mobile; rv:68.0) Gecko/68.0 Firefox/96.0  # default: RSStT/2.2 RSS Reader
      #- IPV6_PRIOR=1  # default: 0
      #- T_PROXY=socks5://172.17.0.1:1080  # Proxy used to connect to the Telegram API
      #- R_PROXY=socks5://172.17.0.1:1080  # Proxy used to fetch feeds
      #- PROXY_BYPASS_PRIVATE=1  # default: 0
      #- PROXY_BYPASS_DOMAINS=example.com;example.net
      #- HTTP_TIMEOUT=30  # default: 12
      #- HTTP_CONCURRENCY=0  # default: 1024
      #- HTTP_CONCURRENCY_PER_HOST=0  # default: 16
      #- TABLE_TO_IMAGE=1  # default: 0
      #- TRAFFIC_SAVING=1  # default: 0
      #- LAZY_MEDIA_VALIDATION=1  # default: 0
      #- MANAGER_PRIVILEGED=1  # default: 0
      #- NO_UVLOOP=1  # default: 0
      #- MULTIPROCESSING=1  # default: 0
      #- DEBUG=1  # debug logging, default: 0
# ↑------ Advanced settings ------↑ #

```

输入 `i` 进入到编辑器的编辑模式，找到 `TOKEN=1234567890:A1BCd2EF3gH45IJK6lMN7oPqr8ST9UvWX0Yz0  # get it from @BotFather`，删除`1234567890:A1BCd2EF3gH45IJK6lMN7oPqr8ST9UvWX0Yz0` 后，将步骤一中获取的机器人 API 粘贴进去。

再找到 `MANAGER=1234567890  # get it from @userinfobot`，删除 `1234567890` 后，将步骤二中获取到的用户 ID 粘贴进去。

再将 `TELEGRAPH_TOKEN` 后面的五条 token 都删除，将步骤二中获取的 token 一条条粘贴进去。

```
- TELEGRAPH_TOKEN=
  1a23b456c78de90f1a23b456c78de90f1a23b456c78de90f1a23b456c78d #替换成步骤二中获取的 token
  1a23b456c78de90f1a23b456c78de90f1a23b456c78de90f1a23b456c78d #替换成步骤二中获取的 token
  1a23b456c78de90f1a23b456c78de90f1a23b456c78de90f1a23b456c78d #替换成步骤二中获取的 token
  1a23b456c78de90f1a23b456c78de90f1a23b456c78de90f1a23b456c78d #替换成步骤二中获取的 token
  1a23b456c78de90f1a23b456c78de90f1a23b456c78de90f1a23b456c78d #替换成步骤二中获取的 token

```

接下来，按 `esc` 键，退出编辑模式，输入 `：wq` 保存修改。

最后输入 `docker-compose up -d`，机器人的后端就搭建好了。

## 在机器人上订阅 RSS

此时，在 Telegram 上打开在步骤一中建好的机器人，会看到输入框前会有一个三天横线的蓝色按钮，点击它就能看到各种指令。

- **/sub**: 添加订阅
- **/unsub**: 退订订阅
- **/unsub_all**: 退订所有订阅
- **/list**: 列出订阅列表
- **/set**: 自定义订阅设置
- **/set_default**: 自定义默认设置
- **/import**: 从 OPML 导入订阅
- **/export**: 导出订阅到 OPML
- **/activate_subs**: 启用订阅
- **/deactivate_subs**: 停用订阅
- **/version**: 查看 bot 版本
- **/help**: 查看帮助
- **/lang**: 选择语言
- **/test**: 测试 (仅 bot 管理员)
- **/set_option**: 更改 bot 配置 (仅 bot 管理员)
- **/user_info**: 查看/修改用户信息 (仅 bot 管理员)

订阅 RSS 时，就是向机器人发送 `/sub <RSS 地址>` 的指令。

当所有的订阅源输入完成后，再发送 `/activate_subs` 来启动所有订阅。

之后，当订阅的 RSS 更新后，就可以在机器人上收到了。

## 拓展：搭建 MTPROTO

MTPROTO 是 Telegram 的代理服务，在`设置-数据和存储-使用代理`中可以找到。

使用了 MTPROTO 之后，不需要开代理软件（如 shadowroeket，clash）也可以正常使用 Telegram，也就是 Telegram 可以 24 小时在线了。

部署的过程非常简单，在 VPS 上直接使用 Sunpma 大佬的[绿色一键脚本](https://github.com/sunpma/mtp)部署就行。

首先，输入 `mkdir /home/mtproxy && cd /home/mtproxy` 新建一个目录。

然后输入 `curl -s -o mtproxy.sh <https://raw.githubusercontent.com/sunpma/mtp/master/mtproxy.sh> && chmod +x mtproxy.sh && bash mtproxy.sh`，根据提示安装脚本。

接着输入 `bash mtproxy.sh start` 运行脚本。

把返回的信息在 Telegram 上设置好就可以了。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/08/24/brexYy.png)

---

我在 Telegram 上新建了一个与博客同名的频道 [`槿呈Goidea`](https://t.me/justgoidea)，期待您的关注。
