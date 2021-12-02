---
title: jmeter相关安装
date: 2021-12-01 14:11:42
categories:
- 性能测试
- jmeter
tags:
- jmeter
---
###### JDK安装(jdk11以上版本没有jre)
选择相应的文件下载：https://www.oracle.com/java/technologies/downloads/#jdk17-windows
(下载的JDK17，貌似不用配置环境变量也可使用)

###### JDK1.8安装及配置环境变量
1、双击jdk1.8安装之后会有2个文件，第1个jdk存C:\Java文件中，第2个Java的jre存C :\java_jre文件夹中
![新建文件夹](\source\_posts\jmeter1/文件夹.png)
2、新建用户变量JAVA_HOME  值为：C:\java
![新建用户变量JAVA_HOME](\source\_posts\jmeter1/用户变量JAVA_HOME.png)
3、CLASSPATH，路径：.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;
![CLASSPATH](\source\_posts\jmeter1/CLASSPATH.png)
4、变量名：Path  (用户变量)  变量值： %JAVA_HOME%\bin
![%JAVA_HOME%\bin](\source\_posts\jmeter1/java_home_bin.png)
5、系统变量path填：
&ensp;&emsp;C:\java\bin
&ensp;&emsp;C:\java\jre
&ensp;&emsp;C:\java_jre\bin
&ensp;&emsp;C:\java_jre\lib 
![系统环境变量](\source\_posts\jmeter1/系统环境变量.png)
6、在doc窗口输入以下命名
```
java -version
javac -version
```
出现以下结果表示配置成功
![doc窗口结果](\source\_posts\jmeter1/cmd.png)
###### JDK卸载干净
安装java jdk之后，会有两个程序:①java 8 update 60（64-bit）；②java SE Development Kit8 update 60（64-bit），然后点击，弹出“卸载”，点击即可。
![](\source\_posts\jmeter1/应用和功能.png)

###### jmeter下载
http://jmeter.apache.org/download_jmeter.cgi
在\apache-jmeter-5.4.1\bin点击jmeter.bat直接运行
###### jmeter用到的插件
https://jmeter-plugins.org/downloads/old/
将相应jar包放在\apache-jmeter-5.4.1\lib\ext文件夹下

推荐使用插件：
https://github.com/Zyxzhongzhi/utils/tree/main/jmeter%E9%A9%B1%E5%8A%A8%E5%8C%85(%E6%94%BE%E5%9C%A8lib%EF%BC%8Cext%E4%B8%8B)
---
jmeter插件管理：jmeter-plugins-manager-1.4.jar：菜单栏上会多出一个“Plugins Manager”的按钮，点击可以查看各种插件,选择要安装的插件之后，点击底部按钮，就会自动安装并重启
![](\source\_posts\jmeter1/options.png)
![](\source\_posts\jmeter1/Available.png)
jmeter扩展插件：JMeterPlugins-Standard.jar、JMeterPlugins-Extras.jar：监听器中会多出以下内容
![](\source\_posts\jmeter1/扩展插件内容.png)

测试websocket:options --> Plugins Manager --> Available Plugins 搜索"WEBSOCKET"
勾选需要的并点击Apply and restart jmeter,这时manager会自动下载依赖包并安装到lib目录下

Jmeter进行webSocket接口测试：https://www.cnblogs.com/penghaihang/p/7724830.html
###### jmeterHTTP请求返回数据乱码
jmeterHTTP请求内容编码已设置成utf-8，返回中文依旧显示乱码
这时需修改jmeter安装目录下 /bin/jmeter.properties配置文件
Ctrl+F搜索“sampleresult.default.encoding”去掉#
sampleresult.default.encoding=ISO-8859-1，将ISO-8859-1更改为UTF-8，如图所示
![](\source\_posts\jmeter1/properties修改.png)