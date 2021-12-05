**Identifying a WAF  识别WAF**

```
dig +short example.com
curl -s https://ipinfo.io/IP | jq -r '.org'
```

-  With AWS, you can often identify a load balancer with the presence of "AWSLB" and "AWSLBCORS" cookies
   使用 AWS，您通常可以通过存在“AWSELB”和“AWSALBCORS”cookie 来识别负载均衡器

**Identifying the source确定来源**

- Use https://dnsdumpster.com to generate a map.
  使用 https://dnsdumpster.com 生成地图。

- Next, make a search using Censys and save the IP's that look to match your target in a text file.
  接下来，使用 Censys 进行搜索并将与目标匹配的 IP 保存在文本文件中。

  Example: https://censys.io/ipv4?q=0x00sec.org

- Another way you can find IP's tied to a domain is by viewing their historical IPs. You can do this with SecurityTrails DNS trails. 
找到与域相关的 IP 的另一种方法是查看它们的历史 IP。 您可以使用 SecurityTrails DNS 跟踪来完成此操作。

	https://securitytrails.com/domain/0x00sec.org/dns
	
	- Here we can see what A records existed and for how long. It is so common for an administrator to switch to a WAF solution after X amount of years of using it bare-metal, and do you think they configure whitelisting? No of course not, it works fine!
	  在这里我们可以看到 A 记录存在哪些以及存在多长时间。 管理员在裸机使用 X 年之后切换到 WAF 解决方案是如此普遍，您认为他们配置了白名单吗？ 不，当然不是，它工作正常！
	-	you can just copy the entire table(Select full table and copy paste it in a txt file) body and use awk to filter the IP's out.
		您可以复制整个表格（选择完整表格并将其复制粘贴到 txt 文件中）正文并使用 awk 过滤掉 IP。
		
		`grep -E -o "([0-9]{1,3}[\\.]){3}[0-9]{1,3}" tails.txt | sort -u | tee -a ips.txt`
		

**DNS Enumeration  DNS 枚举**
		

	If you enumerate your targets DNS, you may find that they have something resembling a dev.example.com or staging.example.com subdomain, and it may be pointing to the source host with no WAF. 
	如果您枚举目标 DNS，您可能会发现它们具有类似于 dev.example.com 或 staging.example.com 子域的内容，并且它可能指向没有 WAF 的源主机。
		
	- Get all the subdomains.获取所有子域。
		`subfinder -silent -d 0x00sec.org | dnsprobe -silent | awk  '{ print $2 }'  | sort -u | tee -a ips.txt`

**Checking IP's for hosts  检查主机的IP**


```
for ip in $(cat ips.txt) # iterate through each line in file
do 
	org=$(curl -s <https://ipinfo.io/$ip> | jq -r '.org') #  Get Org from IPInfo
  title=$(timeout 2 curl -s -k -H "Host: 0x00sec.org" <https://$ip/> | pup 'title text{}') # Get title
	echo "IP: $ip Title: $title Org: $org" # Print results
done 
```
in one line, same command:在一行中，相同的命令：
`for ip in $(cat ips.txt); do org=$(curl -s <https://ipinfo.io/$ip> | jq -r '.org'); title=$(timeout 2 curl --tlsv1.1 -s -k -H "Host: 0x00sec.org" <https://$ip/> | pup 'title text{}'); echo "IP: $ip Title: $title Org: $org"; done`


- What we have now is a quick overview of which IP's respond to which Host header, and we can view the title
  现在我们可以快速浏览一下哪个 IP 响应哪个 Host 标头，我们可以查看标题
- We went through each host, requested the IP directly with the host header, and we have our source IP!
  我们遍历了每个主机，直接用主机头请求IP，我们就有了源IP！

**Setting the Host Header manually  手动设置主机头**
`curl -s -k -H "Host: 0x00sec.org" https://<ip address>/`

or set Host Header in burp.  或者在 burp 中设置 Host Header。

**CloudFail** 

```
git clone <https://github.com/m0rtem/CloudFail.git>
cd CloudFail
pip install -r requirements.txt
python3 cloudfail.py -t 0x00sec.org
```

**But first, Recon!  但首先，侦察！**

- The idea is to start your normal recon process and grab as many IP addresses as you can (host, nslookup, whois, ranges…), then check which of those servers have a web server enabled (netcat, nmap, masscan). 
  这个想法是开始您的正常侦察过程并获取尽可能多的 IP 地址（主机、nslookup、whois、范围……），然后检查其中哪些服务器启用了 Web 服务器（netcat、nmap、masscan）。
- Once you have a list of web server IP, the next step is to check if the protected domain is configured on one of them as a virtual host.
  获得 Web 服务器 IP 列表后，下一步是检查受保护域是否在其中一个上配置为虚拟主机。

**Censys**
- Choose “Certificates” in the select input, provide the domain of your target, then hit \<enter\>
  在选择输入中选择“证书”，提供目标域，然后点击 \<enter\>
- You should see a list of certificates that fit to your target
  您应该会看到适合您的目标的证书列表
- Click on every result to display the details and, in the “Explore” menu at the very right, choose “IPv4 Hosts”.
  单击每个结果以显示详细信息，然后在最右侧的“探索”菜单中选择“IPv4 主机”。
- You should be able to see the IP addresses of the servers that use the certificate
  您应该能够看到使用证书的服务器的 IP 地址
- From here, grab all IP you can and, back to the previous chapter, try to access your target through all of them.
  从这里开始，获取所有可以获取的 IP，然后返回上一章，尝试通过所有 IP 访问您的目标。

  example: 
  `curl -s -k -H "Host: 0x00sec.org" https://<ip address>/`

**Mail headers  邮件标题**

- The next step is to retrieve the headers in the mails issued by your target: Subscribe the newsletter, create an account, use the function “forgotten password”, order something… in a nutshell do whatever you can to get an email from the website you’re testing 
  下一步是检索目标发出的邮件中的标题：订阅时事通讯，创建一个帐户，使用“忘记密码”功能，订购一些东西……简而言之，尽一切可能从您的网站上获取电子邮件 正在测试
- Once you get an email, check the source, and especially the headers. Record all IPs you can find there, as well as subdomains, that could possibly belong to a hosting service. And again, try to access your target through all of them.
  收到电子邮件后，请检查来源，尤其是标题。 记录您可以在那里找到的所有 IP 以及可能属于托管服务的子域。 再次，尝试通过所有这些访问您的目标。

The value of header Return-Path worked pretty well

Tool: https://github.com/christophetd/CloudFlair
This tools works on censys data.

References:
https://delta.navisec.io/a-pentesters-guide-part-5-unmasking-wafs-and-finding-the-source/
https://blog.detectify.com/2019/07/31/bypassing-cloudflare-waf-with-the-origin-server-ip-address/

# Authors
* [@maverickNerd](https://twitter.com/maverickNerd)
