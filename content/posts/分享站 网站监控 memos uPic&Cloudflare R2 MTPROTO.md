---
title: "分享站/网站监控/memos/uPic&Cloudflare R2/MTPROTO"
date: 2023-05-19
slug: "2023-040"
draft: false
tags: ["tech"]
summary: "在 VPS 上部署 file gallery/站点监控/memos/MTPROTO；在 uPic 上配置 Cloudflare R2。"
---

这两天又折腾了一下 VPS，首先是把部分还留在腾讯云轻量上的站点和服务迁移到了 [10g.biz](https://10g.biz/index.php)。十分推荐这一家的 VPS，经过优化的线路，速度快且稳定。

## 一、File Photo Gallery

首先是做了一个[分享站](https://file.justgoidea.eu.org)，这样再写博客和 newsletter 的时候，有一些需要分享的内容（比如视频、文件）就可以直接放到这个分享站里了。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/rtB5hS.png)

这个分享站的部署非常简单，首先在宝塔面板上新建一个网站并设置好 DNS 解析和 SSL 证书，然后在 PHP 环境中安装 `fileinfo` 和 `exif` ，最后到网站的文件目录中上传一个从 [File Gallery 官网](https://www.files.gallery/) 下载的 `index.php` 文件就行了。

`index.php` 中的一些参数随时可以修改，列出了一些常用的供参考：

```markdown
// 根目录配置
    'root' => '',    // 相对路径或者绝对路径，不填代表当前目录，二级目录无需 / 符号
    'start_path' => false,    // 分配加载到视图中的第一个目录，默认情况下，该目录与root目录相同

// 授权登录
    'username' => '',    // 用户账号（留空关闭）
    'password' => '',    // 用户密码（留空关闭）

// 排除文件或者目录
    'files_exclude' => '',    // '/\.(png|jpe?g)$/i'   / 解释：排除后缀png.jpeg.jpg
    'dirs_exclude' => '',    // '/\/AAA|\/doc|\/222(\/|$)/i'    / 解释：排除目录AAA.doc.222

// 菜单
    'menu_enabled' => true    // 启用或禁用左侧文件夹菜单
    'menu_show' => true    // 文件夹菜单展开或折叠
    'menu_sort' => 'name_asc'    // 左侧文件夹菜单排序    / name_asc，name_desc，date_asc，date_desc

// 布局
    'layout' => 'rows'    // 主视图区域布局，包括选项 列表，块，网格，行和列
    'sort' => 'name_asc'    // 主视图区域默认排序    / name_asc，name_desc，date_asc，date_desc
```

## 二、Website Status

之后，我又在 GitHub 上看到了 [uptime-status](https://github.com/yb/uptime-status) 这个项目，可以监控部署的各个站点的运行情况。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/szGJtZ.png)

这个项目所调用的是 [UptimeRobot](https://uptimerobot.com/) 的 API，所以先要去这个网站上注册一下，免费版的用户可以添加 50 个网站进行监控，对于绝大多数人来说足够了。

**步骤一**：注册完成后点击 `+ Add New Monitor`，然后在 Monitor Type 选择 `HTTP(s)` 并填写网站名称和域名就行了。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/ZQViav.png)

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/h2etaM.png)

**步骤二**：添加完需要监控的网站后，将鼠标移动到用户邮箱处，选择 My Settings，然后找到 API Settings，在 Monitor-Specific API Keys 中选择 `Show/hide it`，之后在搜索栏中`输入`刚刚添加的网站名称来获取 API Key。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/0IGa0g.png)

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/oAcYBV.png)

**步骤三**：在宝塔面板中新建网站，并设置好 DNS 解析和 SSL 证书；然后到网站目录中上传并解压从 [uptime-status](https://github.com/yb/uptime-status) 下载的 `uptime-status.zip` 。

**步骤四**：修改 `config.js` 文件：

- `SiteName`：要显示的网站名称
- `ApiKeys`：在 ***步骤二*** 中获取的 API Key
- `CountDays`：要显示的日志天数，建议 60 或 90，显示效果比较好
- `ShowLink`：是否显示站点链接
- `Navi`：导航栏的菜单列表

## 三、Memos

Flomo 是一款非常好的 app，用过的都说好。然而，flomo 因为其不好进行输出和整理的缺点，一直不能融入我的工作流中。那为什么还要部署 memos 呢？

首先，我觉得有很多内容不一定要写在博客里，但又需要分享出来。

其次，之前是用的 Montaigne （详见：[利用 Montaigne 将备忘录变为博客](https://justgoidea.com/posts/2022-021)）直接在苹果的备忘录中写，可是最近发现我还分享了几个备忘录给泽泽和朋友，管理起来容易和 Montaigne 搞混。

于是，我就部署了一个高仿 flomo 的开源项目 [memos](https://github.com/usememos/memos)。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/6Xrlft.png)

相比于 flomo，我觉得 memos 的好处在除了开源和自托管外，也在 [iOS](https://memos.moe/) 和 [macOS](https://github.com/xudaolong/memos-desktop) 上有第三方开发的 app，另外还有许多有趣的玩法，除了比较老套的如[快捷指令](https://sharecuts.cn/shortcut/12640)和 [Raycast Extension](https://www.raycast.com/JakeYu/memos)，还可以部署成[静态展示站点](https://github.com/eallion/memos.top)和[静态图片站点](https://github.com/BarryYangi/MemosGallery)。

通过 Docker 部署十分方便。在 SSH 中连接服务器，然后输入代码：

```bash
docker run -d --name memos -p 5230:5230 -v ~/.memos/:/var/opt/memos ghcr.io/usememos/memos:latest
```

然后在宝塔上创建一个网站，到网站设置中设置反向代理 `http://127.0.0.1:5230 $host` 就可以了。

## 四、Cloudflare R2

今天我才注意到 Cloudflare 推出的对象存储 R2 已经可以设置公开访问，这也就意味着我可以将 memos 站点的数据存储在 R2，还可以在 uPic 上将 R2 设置为图床。

我一直在使用的是腾讯云 COS，对比起来似乎 R2 的价格优势并不大，但是和 AWS S3 比起来，R2 的价格优势就明显了，具体的对比可以看这篇[文章](https://www.vantage.sh/blog/cloudflare-r2-aws-s3-comparison)。

|  | Cloudflare R2 | 腾讯云 COS |
| --- | --- | --- |
| 标准存储费用 | 每月前 10GB 免费，超出后 $0.015/GB/月 | 每月前 10GB 免费，超出后按照不同存储类型和地域收费 |
| 请求费用 | 每月前1000万次免费，超出后 A 类操作 $4.50/百万次，B 类操作 $0.36/百万次 | 每月前1000万次免费，超出部分按照不同的请求类型和地域收费 |
| 下载流量费用 | 无 | 每月前10GB免费，超出部分按照不同的地域和流量类型收费 |
| 上传流量费用 | 无 | 每月前10GB免费，超出部分按照不同的地域和流量类型收费 |
| 资源包抵扣 | 无 | 有 |

虽然 R2 目前与腾讯云 COS 相比，价格优势并不明显，但每个月~~白嫖~~ 10GB 的免费额度，也不错啊。具体的开通过程和 R2 API 令牌的获取方式就不说了。

因为 R2 直接兼容 S3 所以在 uPic 可以直接在图床选项中增加 Amazon S3，然后选择自定义。服务端 URL 填写 R2 中格式为 `https://xxx.r2.cloudflarestorage.com/yourbucketname` 的 URL，可以在存储桶名称下方找到。空间名称就是存储桶的名称，Access Key 和 Secret Key 就是 R2 API 令牌中的`访问密钥 ID` 和`机密访问密钥`，域名就是自定义的存储桶域名。

![](https://cos.justgoidea.com/justgoidea/uPic/2023/06/04/rG2keC.png)

依次填写之后，点击`验证`，uPic 会自动上传一张图片，在 R2 中如果看到了图片文件，就表示配置成功，点击保存后就可以愉快地使用了。

## 五、MTPROTO

最近在 Tg 上需要关注一些信息，但手机又不想一直开着 Surge，干脆就在 VPS 上使用 Sunpma 大佬的[绿色一键脚本](https://github.com/sunpma/mtp)部署了 MTPROTO。

```bash
## 新建目录
mkdir /home/mtproxy && cd /home/mtproxy

## 开始安装
curl -s -o mtproxy.sh https://raw.githubusercontent.com/sunpma/mtp/master/mtproxy.sh && chmod +x mtproxy.sh && bash mtproxy.sh
```

```bash
## 运行服务
bash mtproxy.sh start

## 调试运行
bash mtproxy.sh debug

## 停止服务
bash mtproxy.sh stop

## 重启服务
bash mtproxy.sh restart

## 一键卸载
rm -rf /home/mtproxy
```

```bash
## 开机启动
chmod 755 /home/mtproxy/mtproxy.sh

vi /etc/crontab

## 加入下面这条命令后保存即可

@reboot root nohup bash /home/mtproxy/mtproxy.sh start > /dev/null 2>&1 &
```
