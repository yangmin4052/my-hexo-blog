---
title: Linux(centos6.5)下Nginx的安装步骤
date: 2018-04-26 14:28:28
tags:
---

* 注：root 环境下安装，我用的是虚拟机 VMware，安装的 centos6.5

## 第一步.进入下载目录，比如进入 usr/local/src，可自定义，执行一下命令：

```
cd usr/local/src
```

## 第二步.下载下面 5 个程序

### 1. 下载 openssl

```
wget http://www.openssl.org/source/openssl-fips-2.0.10.tar.gz
```

### 2. 下载 pcre（按照步骤好像也没装上）

```
wget ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.40.tar.gz
```

### 3. 下载 purge 模块（用于删除 Nginx 缓存，这个模块我没有下载，也没有安装）

```
wget http://labs.frickle.com/files/ngx_cache_purge-2.1.tar.gz
```

### 4. 下载 zlib（按照步骤好像也没装上）

```
wget http://zlib.net/zlib-1.2.11.tar.gz
```

### 5. 下载 nginx

```
wget http://nginx.org/download/nginx-1.10.2.tar.gz
```

## 第三步.安装

### 1. 如果安装了 c++的环境就可跳过，如未安装，执行以下命令：

```
yum install gcc-c++
```

（点击 y 即可），安装结尾显示 complete,即代表安装完成。

### 2. 安装 openssl

### (1). 解压 openssl 的压缩包

```
tar -zxvf openssl-fips-2.0.10.tar.gz
```

### (2). 打开解压后的文件夹

```
cd openssl-fips-2.0.10
```

### (3). 按照默认配置执行安装程序

```
./config && make && make install
```

### (4). 返回 usr/local/src 目录

```
cd ..
```

### 3. 安装 pcre（我没有安装成功）

### (1). 解压 pcre 的压缩包

```
tar -zxvf openssl-fips-2.0.10.tar.gz
```

### (2). 打开解压后的文件夹

```
cd pcre-8.40
```

### (3). 按照默认配置执行安装程序

```
./configure && make && make install
```

### (4). 返回 usr/local/src 目录

```
cd ..
```

### 4. 安装 purge（我没有安装）

### (1). 解压 zlib 的压缩包

```
tar -zxvf zlib-1.2.11.tar.gz
```

### 5. 安装 zlib（我没有安装成功）

### (1). 解压 zlib 的压缩包

```
tar -zxvf zlib-1.2.11.tar.gz
```

### (2). 打开解压后的文件夹

```
cd zlib-1.2.11
```

### (3). 按照默认配置执行安装程序

```
./configure && make && make install
```

### (4). 返回 usr/local/src 目录

```
cd ..
```

### 5. 安装 nginx

### (1). 解压 zlib 的压缩包

```
tar zxvf nginx-1.10.2.tar.gz
```

### (2). 打开解压后的文件夹

```
cd nginx-1.10.2
```

### (3). 按照默认配置安装

```
./configure && make && make install
```

### (4). 返回 usr/local/src 目录

```
cd ..
```

## 第四步.启动 nginx

### 1. 查看 nginx 安装的地址（whereis），执行以下命令：

```
whereis nginx
```

结果显示：

```
/usr/local/nginx
```

### 2. 进入目录启动

```
cd /usr/local/nginx/
```

### 3. 执行以下命令启动 nginx

```
/usr/local/nginx/sbin/nginx
```

* 一般这个时候会报错，不要慌张！！！，错误信息是不是像这样

```
错误信息：error while loading shared libraries:libpcre.so.1.......
```

此时，执行以下命令，找一下 libpcre.so.1：

```
whereis libpcre.so.1
```

结果显示：

```
libpcre.so: /lib64/libpcre.so.0 /usr/local/lib/libpcre.so.1 /usr/local/lib/libpcre.so
```

有文章说执行一下下面这条命令就好，就是这篇[Nginx 详细的安装教程（linux）](https://blog.csdn.net/u013641234/article/details/73838472)

```
ln -s /usr/local/lib/libpcre.so.1 /lib64
```

但我发现没用，于是我执行的是（这条命令是添加了软链接）

```
ln -s /usr/local/lib/libpcre.so.1 /lib
```

然后执行以下命令启动 nginx

```
/usr/local/nginx/sbin/nginx
```

现在我们查看下进程，执行以下命令

```
ps -aux | grep nginx
```

结果显示：

```
Warning: bad syntax, perhaps a bogus '-'? See /usr/share/doc/procps-3.2.8/FAQ
root      12007  0.0  0.0  20296   628 ?        Ss   13:28   0:00 nginx: master process sbin/nginx
nobody    12008  0.0  0.1  20716  1220 ?        S    13:28   0:00 nginx: worker process
root      12010  0.0  0.0 103244   836 pts/0    S+   13:29   0:00 grep nginx
```

棒极了，nginx 已经启动，我们测试一下，执行以下命令

```
curl localhost
```

结果显示：

```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

很好，但是你发现在你 windows 电脑的 chrome 浏览器竟然还是没有办法访问虚拟机的 ip，你可能没有关掉防火墙，执行以下命令

```
service iptables status
```

结果显示：

```
表格：filter
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination
1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
2    ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0
3    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
4    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:22
5    REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination
1    REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-prohibited

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination
```

果然如此，执行一下以下命令关闭防火墙

```
service iptables stop
```

结果显示：

```
iptables：将链设置为政策 ACCEPT：filter                    [确定]
iptables：清除防火墙规则：                                 [确定]
iptables：正在卸载模块：                                   [确定]
```

刷新一下 chrome 浏览器，浏览器出现以下内容

```
Welcome to nginx!
If you see this page, the nginx web server is successfully installed and working. Further configuration is required.

For online documentation and support please refer to nginx.org.
Commercial support is available at nginx.com.

Thank you for using nginx.
```

好的，搞定了，关于 nginx 的配置，以后再说。
