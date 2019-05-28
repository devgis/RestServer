# RestServer

## RestServer 可以方便的将MSSQL,Oracle,MySQL,PostGresql数据库发布成rest服务供我们调用减少程序员的编码。RestServer 简单易用 配置非常简单！
## RestServer is a Helpful soft to publish MSSQL,Oracle,MySQL,PostGresql data to a rest server,so it can help programer reduce workload! And it's very easier to use!

## 1.	使用许可&版权说明
### 1)	在保持本软件完整的情况下可以将本软件用于任何商业用途（不限用途和期限）。
### 2)	本软件可以自由传播，但是请保持软件相关文件和说明文档完整。
### 3)	未经许可不得将本软件反编译进行修改。
### 4)	如不同意以上许可请勿使用本软件。

## 2.	关于RestServer
### RestServer是一个快捷的rest服务器，用于直接将数据库数据发布成json格式方便其他需要json格式数据的地方调用。此程序免费，代码有偿提供。1.0.0.22支持所有表数据返回以及表数据条件返回。

## 3.	使用环境
### 1)	服务器:windows xp,7,8,10,windows server 2003,2008,2012。.
### 2)	.net FrameWork 4.0。
### 3)	数据库:oracle 9i,10g,11g,MSSql2000,2005,2008,2012,MySQL5以上。

## 4.	RestServer配置使用
### 1)	解压软件到相应目录。解压后主要有以下文件：
### 2)	安装.net Framework4.0(去微软官方网站下载或者网络搜索即可。)
### 3)	配置配置文件，配置文件在目录下RestServer.exe.config使用记事本打开即可进行编辑修改。只需修改configuration/appSettings配置节下面的内容（配置之前最好先进行复制备份，然后再进行修改），配置文件说明如下：
<add key="HOSTNAME" value="localhost"/><!--服务器名称-->
    <add key="PORT" value="9001"/><!--Restf服务端口-->
    <add key="DBTYPE" value="MYSQL"/><!--ORACLE,MSSQL,MYSQL-->
    <add key="DBCONSTRING" value="User Id=root;Host=localhost;Database=db_carmanager;password=root"/>
    <!--[SQL]: Data Source = 192.168.0.21; Initial Catalog = testtable; User Id = sa; Password = 123456;-->
    <!--[ORACLE]: Data Source = Data Source=carorcl;Persist Security Info=True;User ID=zcb;Password=zcb-->
    <!--[MySQL]: User Id=root;Host=localhost;Database=db_carmanager;password=root-->
<add key="TABLES" value="t_log,t_car"/> <!--t_test , 分割-->

1.1.0.35中增加
''' <add key="DATATYPE" value="JSON"/><!--JSON,JSONP-->
 <add key="JSONPHANDEL" value="MyJsonP"/><!--DATATYPE为JSONP时配置此节内容-->
 <add key="WRITELOG" value="TRUE"/> <!--t_test , 分割--> '''

* a)	HOSTNAME为当前主机名称,id地址或域名。
* b)	PORT为需要使用的端口，请使用系统没有用的否则会创建失败。
* c)	DBTYPE为数据库类型 必须为ORACLE,MSSQL或MYSQL，分别对应使用ORACLE数据库,MS SqlServer,MySQL数据库。
* d)	DBCONSTRING为数据库的链接内容 请参考下方样本按照DBTYPE类型进行配置。
* e)	DATATYPE为类型 支持JSON,JSONP。
* f)	JSONPHANDEL 设置类型为JSONP时需要配置此内容。
* g)	WRITELOG 为True时写日志 否则不写日志。
* 4)	启动软件注意win7以上系统包括Server 2008以上系统请使用右键管理员方式执行，否则会启动失败。启动成功后会有如下提示：
* 表示服务已经启动成功。接下来我们就可以受用了。

## 5.	开始使用
* 启动成功后就可以使用了。比如上一节配置了t_log和t_car两张表
* 这时候我们就可以在IE里边输入以下内容进行操作。
### 1)	查询表中所有内容返回json,输入http://localhost:9001/rest/t_car/query我们就可以在浏览器中看到如下结果：
 
### 2)	我们需要对标进行查询，比如carno="山A23392"这时候我们可以进行如下查询：http://localhost:9001/rest/t_car/query/carno= carno="山A23392"这时浏览器中显示如下：
 
* 当然这里边可以支持sql语句中的where语句进行组合查询。这里就不再做详细说明了。
### 3)	按列查找
* 字符类型查找如下：
* http://localhost:9001/rest/T_TEST/name/'张三'
* 查询结果：
* 按照数值列等查找则值不需要’’如下：
* http://localhost:9001/rest/T_TEST/id/1
* 查询结果如下：
* 由于1.1.0.35以后支持JASONP 这时候返回结果类似如下：

## 6.	2.0新增内容
* 支持Postgresql数据库(各scheme中表名勿重复)
* localhost:9001/rest/T_TEST/q 查询全部 eq:http://localhost:9001/rest/T_TEST/q
* localhost:9001/rest/T_TEST/q/{where} 按条件查询 eq:http://localhost:9001/rest/T_TEST/q/id='1'
* localhost:9001/rest/T_TEST/{colname}/{colvalue} 按列查询 eq:http://localhost:9001/rest/T_TEST/id/'1'
* localhost:9001/rest/T_TEST/q/p/{pagesize}/{pageindex} 所有数据分页 eq:http://localhost:9001/rest/T_TEST/q/p/5/1
* localhost:9001/rest/T_TEST/q/p/{pagesize}/{pageindex}/{where} 按查询条件分页 eq:http://localhost:9001/rest/T_TEST/q/p/10/1/id='1'
*带{}为变量 需要输入相应值或者表达式(Where)
全部为get方式

## 7.	联系我们
* 查询所有以及按条件查询已经覆盖了现在互联网上所有的的查询内容需求，当然如果您需要更进一步的功能或者需要源码自己进行深入开发可以通过以下方式联系我：
### QQ:80163278
### 淘宝:https://shop329476445.taobao.com
### 微信:https://shop329476445.taobao.com
### 或者发送电子邮件到devgis@qq.com

## 8.	覺得不錯 可以打個賞
### 微信
---
![微信收款](zfb.jpg)

### 支付宝
---
![支付宝收款](wx.jpg)
---
