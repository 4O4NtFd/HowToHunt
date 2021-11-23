# Easy CVES using Researching - 简单的CVES使用研究

### 工具
* Google
* Twitter
* Nuclei
  
## 步骤:
```
    1.Grab all the subdomains i.e, subfinder -d domain.com | tee -a domains.txt
    2.Grap all alive domains i.e,  cat domains.txt | httpx -status-code | grep 200 | cut -d " " -f1 | tee -a alive.txt
    3.Run nuclei basic-detection,panels,workflows,cves templates differently and store results in different file. i.e, cat alive.txt | nuclei -t nuclei-templates/workflows | tee -a workflows.
    4.Read each output carefully with patience.
    5.Find interest tech used by target. i.e, jira
    6.put that link into browser check the version used by target.
    7.Go on google search with jira version exploit.
    8.grep the cves
    9.Go to twitter in explore tab search CVE(that you found from google) poc or CVE exploit
    10.Go to google and put cve or some details grab from  twitter for a better poc read writeups related to that.
    11.Try all cves if success report it.:)
    
    1.抓取所有子域名，即subfinder -d domain.com | tee -a domains.txt
    2.抓取所有存活的域名，即，cat domains.txt | httpx -status-code | grep 200 | cut -d " " -f1 | tee -a alive.txt
    3.以不同的方式运行nuclei basic-detection, panels, workflows, cves templates，并将结果存储在不同的文件中。例如，cat alive.txt | nuclei -t nuclei-templates/workflows | tee -a workflows。
    4.耐心地阅读每个输出结果。
    5.找到目标所使用的感兴趣的技术，如：jira
    6.把该链接放到浏览器中，检查目标所使用的版本。
    7.在谷歌上搜索jira版本的漏洞。
    8.grep the cves
    9.去twitter的探索标签中搜索CVE（你从google找到的）poc或CVE漏洞
    10.去谷歌并把CVE或一些细节从twitter上抓取，以获得更好的poc阅读与此相关的写法。
    11.尝试所有的CVE，如果成功的话，就报告它。）
```

### Authors
* [@Virdoex_hunter](https://twitter.com/Virdoex_hunter)
  
    
  
