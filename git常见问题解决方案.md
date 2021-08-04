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



# git 删除远程仓库的文件

远程厂库只能删除仓库，无法删除文件，因此，此问题的解决方案是：

第一步：git pull 远程仓库下来

```shell
git pull origin master  #我之前已标识origin 远程仓库“例如：git remote add origin [url]”
```

第二步：删除指定文件/文件夹

```shell
git rm --cached [file_name]  #删除文件名

git rm -r --cached [dir_name] #删除文件夹 -r 递归删除
```

第三步：git commit 暂存起来

```shell
git commit -m "delete [file_name]" #提交一次，并嵌入信息
```

第四步：git push  推文件到远程仓库

```shell
git push -u origin master  #push文件到仓库
```

