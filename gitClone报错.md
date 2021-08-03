# git clone报错

```shell
$ git clone https://github.com/Rico-Lucky/TestOfGo.git
Cloning into 'TestOfGo'...
fatal: unable to access 'https://github.com/Rico-Lucky/TestOfGo.git/': OpenSSL SSL_read: SSL_ERROR_SYSCALL, errno 10054

```

解决办法

**一、Git限制了推送数据的大小导致的错误。**

```shell
#重新设置通信缓存的大小，再git clone项目
git config --global http.postBuffer 524288000
```

二、GitHub.com无法访问，连接超时

```shell
#在cmd窗口中，尝试ping一下百度
ping www.baidu.com
#再ping一下github.com
ping github.com

```

若ping不通，怀疑是DNS无法解析导致的

三、解决错误

打开C:\Windows\System32\drivers\etc\hosts，

确实没有github.com的解析 
在文件末尾添加如下内容，并保存：

192.30.255.112  github.com git 
185.31.16.184 github.global.ssl.fastly.net 

重启cmd窗口，继续ping一下github.com



四

```shell
git clone https://github.com/xxx.git

提示下载失败,

可以尝试把https://换成 git://

git clone git://github.com/xxx.git
```



