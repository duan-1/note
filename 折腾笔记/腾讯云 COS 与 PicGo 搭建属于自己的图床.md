# 腾讯云 COS 与 PicGo 搭建属于自己的图床

虽然说网上有许多的免费图床供我们选择，但是上传后的图片就是不是我们说了算，而是图床的服务商说了算；如果图床突然无法访问或是跑路，那么我们的图片就算是丢失了。所以搭建一个属于自己的图床极大的提高了数据的安全性。围绕 PicGo 可以有多种方法，如阿里云 OSS 、GitHub 、码云、又拍云等，大家可以根据自己的习惯自行选择。

## 写在前面

这篇博文以腾讯云 COS 为例子，腾讯云 COS 可能不是最优的选择，因为存储空间、外网流量、请求次数都是需要花钱。围绕 PicGo 可以有多种方法，如阿里云 OSS 、GitHub 、码云、又拍云等，大家可以根据自己的习惯自行选择。其次其实你不用 PicGo 也可以，腾讯开发了专门用来管理对象存储的客户端 —— [COSBrowser](https://cloud.tencent.com/document/product/436/11366) 。

## 准备工作

- 下载并安装好 [PicGo](https://github.com/Molunerfinn/PicGo/releases)（如未安装点击链接跳转至下载页）
- 创建腾讯云账号

## 创建存储桶

进入腾讯云控制台，在左上角的云产品中找到对象存储，然后创建存储桶。如下图所示：

![创建存储桶](https://img.secretbase.cn/img/20220322-creatbucket.png)

所属地域不同收费标准也不同，详细见 [腾讯云对象存储计费项](https://cloud.tencent.com/document/product/436/53859)，这里最重要的就是访问权限需要选择 `公共读私有写` ，然后确认完配置后就创建完成了。选配可能会有额外收费，大家根据自身需求选配。

## 设置 PicGo

### 1. 获取 APPID 、SecretId 和 SecretKey 。

在左边菜单栏点击 [`密钥管理`](https://console.cloud.tencent.com/cam/capi) 或是直接点击跳转，如下图所示。

![获取 APPID 、SecretId 和 SecretKey ](https://img.secretbase.cn/img/20220322-getparam.png)

### 2. 获取存储空间名和存储区域

打开存储桶列表，存储桶名称 `bucket-xxxx` 即为存储空间名，所属地域后面的 `xx-xxxx` 即为储存区域。

### 3. 将参数填入 PicGo 

没有明确的 v4 标志就说明版本为 v5，以及在本文发布时创建对象存储以及为 v5 版本。设置完成后，就拥有了自己的图床啦！如果想要了解指定存储路径和设定自定义域名请继续往后面看。

![](https://img.secretbase.cn/img/20220322-picgosetting.png)

## 拓展阅读

### 指定存储路径

如果你整个存储桶就是用来存储图片的，就可以不用指定存储路径。都是如果你像存储的不只是图片，并且想要分类存储，那么为了方便检索存储桶里面的资源，分路径存储是个最好的选择。

在存储桶列表中点击对应的存储桶，然后点击文件列表，就可以在 web 端管理存储桶里的文件了。点击新建文件夹，然后在 PicGo 填好指定存储路径即可。

### 设定自定义域名

在没有设定自定义域名前，观察一下图片的 url ；就会发现非常非常长，观感也比较差。那么我们就可以开一个二级域名专门用于映射图片，例如：img.xxx.com 。

首先先确保你的域名已经完成了备案，然后在域名控制台添加一条 `CNAME 解析` 到你的存储桶。记录值即为你的存储桶地址

![添加记录](https://img.secretbase.cn/img/20220322-creatCNAME.png)

然后再回到对象存储设置 `自定义 CDN 加速域名` ，添加你的自定义域名即可，建议去申请一个免费的 HTTPS 证书给自己的域名；最后在 PicGo 的自定义域名填上刚刚设置的域名。

![自定义域名](https://img.secretbase.cn/img/20220322-diydomain.png)

## 结语

这就是搭建自己图床的基本操作了，PicGo 和腾讯云 COS 还有许多玩法值得进一步探索，需要大家自己去发掘。

>参考资料：[配置手册 | PicGo](https://picgo.github.io/PicGo-Doc/zh/guide/config.html#%E8%85%BE%E8%AE%AF%E4%BA%91cos)