#Maven Repository私服的搭建

##下载JRE和Tomcat替换目录下相应的文件夹

###配置Tomcat

#### 修改服务器端口号
- ${TOMCAT_HOME}/conf/server.xml
```
port="8080"
```

#### 配置虚拟目录
- ${TOMCAT_HOME}/conf/Catalina/localhost路径下
```
<?xml version="1.0" encoding="UTF-8"?>
<Context antiJARLocking="true" docBase="${SERVER_HOME}/RepoData/maven" path="/maven"/>
```

#### 配置浏览器中以文件目录的形式展示
- ${TOMCAT_HOME}/conf/web.xml
```
<servlet>
        <servlet-name>default</servlet-name>
        <servlet-class>org.apache.catalina.servlets.DefaultServlet</servlet-class>
        <init-param>
            <param-name>debug</param-name>
            <param-value>0</param-value>
        </init-param>
        <init-param>
            <param-name>listings</param-name>
            <param-value>true</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
    </servlet>
```

##在线下载Maven模块的方法

###获取整个管理单位树
```
maven clean install -Dmaven.repo.local=<some_foler>
```