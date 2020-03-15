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

##在线下载Maven模块的方法

###获取整个管理单位树
```
maven clean install -Dmaven.repo.local=<some_foler>
```