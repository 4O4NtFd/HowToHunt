
## 1. 电子邮件退回问题 - Email Bounce Issues
- 检查应用程序是否具有邀请功能 - Check if Application has Invite Functionality

- 尝试向无效的电子邮件帐户发送邀请 - Try sending Invites to Invalid Email Accounts

- 尝试寻找电子邮件服务提供商，例如 AWS SES、Hubspot、Campaign Monitor  - Try to find Email Service Provider such as AWS SES , Hubspot , Campaign Monitor
  **Note:  You can find Email Service Provider by checking Email Headers**

  **注意：您可以通过检查电子邮件标题找到电子邮件服务提供商**
* 拥有电子邮件服务提供商后，请检查硬退回限制。 以下是其中一些的限制：
  
* Once you have the Email Service Provider, Check there Hard Bounce Limits. Here are the limits for some of them:
  
  **1. Hubspot Hard bounces:** HubSpot's hard bounce limit is 5%. For reference, many ISPs prefer bounce rates to be under 2%.
  
  **1.Hubspot硬退信：**HubSpot 的硬退信限制是 5%。 作为参考，许多 ISP 更喜欢退信率低于 2%。
  
  **2. AWS SES:** The rate of SES ranges from first 2-5% then 5-10%
  
  **2. AWS SES：** SES(Simple Email Service) 的比率范围从最初的 2-5% 到 5-10%

***Impact: Once the Hard Bounce Limits are reached, Email Service Provider will block the Company which means, No Emails would be sent to the Users !***

***影响：一旦达到硬退回限制，电子邮件服务提供商将阻止公司，这意味着不会向用户发送电子邮件！***

## 2. 长密码 DoS 攻击 - Long Password DoS Attack

- As the value of password is hashed and then stored in Databases. If there is no limit on the length of the Password, it can lead to consumption of resources for Hashing the Long Password.
- 由于密码的值被散列，然后存储在数据库中。 如果对密码的长度没有限制，可能会导致对长密码进行Hash 的资源消耗。

**如何测试？   How to test?**

- Use a Password of length around 150-200 words to check the presense of Length Restriction
- 使用长度在 150-200 字左右的密码来检查长度限制的存在
- If there is no Restriction, Choose a longer password and keep a eye on Response Time
- 如果没有限制，请选择更长的密码并注意响应时间
- Check if the Application Crashes for few seconds 
- 检查应用程序是否崩溃了几秒钟 

**在哪测试？   Where to test?**

- Registration Password Field is usually restricted but the Length of Password on the Forgot Password Page and the Change Password (As Authenticated User) Functionality is usually missing.
- 注册密码字段通常受到限制，但忘记密码页面上的密码长度和更改密码（作为经过身份验证的用户）功能通常会丢失。


## 3. 长字符串 DOS - Long String DOS

* When you set some string so long so server cannot process it anymore it cause DOS sometime
* 当你设置一些字符串太长以至于服务器无法处理它时，它会导致DOS有时

**如何测试  How to test**

```
Create app and put field like username or address or even profile picture name parameter ( second refrence ) like 1000 character of string . 
Search A's account from B's account either it will

创建应用程序并放置字段，如用户名或地址，甚至是个人资料图片名称参数（第二个参考），如 1000 个字符的字符串。
从 B 的帐户中搜索 A 的帐户
```
- Either it will keeping on searching for long time
- 要么会继续搜索很长时间
- Either the application will crash (500 - Error Code)
- 要么应用程序将崩溃（500 - 错误代码） 


## 使用 Password.txt 中的密码 - Use Password From Password.txt
⚠️`it's not recommended using more than 5000 characters as password.`

⚠️`不建议使用超过 5000 个字符作为密码。`

- Here is the [Password.txt](https://raw.githubusercontent.com/KathanP19/HowToHunt/master/Application_Level_DoS/Password.txt)

## 参考: 
\- Email Bounce Issues
* [https://medium.com/bugbountywriteup/an-unexpected-bounty-email-bounce-issues-b9f24a35eb68](https://medium.com/bugbountywriteup/an-unexpected-bounty-email-bounce-issues-b9f24a35eb68)

\- Long Password DoS Attack

- https://www.acunetix.com/vulnerabilities/web/long-password-denial-of-service/
- https://hackerone.com/reports/738569
- https://hackerone.com/reports/167351

\- Long String DOS
- [https://medium.com/@shahjerry33/long-string-dos-6ba8ceab3aa0](https://medium.com/@shahjerry33/long-string-dos-6ba8ceab3aa0)
- https://hackerone.com/reports/764434

## 作者: 
* [Keshav Malik](https://twitter.com/g0t_rOoT_)
* [Fani Malik](https://twitter.com/fanimalikhack)
