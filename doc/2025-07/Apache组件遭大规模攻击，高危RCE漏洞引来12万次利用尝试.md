#  Apache组件遭大规模攻击，高危RCE漏洞引来12万次利用尝试  
 FreeBuf   2025-07-04 11:03  
  
![](https://mmbiz.qpic.cn/mmbiz_gif/qq5rfBadR38jUokdlWSNlAjmEsO1rzv3srXShFRuTKBGDwkj4gvYy34iajd6zQiaKl77Wsy9mjC0xBCRg0YgDIWg/640?wx_fmt=gif "")  
  
  
![](https://mmbiz.qpic.cn/mmbiz_png/qq5rfBadR3ica9YjnMjbyPguILa0zKicqhicnOlE1F7YSxlE0icNql7PR73mkCsu5rEQHGLq4KL7FL1Jkwrf2tdSUw/640?wx_fmt=png&from=appmsg "")  
  
  
**Part01**  
## 漏洞态势分析  
  
  
帕洛阿尔托网络公司Unit 42团队最新研究报告显示，针对Apache Tomcat和Apache Camel关键漏洞的网络攻击正在全球激增。2025年3月披露的这三个远程代码执行（RCE, Remote Code Execution）漏洞——CVE-2025-24813（Tomcat）、CVE-2025-27636与CVE-2025-29891（Camel）——已为攻击者提供了系统劫持的直接通道。  
  
  
报告特别警告：成功利用这些漏洞可使攻击者以Tomcat/Camel权限执行任意代码。监测数据显示，仅2025年3月就记录了来自70余个国家的125,856次扫描探测与漏洞利用尝试。  
  
  
**Part02**  
## 技术细节剖析  
  
### Tomcat漏洞机制  
  
当启用部分PUT请求和会话持久化功能时，用于运行Java Web应用的Apache Tomcat（9.0.0.M1至9.0.98、10.1.0-M1至10.1.34及11.0.0-M1至11.0.2版本）存在HTTP PUT请求处理缺陷。攻击者可借此覆盖序列化会话文件，在反序列化时触发恶意代码执行。  
  
  
典型攻击分为两个阶段：  
1. **载荷投递**  
通过HTTP PUT请求上传伪装成.session文件的序列化恶意对象  
  
1. **触发执行**  
精心构造包含JSESSIONID=.[文件名]的HTTP GET请求，诱使Tomcat反序列化执行载荷  
  
###   
### Camel漏洞成因  
  
该中间件框架因HTTP头部过滤机制存在大小写敏感缺陷，攻击者可通过畸形头部注入恶意命令。例如未有效拦截"CAmelExecCommandExecutable"等变体头部，导致远程命令执行漏洞。  
  
  
**Part03**  
## 防御应对建议  
  
  
Unit 42提出关键缓解措施：  
- **Tomcat配置**  
禁用partial PUT功能并启用readonly设置  
  
- **Camel加固**  
严格校验和净化HTTP头部输入  
  
- **威胁监测**  
使用专业工具检测默认会话名滥用和可疑Content-Range头部  
  
安全团队观察到，大量Tomcat漏洞利用尝试与开源工具Nuclei Scanner的模板高度相似，这意味着攻击门槛显著降低。目前相关补丁已发布，使用受影响组件的组织应立即更新。  
  
  
**参考来源：**  
  
Apache Under Attack: Critical RCE Flaws in Tomcat & Camel Spark Thousands of Exploit Attempts  
  
https://securityonline.info/apache-under-attack-critical-rce-flaws-in-tomcat-camel-spark-thousands-of-exploit-attempts/  
  
  
###   
###   
###   
  
**推荐阅读**  
  
[](https://mp.weixin.qq.com/s?__biz=MjM5NjA0NjgyMA==&mid=2651324107&idx=1&sn=f89429997e0347cfe1580cc8ca6e858b&scene=21#wechat_redirect)  
  
### 电台讨论  
  
****  
  
  
  
![图片](https://mmbiz.qpic.cn/mmbiz_gif/qq5rfBadR3icF8RMnJbsqatMibR6OicVrUDaz0fyxNtBDpPlLfibJZILzHQcwaKkb4ia57xAShIJfQ54HjOG1oPXBew/640?wx_fmt=gif&wxfrom=5&wx_lazy=1&tp=webp "")  
  
   
  
