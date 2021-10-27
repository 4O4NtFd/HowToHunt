# 隐藏的 API 功能暴露 - Hidden API Functionality Exposure
- 应用程序编程接口 (API) 已成为几乎所有业务的关键部分。 API 负责在公司内部或外部公司的系统之间传输信息。 例如，当您登录 Google 或 Facebook 等网站时，API 会处理您的登录凭据以验证它们是否正确。
- Application programming interfaces (APIs) have become a critical part of almost every business. APIs are responsible for transferring information between systems within a company or to external companies. For example, when you log in to a website like Google or Facebook, an API processes your login credentials to verify they are correct.

1. Swagger UI 文档 - Swagger UI Documentation
2. 字典攻击 | 暴力破解 - Dictionary Attack | Brute force
3. API 枚举的常用词表: - Common wordlist for API Enum :
- https://wordlists.assetnote.io/
- https://github.com/Net-hunter121/API-Wordlist

## 执行此攻击的步骤 - Steps to Perform This Attack :
```
第 1 步：将请求捕获到 Burp 中，将请求发送到转发器(repeater)和入侵者(intruder)选项卡
第 2 步：将端点添加到入侵者(intruder)选项卡中，并从单词列表中添加payload
第 3 步：第 1 次在端点上使用带有 sec-list 的字典攻击
第 4 步：使用您的自定义列表或使用我在上一节中提供的列表
第 5 步：然后简单地开始攻击，开始检查 200 状态
第 6 步：一旦它们的状态为 200，就在同一端点上启动递归扫描，以获取诸如 swagger doc 等多汁信息。
第 7 步：其他方法是更改 API 版本并尝试暴力破解相同的端点
例如：Redacted.com/api/v1/{Endpoint} ----- Redacted.com/api/v2/{Endpoint}

Step 1 : Capture the request into Burp, Send the request to repeater and intruder tab
Step 2 : Add the endpoint into the intruder tab and add the payload from the word-list
Step 3 : 1st use dictionary attack with sec-list on the Endpoint
Step 4 : Either use your customized list or use the ones which i have provided in the above section
Step 5 : Then simply start the attack, Start checking for 200 status
Step 6 : Once their is 200 status OK, Start the recursive scan on the same endpoint for juicy information like swagger doc and so on.
step 7 : Other method is to change the API version and try bruteforcing the same endpoint
Eg: Redacted.com/api/v1/{Endpoint} ----- Redacted.com/api/v2/{Endpoint}
```
* 注意：它们将是每个请求的最小限制，这些限制将在没有 API 密钥的情况下分配，因此请确保尽可能多地使用手动方法，然后其余部分可以通过自动化工具自动扫描 API 中的漏洞。
* Note: Their will be minimum limits per request which will be assigned without API keys so make sure to utilize manual approach as much as you can,Then the rest can be automated for scanning the vulnerability in API with automated tools.

## 贡献者:
- [N3T_hunt3r](https://twitter.com/N3T_hunt3r)
