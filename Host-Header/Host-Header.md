# Summary For Host Header  主机头摘要
![https://pbs.twimg.com/media/ET39wJOWoAAfTBb?format=jpg&name=small](https://pbs.twimg.com/media/ET39wJOWoAAfTBb?format=jpg&name=small)

# Also Check This Things While Testing  测试时也要检查这些东西
1. Add two `HOST:` in Request.
    在请求中添加两个`HOST:`。
2. Try this Headers
    尝试这些headers
    
    ```      
       X-Original-Url:
       X-Forwarded-Server:
       X-Host:
       X-Forwarded-**Host**:
       X-Rewrite-Url:
    ```
3. If you come across `/api.json` in any AEM instance during bug hunting, try for web cache poisoning via following
    如果您在寻找错误期间在任何 AEM 实例中遇到 `/api.json`，请尝试通过以下方式进行 Web 缓存中毒
   `Host: , X-Forwarded-Server , X-Forwarded-Host:`
   and or simply try https://localhost/api.json HTTP/1.1
   或者干脆尝试 https://localhost/api.json HTTP/1.1
4. Also try  `也试试这个`  `Host: redacted.com.evil.com`
5. Try Host: evil.com/redacted.com
  尝试主机：evil.com/redacted.com

  [https://hackerone.com/reports/317476](https://hackerone.com/reports/317476)
6. Try this too `Host: example.com?.mavenlink.com`
    也试试这个`Host：example.com?.mavenlink.com`
7. Try `Host: javascript:alert(1);` Xss payload might result in debugging mode.  Xss payload可能会导致调试模式。
[https://blog.bentkowski.info/2015/04/xss-via-host-header-cse.html](https://blog.bentkowski.info/2015/04/xss-via-host-header-cse.html)
8. Host Header to Sqli  Sqli 的主机头
[https://blog.usejournal.com/bugbounty-database-hacked-of-indias-popular-sports-company-bypassing-host-header-to-sql-7b9af997c610](https://blog.usejournal.com/bugbounty-database-hacked-of-indias-popular-sports-company-bypassing-host-header-to-sql-7b9af997c610)
9. Bypass front server restrictions and access to forbidden files and directories through
   
   通过绕过前端服务器限制和访问被禁止的文件和目录
    `X-Rewrite-Url/X-original-url:` 
   `curl -i -s -k -X 'GET' -H 'Host: <site>' -H 'X-rewrite-url: admin/login' 'https://<site>/'.`


## Author:
* [@KathanP19](https://twitter.com/KathanP19)
