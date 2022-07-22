



```sh
#gcc安装，nginx源码编译需要
yum install gcc-c++

#PCRE pcre-devel 安装，nginx 的 http 模块使用 pcre 来解析正则表达式
yum install -y pcre pcre-devel

#zlib安装，nginx 使用zlib对http包的内容进行gzip
yum install -y zlib zlib-devel

#OpenSSL 安装，强大的安全套接字层密码库，nginx 不仅支持 http 协议，还支持 https（即在ssl协议上传输http）
yum install -y openssl openssl-devel

#下载版本号可根据目前官网最新稳定版自行调整
wget -c https://nginx.org/download/nginx-1.16.1.tar.gz

#根目录使用ls命令可以看到下载的nginx压缩包，然后解压
tar -zxvf nginx-1.16.1.tar.gz

#解压后进入目录
cd nginx-1.16.1

#使用默认配置
./configure

#编译安装
make
make install

#查找安装路径，默认都是这个路径
[root@VM_0_12_centos ~]# whereis nginx
nginx: /usr/local/nginx

#启动、停止nginx
cd /usr/local/nginx/sbin/
./nginx     #启动
./nginx -s stop  #停止，直接查找nginx进程id再使用kill命令强制杀掉进程
./nginx -s quit  #退出停止，等待nginx进程处理完任务再进行停止
./nginx -s reload  #重新加载配置文件，修改nginx.conf后使用该命令，新配置即可生效

#重启nginx，建议先停止，再启动
./nginx -s stop
./nginx

#查看nginx进程，如下返回，即为成功
[root@VM_0_12_centos ~]# ps aux|grep nginx
root      5984  0.0  0.0 112708   976 pts/1    R+   14:41   0:00 grep --color=auto nginx
root     18198  0.0  0.0  20552   612 ?        Ss   11:28   0:00 nginx: master process ./nginx
nobody   18199  0.0  0.0  23088  1632 ?        S    11:28   0:00 nginx: worker process
```

