---
title: ucloud基本使用
date: 2019-06-26 11:21:02
tags:
---
### 什么是对象储存？
对象存储（UFile）是为互联网应用提供非结构化文件存储的服务；相对于传统硬盘存储，对象存储具有存储无上限、支持高并发访问、成本更低等优势；解决业务架构的文件存储问题，有效降低海量文件的存储成本，支持热点数据的高并发访问，提升终端用户访问体验。  
核心概念：  
单地域空间管理   
单地域对象存储服务能够解决业务架构的文件存储问题，为用户上传的数据创建多份副本并实现跨机房存储。  

### 对象存储空间（Bucket） 
对象存储空间（简称存储空间）是文件的组织管理单位，一个文件必然位于某个空间中。空间名称全局唯一，且无法进行修改。 每个账号最多可以创建20个存储空间，存储空间内文件数量无限制，单个文件最大5TB。 用户可以将存储空间设置为公开或私有，以控制存储空间内文件的访问权限。

对象存储空间命名规范
     1.仅包含小写字母，数字和连字符（-）
     2.必须以小写字母或者数字开头 
     3.长度必须在6-63字节之间。

#### 文件（File） 
文件是存储空间的逻辑存储单元。对于每个账号，该账号里存放的每个文件都有唯一的一对存储空间（Bucket）与键（Key）作为标识。PUT方式上传文件大小最大为5 TB。

#### 文件名（Key） 
文件名是对应文件的名称，在存储空间中全局唯一，每个文件名在存储空间均标识了一个文件，写入文件时，用户可以自定义文件名。上传同样文件名的文件，会导致原文件名文件被覆盖。 使用者在下载文件时只需要知道下载出口的域名，而无需了解文件具体会被存放到哪个机房的哪个设备，也无需知道具体存放形式。只需在浏览器输入对应的URL访问即可

### 文件名命名规范
     1.使用UTF-8编码
     2.长度必须在1-1023字节之间
     3.可以“/”字符开头，但不允许出现“{}^[]<>\#\~\%”。

### cloud提供了命令行工具
     bucketmgr：用来操作bucket，增删改查
     filemgr：用来处理文件相关：上传、下载、删除等

ucloud提供了多语言的API
ucloud提供了基本的命令行工具和python api  
写了基本上传工具、下载工具，使用python api，调用非常方便  
```python
#基本设置
config.set_default(uploadsuffix='.hk.ufileos.com')
config.set_default(downloadsuffix='.ufile.ucloud.com.cn')
config.set_default(connection_timeout=60)
config.set_default(expires=60)
#日志设置

DATA = datetime.datetime.now().isocalendar()
BUCKETNAME = "%d-week-%d"%(DATA[0], DATA[1])
# print bucket_name
locallogname = '/mnt/proj/trash/log/tools/ste/%s.log'%BUCKETNAME #完整本地日志文件名
logger.set_log_file(locallogname)

public_key = 'SzA832cU69RahCifWwsChN0rFiv3aKIRd+2Ij+1/t9tXLVmjLhoPnw=='         #账户公私钥中的公钥
private_key = 'f3c0015184207cd89159236058c5f70abd2ca944'        #账户公私钥中的私钥
region = 'hk'
#关键的入口
bucketmanager = bucketmanager.BucketManager(public_key, private_key)
filemanager = filemanager.FileManager(public_key, private_key)
multipartuploadufile_handler = multipartuploadufile.MultipartUploadUFile(public_key, private_key)
#获取指定bucket下所有的文件列表，默认限制是20个
ret, resp = self.bucketmanager.getfilelist(self.bucket, limit=200)
```
