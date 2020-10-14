<h1 align="center">
BILIBILI-HELPER
</h1>

<div align="center"> 

[![GitHub issues](https://img.shields.io/github/issues/JunzhouLiu/BILIBILI-HELPER?style=flat-square)](https://github.com/JunzhouLiu/BILIBILI-HELPER/issues)
[![GitHub forks](https://img.shields.io/github/forks/JunzhouLiu/BILIBILI-HELPER?style=flat-square)](https://github.com/JunzhouLiu/BILIBILI-HELPER/network)
[![GitHub stars](https://img.shields.io/github/stars/JunzhouLiu/BILIBILI-HELPER?style=flat-square)](https://github.com/JunzhouLiu/BILIBILI-HELPER/stargazers)
[![GitHub license](https://img.shields.io/github/license/JunzhouLiu/BILIBILI-HELPER?style=flat-square)](https://github.com/JunzhouLiu/BILIBILI-HELPER/blob/main/LICENSE) 
 
</div>

# 目录
- [目录](#目录)
- [工具简介](#工具简介)
- [功能列表](#功能列表)
- [开始使用](#开始使用)
  - [使用前准备](#使用前准备)
  - [查看运行日志](#查看运行日志)
  - [<span id="jump">如何获取Bilibili cookies</span>](#如何获取bilibili-cookies)
  - [<span id="jump1">自定义投币</span>](#自定义投币)
- [快速更新](#快速更新)
  - [关于项目更新频率](#关于项目更新频率)
  - [快速拉取最新代码](#快速拉取最新代码)
- [API参考列表](#api参考列表)
[查看如何自定义每日投币数量](#jump1)

# 工具简介 

这是一个利用GitHub Action实现哔哩哔哩签到，简单配置便可自动获取每日65点经验的小工具，也可以部署到个人的服务器上，目前正在快速开发迭代中，快来和我一起成为Lv6吧~~~~。


# 功能列表
* [x] 每天上午10点30自动执行。 
* [x] 自动登录，获取登录经验5点 
* [x] 哔哩哔哩漫画每日自动签到 
* [x] 每日自动分享1个视频 5exp 
* [x] 每日自动从热门视频中随机观看1个视频 5exp  ps:观看视频会产生观看记录
* [x] 每日从热门视频中选取5个进行投币 50exp
* [x] 投币支持下次一定啦，可自定义每日投币数量。

·····

# 开始使用
## 使用前准备
1. **fork本项目，功能正在逐步增加中，要是能顺手点个Star就更好了**
2. **手动开GitHub Action服务**
   
Github Actions默认处于禁止状态，请手动开启Actions. 之后每天10点半会运行一次。
![图示](docs/IMG/openActions.png)

1. **点击项目 Seeting->Secrets->New Secrets 添加以下三个环境变量。** 
 
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


## <span id="jump">如何获取Bilibili cookies</span>

1. 浏览器打开并登录[bilibili网站](https://www.bilibili.com/)
2. 按F12打开 “开发者工具” 找到应用程序/Application -> 存储-> Cookies
3. 找到`bili_jct`,`SESSDATA`,`DEDEUSERID`三项，并复制他们的值，创建GitHub Secrets。

![图示](docs/IMG/20201012001307.png)

## <span id="jump1">自定义投币</span>

**配置文件位于`src/main/resources/config.json`**

参数示意
| Key           | Value | 说明                           |
| ------------- | ----- | ------------------------------ |
| numberOfCoins | 0到5  | 每日投币数量                   |
| select_like   | 1，0  | 1：投币时点赞，0：投币时不点赞 |
| watch_share   | 1，0  | 1：观看时分享，0：观看不分享   |

*投币数量如果随便写的话，可能会导致你破产。。。。（代码做了处理，投币最多5个）*


# 快速更新

## 关于项目更新频率
目前处于快速迭代阶段，建议通过以下方式从本仓库拉取最新代码。

## 快速拉取最新代码

0. 通过`git remote -v`查看是否有源头仓库的别名和地址。

例如这里origin就是你自己的仓库，upstream是你fork的源头仓库。
```bash
$ git remote -v
origin  https://github.com/JunzhouLiu/cxmooc-tools.git (fetch)
origin  https://github.com/JunzhouLiu/cxmooc-tools.git (push)
upstream        https://github.com/CodFrm/cxmooc-tools.git (fetch)
upstream        https://github.com/CodFrm/cxmooc-tools.git (push)

```

1. fork仓库后，将你的仓库拉到本地，如果没有源头仓库，则添加源头仓库
```bash
git remote add upstream https://github.com/JunzhouLiu/BILIBILI-HELPER.git
```

2. 更新上游仓库main分支的代码（pull操作实际上是 `fetch+merge`）

```bash
git pull upstream main
```

3. 将从源头仓库更新后的代码推送到你自己的github仓库

```bash
git push origin main 
```
4. 这样你就能快速的从我的仓库拉取最新的代码，并更新到你自己的仓库里了。自定义配置的同学，要注意`config.json` 不要被我的文件覆盖了。 


# API参考列表

- [SocialSisterYi/bilibili-API-collect](https://github.com/SocialSisterYi/bilibili-API-collect)
- [happy888888/BiliExp](https://github.com/happy888888/BiliExp)
