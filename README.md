# ValidEmail
一个用于检测目标邮箱地址是否存在的Python程序，基于Ubuntu和Python 3.6.4开发。

## 原理说明
1. 通过nslookup检查目标邮箱域名的MX记录；
2. 与MX记录的服务器地址、端口建立连接，并通过SMTP扩展协议的ehlo命令建立连接；
3. 通过mail FROM:<''>设置发送地址为空；
4. 通过rcpt TO:<'email address'>探测服务器对邮箱地址的反馈信息，如返回代码是250则表示邮箱存在，如是550则表示邮箱不存在，个别邮件服务商用其他返回代码。

## 功能描述
只有一个功能，检测邮箱地址是否真实存在，存在则返回True，不存在则返回False。

## 应用场景
* 批量群发邮件时，事先通过该程序过滤有效邮箱地址；
* 在一些特殊情况下，结合字典对目标域名的邮箱进行猜测；

## 特别说明
* 该程序修改自Python的[validate_email](https://pypi.org/project/validate_email/)模块，并进行了优化、简化；
* 由于DNS模块的需要，该程序仅能运行于Linux环境。