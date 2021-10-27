# 双因素认证绕过技术 - 2FA Bypass Techniques

`2FA=2 Factor Authentication`

### [思维导图](https://mm.tt/1736437018?t=SEeZOmvt01)

指数？ - Index | 技术- Technique 
--- | ---
**1** | 响应操作 - Response Manipulation
**2** | 状态代码操作 - Status Code Manipulation 
**3** | 2FA代码泄漏响应 - 2FA Code Leakage in Response 
**4** | JS文件分析 - JS File Analysis 
**5** | 2FA代码重用 - 2FA Code Reusability 
**6** | 缺乏爆破保护 - Lack of Brute-Force Protection 
**7** | 缺少2FA代码完整性验证 - Missing 2FA Code Integrity Validation 
**8** | CSRF在2FA禁用时 - CSRF on 2FA Disabling 
**9** | 密码重置禁用2FA - Password Reset Disable 2FA 
**10** | 备份代码滥用 - Backup Code Abuse 
**11** | 在2FA禁用页面上点击劫持 - Clickjacking on 2FA Disabling Page 
**12** | 启用2FA不会过期以前的活动会话 - Enabling 2FA doesn't expire Previously active Sessions 
**13** | 用null或者000000绕过2FA - Bypass 2FA with null or 000000 
___
#### 响应操作 - Response Manipulation
```
In response if "success":false
Change it to "success":true

在响应中如果"success":false
将它改为"success":true
```

#### 状态代码操作 - Status Code Manipulation

```
If Status Code is 4xx
Try to change it to 200 OK and see if it bypass restrictions

如果状态码是4xx
尝试将它改为200 OK 并看他是否绕过限制
```
#### 2FA代码泄漏响应 - 2FA Code Leakage in Response
```
Check the response of the 2FA Code Triggering Request to see if the code is leaked
检查2FA代码触发请求的响应，以查看代码是否已泄露
```
#### JS文件分析 - JS File Analysis
```
Rare but some JS Files may contain info about the 2FA Code, worth giving a shot
罕见但有些JS文件可能包含有关2FA代码的信息，值得试一下
```
#### 2FA代码重用 - 2FA Code Reusability
```
Same code can be reused
可以重复使用相同的代码
```
#### 缺乏爆破保护 - Lack of Brute-Force Protection
```
Possible to brute-force any length 2FA Code
可能爆破任何长度2FA代码
```
#### 缺少2FA代码完整性验证 - Missing 2FA Code Integrity Validation
```
Code for any user acc can be used to bypass the 2FA
任何用户帐户的代码可用于绕过2FA
```
#### CSRF在2FA禁用时 - CSRF on 2FA Disabling
```
No CSRF Protection on disabling 2FA, also there is no auth confirmation
没有CSRF保护对禁用2FA，也没有授权确认
```
#### 密码重置禁用2FA - Password Reset Disable 2FA
```
2FA gets disabled on password change/email change
2FA在密码更改/电子邮件更改时禁用
```
#### 备份代码滥用 - Backup Code Abuse
```
Bypassing 2FA by abusing the Backup code feature
Use the above mentioned techniques to bypass Backup Code to remove/reset 2FA restrictions

通过滥用备份代码功能绕过2FA
使用上述技术来绕过备份代码来移除/重置2FA的限制
```
#### 在2FA禁用页面上点击劫持 - Clickjacking on 2FA Disabling Page
```
Iframing the 2FA Disabling page and social engineering victim to disable the 2FA
ifRaming 2FA禁用页面和社交工程受害者禁用2FA
```
#### 启用2FA不会过期以前的活动会话 - Enabling 2FA doesn't expire Previously active Sessions
```
If the session is already hijacked and there is a session timeout vulnerable
如果会话已经被劫持，并且有一个会话超时漏洞
```
#### 用null或者000000绕过2FA - Bypass 2FA with null or 000000
```
Enter the code 000000 or null to bypass 2FA protection.
输入代码000000或null以绕过2FA保护。
```
___

### Articles 
- [Testing Two-Factor Authentication](https://research.nccgroup.com/2021/06/10/testing-two-factor-authentication/) by [NCC Group](https://research.nccgroup.com/)


## Author

[Harsh Bothra](https://twitter.com/harshbothra_) \
[Vishal Saini](https://twitter.com/k4k4r07)
