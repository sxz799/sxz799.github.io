---
title: 修改Tomcat的默认访问路径为你的JSP项目首页
copyright: true
date: 2020-05-22 23:35:44
tags:
- 技巧
categories:
- 教程
comments:
password:
---
我们都知道将打包好的项目放到Tomcat的webapp目录下后，Tomcat会自动解压，但是如果想访问项目就需要在url后加上我们的项目目录才可以访问到我们项目的默认index主页（这个是可以修改的），那么我们怎样做到输入端口号后直接访问到我们的项目呢?也很简单，修改Tomcat的配置文件就可以实现了。
## 配置方法
找到Tomcat安装目录下的conf文件夹内的server.xml文件，找到最后面部分
添加这一段代码
```
<Context path="" docBase="WDAdmin" debug="0"/>
```
```
      <Host name="localhost"  appBase="webapps"
            unpackWARs="true" autoDeploy="true">

        <!-- SingleSignOn valve, share authentication between web applications
             Documentation at: /docs/config/valve.html -->
        <!--
        <Valve className="org.apache.catalina.authenticator.SingleSignOn" />
        -->

        <!-- Access log processes all example.
             Documentation at: /docs/config/valve.html
             Note: The pattern used is equivalent to using pattern="common" -->
        <Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
               prefix="localhost_access_log" suffix=".txt"
               pattern="%h %l %u %t &quot;%r&quot; %s %b" />
         <!-- 添加下面这段代码 -->
        <Context path="" docBase="WDAdmin" debug="0"/>
      </Host>
    </Engine>
  </Service>
</Server>
```
按照下图的提示进行修改即可
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20200523/20200523001725.png" width="600px"/>
