
<center>

[![GitHub issues](https://img.shields.io/github/issues/JunzhouLiu/BILIBILI-HELPER?style=flat-square)](https://github.com/JunzhouLiu/BILIBILI-HELPER/issues)

[![GitHub forks](https://img.shields.io/github/forks/JunzhouLiu/BILIBILI-HELPER?style=flat-square)](https://github.com/JunzhouLiu/BILIBILI-HELPER/network)

[![GitHub stars](https://img.shields.io/github/stars/JunzhouLiu/BILIBILI-HELPER?style=flat-square)](https://github.com/JunzhouLiu/BILIBILI-HELPER/stargazers)

[![GitHub license](https://img.shields.io/github/license/JunzhouLiu/BILIBILI-HELPER?style=flat-square)](https://github.com/JunzhouLiu/BILIBILI-HELPER/blob/main/LICENSE) 
</center>

# BILIBILI-HELPER
这是一个利用GitHub Action实现哔哩哔哩签到，简单配置便可自动获取每日65点经验的小工具，也可以部署到个人的服务器上，目前正在快速开发迭代中，快来和我一起成为Lv6吧~~~~。

# 功能列表
* [x] 每天上午10点30自动执行。 
* [x] 自动登录，获取登录经验5点 
* [x] 哔哩哔哩漫画每日自动签到 
* [x] 每日自动分享1个视频 5exp 
* [ ] 每日自动模拟观看1个视频 5exp 
* [x] 每日从热门视频中选取5个进行投币 50exp
* [x] 投币支持下次一定啦，可自定义每日投币数量。

[查看如何自定义每日投币数量](#jump1)

·····

# 开始使用
- fork本项目
- 点击项目 Seeting->Secrets->New Secrets 添加以下三个环境变量即可。

| Name       | Value              |
| ---------- | ------------------ |
| BILI_JCT   | 从浏览器缓存中获取 |
| DEDEUSERID | 从浏览器缓存中获取 |
| SESSDATA   | 从浏览器缓存中获取 |

[查看如何获取哔哩哔哩Cookies](#jump)

*如果收到了GitHub Action的错误邮件，请检查Cookies是不是失效了，用户在浏览器中主动退出B站账号，会导致`BILI_JCT`和`DEDEUSERID`失效*

![图示](docs/IMG/20201013210000.png)

## 查看运行日志 
*通过`DEBUG`标签快速过滤日志*  

![图示](docs/IMG/20201013134409.png)


## 如何获取Bilibili cookies

<span id="jump">如何获取Bilibili cookies</span>

1. 浏览器打开并登录[bilibili网站](https://www.bilibili.com/)
2. 按F12打开 “开发者工具” 找到应用程序/Application -> 存储-> Cookies
3. 找到`bili_jct`,`SESSDATA`,`DEDEUSERID`三项，并复制他们的值，创建GitHub Secrets。

![图示](docs/IMG/20201012001307.png)

## 自定义投币
**配置文件位于`src/main/resources/config.json`**
<span id="jump1">查看如何自定义每日投币数量</span>

参数示意
| Key           | Value | 说明                           |
| ------------- | ----- | ------------------------------ |
| numberOfCoins | 0到5  | 每日投币数量                   |
| select_like   | 1，0  | 1：投币时点赞，0：投币时不点赞 |

*投币数量如果随便写的话，可能会导致你破产。。。。*

# API参考列表

- [SocialSisterYi/bilibili-API-collect](https://github.com/SocialSisterYi/bilibili-API-collect)
- [happy888888/BiliExp](https://github.com/happy888888/BiliExp)
