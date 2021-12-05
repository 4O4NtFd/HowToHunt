# HTTP Desync or Request Smuggling:  <br>HTTP 不同步或请求走私：
- Basics:
  "HTTP request smuggling is a technique for interfering with the way a web site processes sequences of HTTP requests that are received from one or more users. Request smuggling vulnerabilities are often critical in nature, allowing an attacker to bypass security controls, gain unauthorized access to sensitive data, and directly compromise other application users. " -Portswigger  
  “HTTP 请求走私是一种干扰网站处理从一个或多个用户收到的 HTTP 请求序列的方式的技术。请求走私漏洞本质上通常很关键，允许攻击者绕过安全控制，获得未经授权的访问 敏感数据，并直接危害其他应用程序用户。” -Portswigger


 ## Where ?:  

 - Any Endpoint might be Vulnerable to HTTP Desync attack.  
   任何端点都可能容易受到 HTTP Desync 攻击。

 - You can Find the Vulnerability on Non-endpoints as well, But impact is always much higher on Sensitive Endpoints ;)
   您也可以在非端点上找到漏洞，但对敏感端点的影响总是要高得多；)
---
 ### Step 1:  

 * Go To Repeater tab, and try various Timing based payloads to confirm the bug. More Explanation here:  
   转到Repeater选项卡，并尝试各种Timing based payloads以确认错误。 更多解释在这里：

[Finding the Vulnerability](https://portswigger.net/web-security/request-smuggling/finding)

### Step 2:  

* Once you have successfully discovered the bug, you can chain it with various bugs eg. Account Takeover by stealing session IDs, Cross side Scripting Attacks in User-Agent Header,etc. More Description here:  
  一旦你成功地发现了这个错误，你就可以将它与各种错误链接起来，例如。 通过窃取会话 ID 进行帐户接管、用户代理标头中的跨端脚本攻击等。 更多描述在这里：

[Exploiting the Vulnerability](https://portswigger.net/web-security/request-smuggling/exploiting)  

---
## Tools:  

1. [defparam`s_smuggler.py](https://github.com/defparam/smuggler)  

`Usage:`  
* Smuggler.py :

    `cat alive_urls.txt | python3 smuggler.py -m GET/POST #either GET or POST ` 
    
    OR
    
    ` python3 smuggler.py -u https://example.com -m GET/POST  `
    
2. [Burp_smuggler](https://github.com/PortSwigger/http-request-smuggler) (also available in BApp store)  

## More Info:  

### Topics  

https://paper.seebug.org/1049/ (Recommended !)  

[Portswigger Topic](https://portswigger.net/research/http-desync-attacks-request-smuggling-reborn)  

[Portswigger Lab](https://portswigger.net/web-security/request-smuggling)  

### Reports (Hackerone):  

[Report 1](https://hackerone.com/reports/737140)  

[Report 2](https://hackerone.com/reports/867952)  

[Report 3](https://hackerone.com/reports/498052)  

[Report 4](https://hackerone.com/reports/526880)

[Report 5](https://hackerone.com/reports/771666)  

[Report 6](https://hackerone.com/reports/753939)  

[Report 7](https://hackerone.com/reports/648434 )  

[Report 8](https://hackerone.com/reports/740037)  

## Writeups (Medium.com):  

[Article 1](https://medium.com/@ricardoiramar/the-powerful-http-request-smuggling-af208fafa142)  

[Article 2](https://medium.com/cyberverse/http-request-smuggling-in-plain-english-7080e48df8b4)  

[Article 3](https://medium.com/@cc1h2e1/write-up-of-two-http-requests-smuggling-ff211656fe7d)  

[Article 4](https://medium.com/bugbountywriteup/crossing-the-borders-the-illegal-trade-of-http-requests-57da188520ca)  

## Extra:  

[A Brief Video About Req. Smuggling](https://youtu.be/gzM4wWA7RFo)

### Author:
[Neutron__](https://twitter.com/Neutron__)

###### If you think something was missed, feel free to add/modify/delete it :)
