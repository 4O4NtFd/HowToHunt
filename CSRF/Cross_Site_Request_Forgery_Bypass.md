**Cross Site Request Forgery跨站请求伪造(CSRF)**

Hello Guys, I Tried My Best To Share all The CSRF Bypasses I Know.
I Hope This Will Help You.
大家好，我尽力分享我知道的所有CSRF绕过方法。
我希望这能帮助你。

CSRF will be login, logout, reset pass, change password, add-cart, like, comment, profile change, user details change, balance transfer, subscription etc.
CSRF是指登录、注销、重设密码、更改密码、添加购物车、喜欢、评论、个人资料更改、用户详情更改、资金转移、订阅等。

```
-Change Request Method [POST => GET]
-改变请求方法 [POST => GET]

-Remove Total Token Parameter
-移除总的Token参数

-Remove The Token, And Give a Blank Parameter
-移除Token，并给出一个空白的参数

-Copy a Unused Valid Token , By Dropping The Request and Use That Token
-复制一个未使用的有效Token，通过放弃请求并使用该Token

-Use Own CSRF Token To Feed it to Victim
-使用自己的CSRF令Token，将其提供给受害者

-Replace Value With Of A Token of Same Length
-用相同长度的Token替换值 

-Reverse Engineer The Token
-反向设计Token

-Extract Token via HTML injection
-通过HTML注入提取Token

-Switch From Non-Form Content-Type: application/json or Content-Type: application/x-url-encoded To Content-Type: form-multipart
-从非表单的 "Content-Type: application/json"或 "Content-Type: application/x-url-encoded"切换到 "Content-Type: form-multipart"

-Change/delete the last or frist character from the token
-改变/删除令牌的最后一个或最开始的字符

-Change referrer to Referrer
-将referrer改为Referrer

-Bypass the regex
  If the site is looking for “bank.com” in the referer URL, maybe “bank.com.attacker.com” or “attacker.com/bank.com” will work.
-绕过正则表达式
  如果该站点在引用 URL 中查找“bank.com”，则“bank.com.attacker.com”或“attacker.com/bank.com”可能会起作用。

-Remove the referer header (add this <meta name=”referrer” content=”no-referrer”> in your payload or html code)
-删除引用标头（在您的pauload或 html 代码中添加此 <meta name=”referrer” content=”no-referrer”>）

-Clickjacking
-点击劫持

  (If you aren’t familiar with clickjacking attacks, more information can be found https://owasp.org/www-community/attacks/Clickjacking.)
  Exploiting clickjacking on the same endpoint bypasses all CSRF protection. Because technically, the request is indeed originating from the legitimate site. If the page where   the vulnerable endpoint is located on is vulnerable to clickjacking, all CSRF protection will be rendered irrelevant and you will be able to achieve the same results as a CSRF   attack on the endpoint, albeit with a bit more effort.
  (如果你不熟悉点击劫持攻击，更多的信息可以在https://owasp.org/www-community/attacks/Clickjacking）。
  在同一个端点上利用点击劫持，可以绕过所有CSRF保护。因为从技术上讲，该请求确实是来自合法网站。如果有漏洞的端点所在的页面容易被点击劫持，那么所有的CSRF保护都将变得无关紧要，你将能够达到与端点上的CSRF攻击相同的结果，尽管需要付出更多努力。
```

### 参考
[Medium Writeup](https://medium.com/swlh/intro-to-csrf-cross-site-request-forgery-9de669df03de)

[Medium Writeup](https://medium.com/swlh/attacking-sites-using-csrf-ba79b45b6efe)

[Medium Writeup](https://medium.com/swlh/bypassing-csrf-protection-c9b217175ee)


### 作者
* [@SMHTahsin33](https://twitter.com/SMHTahsin33)
* [@Virdoex_hunter](https://twitter.com/Virdoex_hunter)
* [@remonsec](https://twitter.com/remonsec)
* [@tamimhasan404](https://twitter.com/tamimhasan404)

