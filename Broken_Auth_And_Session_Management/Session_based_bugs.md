# 损坏的身份验证和会话管理<br>Broken Authentication And Session Management.

### 密码更改后旧会话不会过期<br>Old Session Does Not Expire After Password Change:
* 步骤:
```
      1.create An account On Your Target Site
        在目标网站创建账户
        
      2.Login Into Two Browser With Same Account(Chrome, FireFox.You Can Use Incognito Mode As well) 
        使用同一个帐户登录两个浏览器（Chrome、FireFox。您也可以使用隐身模式）
        
      3.Change You Password In Chrome, On Seccessfull Password Change Referesh Your Logged in Account In FireFox/Incognito Mode.
      在 Chrome 中更改密码，成功更改密码后刷新您在 FireFox/隐身模式下的登录帐户。
      
      4.If you'r still logged in Then This Is a Bug
      如果您仍然登录，那么这是一个Bug
```

### 会话劫持（预期行为）<br>Session Hijacking (Intended Behavior)
* 步骤:
```
    1.Create your account
      创建账户
      
    2.Login your account
      登录账户
    
    3.Use cookie editor extension in browser
      在浏览器中使用 cookie 编辑器扩展
    
    4.Copy all the target cookies
      复制所有目标 cookie
    
    5.Logout your account
      登出您的帐户
      
    6.Paste that cookies in cookie editor extension
      将该 cookie 粘贴到 cookie 编辑器扩展中
      
    7.Refresh page if you are logged in then this is a session hijacking
      如果您已登录，请刷新页面，这就是会话劫持
```
`Impact:` If attacker get cookies of victim it will leads to account takeover.

`影响：` 如果攻击者获得受害者的 cookie，它将导致帐户接管。


### 密码重置令牌不会过期(不安全的可配置性)<br>Password reset token does not expire (Insecure Configurability)
* 步骤:
```
      1.Create your account on target Site.
        在目标网站创建账户
        
      2.request for a forget password token.
        请求忘记密码令牌。
        
      3.Don't use that link
        不要使用那个链接
      
      4.Instead logged in with your old password and change your email to other.
        而是使用您的旧密码登录并将您的电子邮件更改为其他
        
      5.Now use that password link sents to old email and check if you are able to change your password if yes than there is the litle bug.
        现在使用发送到旧电子邮件的密码链接，并检查您是否可以更改密码，如果是的话，那是不是有一个小错误。
```

 ### 服务器安全配置错误 -> 缺少安全标头 -> 安全页面的缓存控制<br>Server security misconfiguration -> Lack of security headers -> Cache control for a security page
 * 步骤:
 ``` 
     1.Login to the application
       登录应用程序
     
     2.Navigate around the pages
        浏览页面
     3.Logout
       登出
     
     4.Press (Alt+left-arrow) buttons
       按Alt + ←
       
     5.If you are logged in or can view the pages navigated by the user. Then you found a bug.
     如果您已登录或可以查看用户浏览的页面。 然后你发现了一个错误。
 ```
  `Impact:` At a PC cafe, if a person was in a very important page with alot of details and logged out, then another person comes and clicks back (because he didnt close the browser) then data is exposed. User information leaked

`影响：` 在网吧，如果一个人在一个非常重要的页面，有很多细节并退出，然后另一个人回来点击（因为他没有关闭浏览器）然后数据被暴露。 用户信息泄露

 ### 对电子邮件验证绕过的破坏身份验证(P4) ：<br>Broken Authentication To Email Verification Bypass (P4) :
  `category` : P4 >> Broken Authentication and Session Management >> Failure to Invalidate Session >> On Password Reset and/or Change

`类别`：P4 >> 损坏的身份验证和会话管理 >> 使会话无效 >> 关于密码重置和/或更改

* 重现步骤：
``` 
    1.First You need to make a account & You will receive a Email verification link.
      首先您需要创建一个帐户，您将收到一个电子邮件验证链接。 
      
    2.Application in my case give less Privileges & Features to access if not verified.
      在我的情况下，如果未验证，应用程序将提供较少的访问权限和功能。
      
    3.Logged into the Application & I change the email Address to Email B.
      登录应用程序，我将电子邮件地址更改为电子邮件 B。
      
    4.A Verification Link was Send & I verified that.
      已发送验证链接，我对此进行了验证。
    
    5.Now I again Changed the email back to Email I have entered at the time of account creation.
      现在我再次将电子邮件改回创建帐户时输入的电子邮件。
    
    6.It showed me that my Email is Verified.
      它显示我的电子邮件已验证。
      
    7.Hence , A Succesful Email verfication Bypassed as I haven't Verified the Link which was sent to me in the time of account creation still my email got verified.
      因此，绕过了成功的电子邮件验证，因为我还没有验证在创建帐户时发送给我的链接，但我的电子邮件仍然得到了验证。
      
    8.idn't Receive any code again for verification when I changed back my email & When I open the account it showed in my Profile that its Verified Email.
    当我改回我的电子邮件时，我没有再次收到任何验证代码，当我打开帐户时，它在我的个人资料中显示其已验证的电子邮件。
```

