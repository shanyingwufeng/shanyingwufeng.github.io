---
title: CentOS7 安装配置 Java、Tomcat、Nginx
date: 2020-07-14 00:50:32
categories:
- CentOS7
tags:
- study
---

# 安装配置 Java

1、检查 CentOS7 是否安装了其它版本的 JDK，执行命令

```
rpm -qa|grep java
```

如果没有安装，则官网下载 jdk，地址为：

[JDK 下载地址](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)

下载 JDK 需要 Oracle 账号：

账号：2696671285@qq.com

密码：Oracle123

<!-- more -->

2、CentOS7 中切换到 /usr/local 目录并通过 ftp 工具将下载的 JDK 包传入，执行命令解压

```
tar -zxvf jdk-8u251-linux-x64.tar.gz
```

将解压后的文件夹重命名为 java

```
mv jdk1.8.0_251 java
```

3、配置 java 环境变量，打开 /etc/profile 文件，添加以下内容

```
export JAVA_HOME=/usr/local/java
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib/dt.JAVA_HOME/lib/tools.jar:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:${PATH}
```

执行命令使配置生效

```
source /etc/profile
```

查看 java 是否配置成功

```
java
javac
java -version
```



# 安装配置 Tomcat

1、下载 Tomcat，选择 Tomcat8，下载地址为：

[Tomcat 下载地址](https://tomcat.apache.org/download-80.cgi)

2、页面找到 Core 中的 tar.gz 下载并通过 ftp 工具传到 /usr/local 中，然后解压

```
tar -zxvf apache-tomcat-8.5.57.tar.gz
```

将解压的文件夹重命名为 tomcat8

```
mv apache-tomcat-8.5.57 tomcat8
```

3、进入 tomcat 的 bin 目录启动 tomcat

```
cd /usr/local/tomcat8
./startup.sh
```

查看 tomcat 是否启动成功

```
ps -ef|grep tomcat
```

4、开放8080端口

```
# 开启8080端口并永久有效
firewall-cmd --zone-public --add-port=8080/tcp --permanent

# 重新加载防火墙
firewall-cmd --reload

# 查看已经开启的端口
firewall-cmd --list-port
```

5、本地浏览器访问 http://CentOSip:8080

出现 tomcat 的默认页面则访问成功。

# 安装配置 Nginx

1、yum 源中添加 Nginx

```
rpm -ivh http://nginx.org/packages/CentOS/7/noarch/RPMS/nginx-release-CentOS-7-0.el7.ngx.noarch.rpm
```

查看 yum 源

```
yum repolist
```

2、安装 Nginx

```
yum install -y nginx
```

3、配置 Nginx

```
# 设置开机启动
systemctl enable nginx

# 启动服务
systemctl start nginx

# 停止服务
systemctl stop nginx

# 重新加载（编辑配置文件后需要执行）
systemctl reload nginx
```

4、开启端口，默认80端口

```
firewall-cmd --zone=public --add-service=http --permanent
firewall-cmd --reload
firewall-cmd --list-service
```

5、如果出现访问403问题，则需要关闭 SELinux

```
# 查看状态（如果是 enabled 则需要关闭）
sestatus

# 彻底关闭
sed -i 's/SELINUX=enforcing/SELINUX=disabled/' /etc/selinux/config

# 重新启动 CentOS
reboot
```

