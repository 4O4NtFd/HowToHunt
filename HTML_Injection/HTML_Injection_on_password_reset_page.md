
## Summary
Password reset links are usually addressed to your account name followed by the reset link. Also if the application allows you to have your account name with tags and special characters then you should try this.
密码重置链接通常指向您的帐户名，然后是重置链接。 此外，如果应用程序允许您使用带有标签和特殊字符的帐户名称，那么您应该尝试这样做。

### Steps 步骤

1. Create your account
   创建用户
2. Edit your name to `<h1>attacker</h1>` or `"abc><h1>attacker</h1>` and save it.
   将您的姓名编辑为 `<h1>attacker</h1>` 或 `"abc><h1>attacker</h1>` 并保存。
3. Request for a reset password and check your email.
   请求重置密码并检查您的电子邮件。
4. You will notice the `<h1>` tag getting executed
   你会注意到 `<h1>` 标签被执行

* HTML injection are usually considered as low to medium severity bugs but you can escalate the severity by serving a malicious link by using `<a href>` for eg: `<h1>attacker</h1><a href="your-controlled-domain"Click here</a>`
HTML 注入通常被视为低到中等严重性错误，但您可以通过使用`<a href>`提供恶意链接来提升严重性，例如：`<h1>attacker</h1><a href="your-controlled -domain"Click here</a>`
* You can redirect the user to your malicious domain and serve a fake reset password page to steal credentials 
  Also you can serve a previously found XSS page and steal user cookies etc etc.. The creativity lies on you.您可以将用户重定向到您的恶意域并提供伪造的重置密码页面来窃取凭据
  您也可以提供先前发现的 XSS 页面并窃取用户 cookie 等。创意在于您。

## Author
[@C1pher15](https://twitter.com/C1pher15)