`Impact` :
Email Verfication was bypassed due to Broken Authentication Mechanism , Thus more Privileged account can be accessed by an attacker making website prone to Future Attacks.    
  Happy Hacking:)

`影响`：

由于身份验证机制损坏，电子邮件验证被绕过，因此攻击者可以访问更多特权帐户，从而使网站容易受到未来攻击。  Happy Hacking:)

  ### 电子邮件验证绕过<br>Email Verification Bypass (P3/P4)
  * 步骤:
   ``` 
    1.First You need to Create an account with Your Own Email Address.
      首先，您需要使用您自己的电子邮件地址创建一个帐户。
      
    2.After Creating An Account A Verification Link will be sent to your account.
      创建帐户后，验证链接将发送到您的帐户。
      
    3.Dont Use The Email Verification link. Change Your Email to Victim's Email.
      不要使用电子邮件验证链接。 将您的电子邮件更改为受害者的电子邮件。
      
    4.Now Go in Your Email and Click on Your Own Email Verification Link.
      现在进入您的电子邮件并单击您自己的电子邮件验证链接。
      
    5.if the Victim's Email Get Verified then This is a Bug.
      如果受害者的电子邮件得到验证，那么这是一个错误。
   ```
`Impact` : Email Verfication Bypass

`影响`：email验证绕过

 ### 旧密码重置令牌在请求新密码时不会过期（有时为 P4）：<br>Old Password Reset Token Not Expiring Upon Requesting New One (Sometimes P4) :
  * 步骤:
 ``` 
    1.First You need to Create an account with a Valid Email Address.
      首先，您需要使用有效的电子邮件地址创建一个帐户。
    
    2.After Creating An Account log out from your Account and Navigate on Forgot Password Page.
      创建帐户后，从您的帐户注销并导航到忘记密码页面。
      
    3.Request a Password Reset Link for your Account.A Verification Link will be sent to your account.
      为您的帐户申请密码重置链接。验证链接将发送到您的帐户。
      
    4.Without Using this Password Reset Link Request A New Password Reset Link.
      不使用此密码重置链接请求新的密码重置链接。
    5.Now go in Your email and Use 1st Password Reset Link Rather than Using 2nd One And Change Your Password.
      现在进入您的电子邮件并使用第一个密码重置链接而不是使用第二个并更改您的密码。
    6.If You Are Able to Change Your Password Than This Is a tiny Bug ;).
      如果您能够更改密码，那么这是一个小错误。
 ```
* Note:- Some Companies Won't Accept it As Valid Issue. 
* 注意:-一些公司不会接受它作为有效问题。

### 密码更改后密码重置令牌未过期：<br>Password Reset Token Not Expiring After Password Change (P4):
  * 步骤:
 ``` 
    1.First You need to Create an account with a Valid Email Address.
      首先，您需要使用有效的电子邮件地址创建一个帐户。
      
    2.After Creating An Account log out from your Account and Navigate on Forgot Password Page.
      创建帐户后，从您的帐户注销并导航到忘记密码页面。
    3.Request a Password Reset Link for your Account.
      为您的帐户请求密码重置链接。
      
    4.Use The Password Reset Link And Change The Password, After Changing the Password Login to Your Account.
      使用密码重置链接并更改密码，更改密码后登录到您的帐户。
      
    5.Now Use The Old Password Reset Link To Change The Password Again.
      现在使用旧密码重置链接再次更改密码。
      
    6.If You Are Able to Change Your Password Again Than This Is a tiny Bug  ;).
      如果您能够再次更改密码，那么这是一个小错误。
 ```

* Thanks For Reading Guys Happy Hunting :).

  ## Resources:
  Google,Youtube.

## Authors
* [https://twitter.com/Virdoex_hunter](https://twitter.com/Virdoex_hunter) 
* Linkedin : [@chirag_Agrawal](https://www.linkedin.com/in/chirag-agrawal-770488144/), Twitter  : [@Raiders](https://twitter.com/ChiragA15977205)
* Twitter : [Fani Malik](https://twitter.com/fanimalikhack) 
