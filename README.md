<h1 align="center">💥 I'm Boom 💥</h1>
<p>
  <img src="https://img.shields.io/github/release/Fly-Playgroud/Boom.svg" />
  <img src="https://img.shields.io/github/release-date/Fly-Playgroud/Boom.svg?color=blue&label=update" />
  <img src="https://img.shields.io/badge/go report-A+-brightgreen.svg" />
</p>



## 👑 Boom 简介

**Boom** 是一款基于无头浏览器的 Web 弱口令爆破工具。它具有以下特性：

- 自动识别网页是否是登录页面
- 自动识别爆破目标类型：表单/传统认证协议类型(Basic/Digest/NTLM)
- 自动识别登录相关组件并填充点击
- 自动判别登录成功与否
- 支持 URL 批量并发爆破
- 支持单 URL 并发爆破
- 多种爆破模式：**密码优先**和**用户名优先**

- [ ] WebHook 消息推送
- [ ] 支持验证码组件识别



## ✨ Demo

![BoomDemo](./images/BoomDemo.gif)



## 🚀 快速使用

**在使用之前，请务必阅读并同意 [License](https://github.com/Fly-Playgroud/Boom/blob/master/LICENSE.md) 文件中的条款，否则请勿安装使用本工具。**

1. 单个URL爆破：

   ```bash
   Boom -t https://www.example.com/login.html --us users.txt --ps ./passwords.txt
   ```

    - `-t` ：指定单个爆破目标
    - `--us` ：指定用户名字典
    - `--ps`：指定密码字典

   > 注意：在未显示使用 `-m` 参数时将使用默认爆破模式——**密码优先**

2. URL 批量爆破

   ```bash
   Boom --ts targets.txt --us users.txt --ps passwords.txt
   ```

    - `--ts` ：指定爆破目标的字典
    - `--us` ：指定用户名字典
    - `--ps`：指定密码字典


3. 爆破结果存储

   爆破结果存储有两种格式：

   - `--to` ：--text-ouput 的缩写，以文本格式输出到指定的文件中
   - `--jo` ：--json-output 的缩写，以 JSON 结构化数据存储到指定 JSON 文件中

   ```bash
   Boom --ts targets.txt --us users.txt --ps passwords.txt --to ./res.txt
   ```

   > `--jo` 和 `--to` 是文件 publisher 的快捷方式而已，通过配置文件配置 File Publisher 也是可以的



## 📒 配置文件介绍

```yaml
# Version: 0.3

max_boom_concurrent: 2                                                  # 最大同时爆破的目标个数
boom_target_path: "" 							# 爆破目标字典路径
browser_config:								# 浏览器配置
    browser_model: local					        # 浏览器模式
    chrome_bin_path: ""							# 浏览器可执行文件所在路径
    chrome_temp_dir: ./chrome_temp					# 浏览器临时文件存储目录
    disable_headless: false						# 禁用无头模式
    disable_images: true						# 禁用图片
    leak_less: true							# 实验性参数：防止内存泄露
    no_sandbox: true						        # 是否使用沙盒：Linux 以 root 用户运行的情况下设置为 true 
    proxy: ""							        # 浏览器代理
    running_chrome:							# 正在运行的浏览器：如果启用， Boom 将会接管正在使用的浏览器
        enable: false
        ip: ""
        port: 0
    user_agent: ""							# 浏览器 UA
logger_config:								# 日志配置
    logger_level: "info"					        # 默认日志等级	
    logger_time_format: 2006/01/02 15:04:05	                        # 日志输出时间格式
    logger_file_name: ./log/boom.log				        # 日志文件存储路径
    logger_output_level: []						# 输出到文件中的日志等级
    logger_file_max_size: 50					        # 日志文件最大体积：单位 MB
    logger_file_max_backups: 5						# 日志文件最大备份个数：单位 个
    logger_file_max_age: 30						# 日志文件最大存储时长：单位 天
    logger_prefix: ""							# 日志前缀
global_boom_config:							# 全局爆破配置
    boomConCurrent: 2							# 单个爆破目标的爆破并发数
    clientMaxTimeout: 5                                                 # 客户端最大超时时间
    boomModel: 2							# 爆破模式：1.用户名优先--用户名跑字典，密码固定；2.密码优先--密码跑字典，用户名固定
    boomTarget: ""							# 爆破的目标
    userNamePath: ""							# 用户名字典路径
    passwordPath: ""							# 密码字典路径
publish_config:                                                         # publisher_config/webhook config
   file:                                                                # 文件 publisher
      enable: true                                                      # 是否开启文件存储
      format: text                                                      # 结果存储格式：text/json
      filePath: ./res.txt                                               # 存储文件路径：.txt/.json
```

## 🏩 学习交流
扫描添加作者QQ，拉你进群
备注：**Boom**
![qr](./images/qr.jpg)

