# Misconfigured CORS - 错误配置的 CORS
 Here are few methods and steps you can do to check for misconfigure cors.
您可以通过以下几种方法和步骤来检查配置错误的 cors。

* Hunting method 1(Single target):
  狩猎方式一（单一目标）：

```
Step->1. Capture the target website and spider or crawl all the website using burp.
Step->2. Use burp search look for Access-Control
Step->3. Try to add Origin Header i.e,Origin:attacker.com or Origin:null or Origin:attacker.target.com or Origin:target.attacker.com
Step->4  If origin is reflected in response means the target is vuln to CORS
步骤->1.捕获目标网站，并使用burp对所有网站进行蜘蛛搜索或抓取。
步骤->2.使用 burp 搜索查找Access-Control
步骤->3.尝试添加 Origin Header，即 Origin:attacker.com 或 Origin:null 或 Origin:attacker.target.com 或 Origin:target.attacker.com
Step->4.如果Origin在响应中被反映出来，意味着目标对CORS是脆弱的。
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

* Hunting method 2(multiple means including subdomains):
  狩猎方法2（包括子域的多重手段）
```
step 1-> find domains i.e subfinder -d target.com -o domains.txt
step 2-> check alive ones : cat domains.txt | httpx | tee -a alive.txt
step 3-> send each alive domain into burp i.e, cat alive.txt | parallel -j 10 curl --proxy "http://127.0.0.1:8080" -sk 2>/dev/null
step 4-> Repeat hunting method 1
步骤 1-> 找到域名，即 subfinder -d target.com -o domains.txt
步骤 2-> 检查活着的域名：cat domains.txt | httpx | tee -a alive.txt
步骤 3-> 将每个存活的域名送入burp，即cat alive.txt | parallel -j 10 curl --proxy "http://127.0.0.1:8080" -sk 2>/dev/null
步骤 4-> 重复狩猎方法1
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

* Both above method are manual methods so lets check an automated way
  以上两种方法都是手动方法，所以让我们检查一下自动方法
# 工具
* [https://github.com/chenjj/CORScanner](https://github.com/chenjj/CORScanner)
* [https://github.com/lc/theftfuzzer](https://github.com/lc/theftfuzzer)
* [https://github.com/s0md3v/Corsy](https://github.com/s0md3v/Corsy)
* [https://github.com/Shivangx01b/CorsMe](https://github.com/Shivangx01b/CorsMe)

# 自动方法：
```
step1-> find domains i.e, subfinder -d domain.com -o target.txt
step2-> grep alive: cat target.txt | httpx | tee -a alive.txt
step3-> grep all urls using waybackurls by @tomnomnom and gau tool i.e,cat alive.txt | gau | tee -a urls.txt
step4-> run any of these tools on each url 
step5-> configure the manually
步骤1-> 查找域，即subfinder -d domain.com -o target.txt
步骤2-> grep alive: cat target.txt | httpx | tee -a alive.txt
步骤3-> 使用tomnomnom的waybackurls和gau工具，grep所有的urls，例如，cat alive.txt | gau | tee -a urls.txt
步骤4-> 在每个URL上运行这些工具中的任何一个 
步骤5-> 手动配置
```
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# 其他方法

### 本方法所需的工具。
* [https://github.com/tomnomnom/meg](https://github.com/tomnomnom/meg)
* [https://github.com/tomnomnom/gf](https://github.com/tomnomnom/gf)
* [https://github.com/projectdiscovery/subfinder](https://github.com/projectdiscovery/subfinder)
* [https://github.com/tomnomnom/assetfinder](https://github.com/tomnomnom/assetfinder)
* [https://github.com/Edu4rdSHL/findomain](https://github.com/Edu4rdSHL/findomain)
* [https://github.com/projectdiscovery/httpx](https://github.com/projectdiscovery/httpx)
         
### 步骤
```
1) Find Domains with the help of subfinder,assetfinder,findomain i.e , subfinder -d target.com | tee -a hosts1 , findomain -t target.com | tee -a hosts1 , assetfinder --subs-only target.com |tee -a hosts1 .
2) Then cat hosts1 | sort -u | tee -a hosts2 and then cat hosts2 | httpx | tee -a hosts .
3) Navigate through terminal where hosts file is located  echo "/" > paths
4) Then type meg -v
5) After the completion of process type gf cors.
6) All the urls with Access-Control-Allow will be displayed.  

1) 在subfinder,assetfinder,findomain的帮助下查找域名，即
	subfinder -d target.com | tee -a hosts1 , 
	findomain -t target.com | tee -a hosts1 , 
	assetfinder --subs-only target.com |tee -a hosts1。
2) 然后cat hosts1 | sort -u | tee -a hosts2 ，然后cat hosts2 | httpx | tee -a hosts 。
3) 通过终端浏览hosts文件的位置 echo "/" > paths
4) 然后输入meg -v
5) 进程完成后，输入gf cors。
6) 所有带有Access-Control-Allow的URL将被显示出来。 
```

# Authors
* [@Virdoex_hunter](https://twitter.com/Virdoex_hunter)
