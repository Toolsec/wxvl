#  漏洞预警 | Oracle数据库远程接管漏洞  
浅安  浅安安全   2025-07-22 00:00  
  
**0x00 漏洞编号**  
- # CVE-2025-30751  
  
**0x01 危险等级**  
- 高危  
  
**0x02 漏洞概述**  
  
Oracle数据库是全球广泛使用的关系型数据库管理系统。  
  
![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/7stTqD182SVjdb8W7T5YIrddGeQMLUBTXbxfZXlfOKXWTLDDbHJlEslX5e6xKhdokgiccSG2ibPY1uNib5wFzVicEg/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1&tp=webp "")  
  
**0x03 漏洞详情**  
###   
  
**CVE-2025-30751**  
  
**漏洞类型：**  
远程接管  
  
**影响：**  
越权接管  
  
  
  
**简述：**  
Oracle数据库服务器组件存在远程接管漏洞，具备Create Session和Create Procedure权限的攻击者可利用该漏洞完全接管Oracle数据库。  
  
**0x04 影响版本**  
- 19.3 <= Oracle Database <= 19.27  
  
- 23.4 <= Oracle Database <= 23.8  
  
**0x05****POC状态**  
- 未公开  
  
****  
**0x06****修复建议**  
  
**目前官方已发布漏洞修复版本，建议用户升级到安全版本****：**  
  
https://www.oracle.com/cn/  
  
  
  
