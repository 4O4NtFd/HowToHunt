## 通过响应操作在寄存器帐户上的OTP绕过 - OTP Bypass on Register account via Response manipulation

 ### 1. 第一个方法 - First Method
1. Register account with mobile number and request for OTP.
`使用手机号码的注册帐户和OTP的请求。`
2. Enter incorrect OTP and capture the request in Burpsuite.
`输入不正确的OTP并捕获在Burpsuite中的请求。`
3. Do intercept response to this request and forward the request.
`为此请求进行拦截回复并转发请求。`
4. response will be 
`回复将是 `

`{"verificationStatus":false,"mobile":9072346577","profileId":"84673832"}`

5. Change this response to

   `改变这个响应`

`{"verificationStatus":true,"mobile":9072346577","profileId":"84673832"}`

6. And forward the response.

   `并转发响应。`

7. You will be logged in to the account.

   `您将登录到帐户。`

***Impact: Account Takeover***

### 2. 第二个方法 - Second Method.
1. Go to login and wait for OTP pop up.
    `转到登录并等待OTP弹出。`
    
2. Enter incorrect OTP and capture the request in Burpsuite.
    `输入不正确的OTP并捕获在Burpsuite中的请求。`
    
3. Do intercept response to this request and forward the request.
   `对此请求进行拦截响应并转发请求。`
   
4. response will be 
`回复将是 `
    `error`

5. Change this response to
`改变这个响应`
`success`
   
6. And forward the response.
`并转发响应。`

7. You will be logged in to the account.

    `您将登录到帐户。`

***Impact: Account Takeover***

***影响：账户接管***

### 3. 第三个方法 - Third Method:

  ```
    1.Register 2 accounts with any 2 mobile number(first enter right otp)
      注册2个帐户，其中包含任何2个手机号码（首先输入正确的OTP）
    
    2.Intercept your request
      拦截您的请求
    
    3.click on action -> Do intercept -> intercept response to this request.
      单击“操作” - > 拦截 - >拦截对此请求的响应。
    
    4.check what the message will display like status:1
      检查邮件将显示的状态为状态：1
    
    5.Follow the same procedure with other account but this time enter wrong otp
      使用其他帐户相同的过程，但此时输入错误的OTP
    
    6.Intercept respone to the request
      拦截响应到request
    
    7.See the message like you get status:0
      将您获得状态的消息：0
    
    8.Change status to 1 i.e, status:1 and forward the request if you logged in means you just done authentication bypass.
      将状态为1 i.e，状态：1，如果您登录的情况下，请转发请求意味着您刚刚完成身份验证绕过。 
  ```

## 通过使用repeater多次重复提交表格，绕过注册表格中的OTP - Bypassing OTP in registration forms by repeating the form submission multiple times using repeater

**步骤 :**

```
      1. Create an account with a non-existing phone number
         用一个不存在的电话号码创建一个账户
      
      2. Intercept the Request in BurpSuite
         在BurpSuite中拦截请求
      3. Send the request to the repeater and forward
         将请求发送到repeater并转发
      4. Go to Repeater tab and change the non-existent phone number to your phone number
         进入repeater标签，将不存在的电话号码改为你的电话号码
      5. If you got an OTP to your phone, try using that OTP to register that non-existent number
         如果你的手机收到了OTP，试着用这个OTP来注册这个不存在的号码。
```

## 不限速 - No Rate Limit
 * 步骤:-
 ```
     1) Create an Account
        创建一个帐户
        
     2) When Application Ask you For the OTP( One-time password ), Enter wrong OTP and Capture this Request In Burp.
        当应用程序询问您输入OTP（一次性密码）时，输入错误的OTP并在Burp中捕获此请求。
        
     3) Send This Request into Repeater and repeat it by setting up payload on otp Value.
        将此请求发送到Repeater并通过在OTP值上设置payload重复它。
        
     4) if there is no Rate Limit then wait for 200 Status Code (Sometimes 302)
        如果没有速率限制，那么等待200状态代码（有时302）
        
     5)if you get 200 ok or 302 Found Status Code that means you've bypass OTP
        如果您获得200 ok或302 Found状态代码，这意味着您绕过了OTP
 ```

### Contributors:
* [@akshaykerkar13](https://twitter.com/akshaykerkar13)
* [@Yn0tWhy](https://twitter.com/Yn0tWhy)
* [@Virdoex_hunter](https://twitter.com/Virdoex_hunter)
* [febinrev](https://twitter.com/febinrev)
* [Fani Malik](https://twitter.com/fanimalikhack)
