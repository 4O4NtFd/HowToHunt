# Bypassing File Uploads文件上传绕过

Suppose you have a limitation that you can only upload in a few formats like PDF, JPEG, JPG, ….But what if you can upload a PHP file by defying the Upload mechanism and validation of file type check. let me tell you if someone can upload a PHP file then its game over for the website as he will upload a php shell and can easily perform an RCE , or Worst will simply gain a reverse shell on the server.
假设您有一个限制，即您只能以几种格式上传，例如 PDF、JPEG、JPG ……但是如果您可以通过无视上传机制和文件类型检查验证来上传 PHP 文件呢？ 让我告诉你，如果有人可以上传 PHP 文件，那么它的网站游戏就结束了，因为他将上传一个 php shell 并且可以轻松执行 RCE(远程命令执行)，或者最糟糕的是只会在服务器上获得一个反向 shell。

> __How does Bypass work  如何绕过__

Well it depends on which kind of validation the system is using …it is just verifying the extension ?? if its just doing that then it becomes very easy to bypass and upload a PHP file or something malicious. suppose we have to upload a JPG file so the extension must be something.jpg
好吧，这取决于系统使用的是哪种验证……它只是验证扩展名？？ 如果它只是这样做，那么绕过和上传 PHP 文件或恶意文件就变得非常容易。 假设我们必须上传一个 JPG 文件，所以扩展名必须是 something.jpg

---


### 1. Bypassing Normal extension  绕过正常扩展名
Now what we can do is we can upload a file which looks like this something.php.jpg or somethings.jpg.php.
现在我们可以做的是我们可以上传一个看起来像something.php.jpg 或somethings.jpg.php 的文件。

### 2. Bypassing the magic Byte validation.  绕过魔术字节验证。

For this method we use polyglots. Polyglots, in a security context, are files that are a valid form of multiple different file types. For example, a GIFAR is both a GIF and a RAR file. There are also files out there that can be both GIF and JS, both PPT and JS, etc.
对于这种方法，我们使用多语言。 在安全上下文中，多语言是多种不同文件类型的有效形式的文件。 例如，GIFAR 既是 GIF 又是 RAR 文件。 还有一些文件可以是 GIF 和 JS，也可以是 PPT 和 JS 等。

so while we have to upload a JPEG file type we actually can upload a PHAR-JPEG file which will appear to be a JPEg file type to the server while validating. the reason is the file PHAR-JPEg file has both the JPEG header and the PHP file also. so while uploading it didn’t get detected and later after processing the PHP file can be used to exploit.
因此，虽然我们必须上传 JPEG 文件类型，但实际上我们可以上传一个 PHAR-JPEG 文件，该文件将在验证时显示为 JPEG 文件类型。 原因是文件 PHAR-JPEg 文件同时具有 JPEG 标头和 PHP 文件。 所以在上传时它没有被检测到，稍后处理 PHP 文件后就可以被利用了。

And at last Uploading a shell to some random websites for fun is not really cool so don’t ever try until unless you have the permission to test.
最后，为了好玩而将 shell 上传到一些随机网站并不是很酷，所以除非您获得测试许可，否则不要尝试。

-----

**How the bypass was possible?·`如何绕过？`**

1. Create a malicious file with an extension that is accepted by the application.`使用应用程序接受的扩展名创建恶意文件。`
2. Upload that file and click on send.`上传该文件并单击发送。`
3. Capture the request in any proxy tool, edit the file extension to the malicious extension that you want. In some cases, you might need to change the content type of a file.`在任何代理工具中捕获请求，将文件扩展名编辑为您想要的恶意扩展名。 在某些情况下，您可能需要更改文件的内容类型。`
4. Forward the request to the server.`将请求转发到服务器。`

------

**Test PDF upload functionality. 测试 PDF 上传功能**

- [https://github.com/jonaslejon/malicious-pdf](https://github.com/jonaslejon/malicious-pdf)

Resources :-

- [File upload Bypass pdf](https://harshitsengar.in/resources/File%20Upload%20Bypass%20.pdf)
