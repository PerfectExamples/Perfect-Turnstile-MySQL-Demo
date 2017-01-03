# 使用 MySQL 的 Perfect Turnstile 认证层 [English](README.md)

<p align="center">
    <a href="http://perfect.org/get-involved.html" target="_blank">
        <img src="http://perfect.org/assets/github/perfect_github_2_0_0.jpg" alt="Get Involed with Perfect!" width="854" />
    </a>
</p>

<p align="center">
    <a href="https://github.com/PerfectlySoft/Perfect" target="_blank">
        <img src="http://www.perfect.org/github/Perfect_GH_button_1_Star.jpg" alt="Star Perfect On Github" />
    </a>  
    <a href="http://stackoverflow.com/questions/tagged/perfect" target="_blank">
        <img src="http://www.perfect.org/github/perfect_gh_button_2_SO.jpg" alt="Stack Overflow" />
    </a>  
    <a href="https://twitter.com/perfectlysoft" target="_blank">
        <img src="http://www.perfect.org/github/Perfect_GH_button_3_twit.jpg" alt="Follow Perfect on Twitter" />
    </a>  
    <a href="http://perfect.ly" target="_blank">
        <img src="http://www.perfect.org/github/Perfect_GH_button_4_slack.jpg" alt="Join the Perfect Slack" />
    </a>
</p>

<p align="center">
    <a href="https://developer.apple.com/swift/" target="_blank">
        <img src="https://img.shields.io/badge/Swift-3.0-orange.svg?style=flat" alt="Swift 3.0">
    </a>
    <a href="https://developer.apple.com/swift/" target="_blank">
        <img src="https://img.shields.io/badge/Platforms-OS%20X%20%7C%20Linux%20-lightgray.svg?style=flat" alt="Platforms OS X | Linux">
    </a>
    <a href="http://perfect.org/licensing.html" target="_blank">
        <img src="https://img.shields.io/badge/License-Apache-lightgrey.svg?style=flat" alt="License Apache">
    </a>
    <a href="http://twitter.com/PerfectlySoft" target="_blank">
        <img src="https://img.shields.io/badge/Twitter-@PerfectlySoft-blue.svg?style=flat" alt="PerfectlySoft Twitter">
    </a>
    <a href="http://perfect.ly" target="_blank">
        <img src="http://perfect.ly/badge.svg" alt="Slack Status">
    </a>
</p>

该示例程序展示了使用 MySQL ORM 时集成 Stormpath 开发的 Turnstile 认证系统。

该认证库可以在 [https://github.com/PerfectlySoft/Perfect-Turnstile-MySQL](https://github.com/PerfectlySoft/Perfect-Turnstile-MySQL) 找到。

该包作为 [Perfect](https://github.com/PerfectlySoft/Perfect) 项目的一部分，可以通过 Swift 包管理器进行编译。

编译前请确保安装了 Xcode 8.0 或以上版本。

## 编译事项

### macOS

使用 Homebrew 包管理器安装 MySQL。

```
brew install mysql
```

若未安装 Homebrew，请使用下面命令进行安装：

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

安装完 MySQL 后需要编辑 mysqlclient.pc 文件，该文件在下面的路径中：

```
/usr/local/lib/pkgconfig/mysqlclient.pc
```

移除该文件中的 "fno-omit-frame-pointer" 项。该文件默认是只读的，所以在编辑前请先对该文件的读写权限进行修改。

### Linux

确保您为 MySQL 5.6 或更高版本安装了 libmysqlclient-dev：

```
sudo apt-get install libmysqlclient-dev
```

注意：Ubuntu 14 默认安装了无法成功编译的 MySQL 客户端。请手动安装 MySQL 5.6 或更高版本。

## 设置 - Xcode 8

* 检出或下载该项目；
* 切换目录到项目根目录中并执行下面的命令

```
swift package generate-xcodeproj
```

* 打开 `PerfectTurnstile MySQL Demo.xcodeproj`

为了从 Xcode 中运行该项目，请编辑项目的 Scheme，"Options" 选择 "run"，选中 "Use custom working directory" 并选择该项目的工作目录。做完这些设置后，该项目就可以从 Xcode 中运行了。

## 设置 - 终端

* 检出或下载该项目；
* 切换目录到项目根目录中
* 执行 `swift build`
* 编译完成后，执行 `./.build/debug/PerfectTurnstile MySQL Demo`

```
[INFO] Starting HTTP server on 0.0.0.0:8181 with document root ./webroot
```

### JSON 路由

该框架包含了几个基本的路由：

```
POST /api/v1/login (with username & password form elements)
POST /api/v1/register (with username & password form elements)
GET /api/v1/logout
```

### 浏览器路由

下面的路由可用于浏览器测试：

```
http://localhost:8181
http://localhost:8181/login
http://localhost:8181/register
```

这些路由在 webroot 目录中使用了 Mustache 模板文件。