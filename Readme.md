<h1 align="center"> 免责声明 </h1>
<p align="center">
只面向海外华人用户且仅供科研学习之用，切勿用于其他用途
<br>
中国居民请自觉关闭本项目并24小时之内删掉与本项目相关的一切内容，否则出现一切问题，项目作者概不负责
</p>
<hr>

## 一、先说一下V2的os部署：
* 原始项目：yulahuyed/v2ray，docker file：yulahuyed/v2ray/dockerfile。已fork至v2ray-1。对应生成docker image：[b1nitp7iw/v2ray](https://hub.docker.com/r/b1nitp7iw/v2ray/)。**这个image里有酸酸的部署，还没学会用。**
* 关联项目：wangyi2005/v2ray，已经GEGE了。已fork，即本项目。master分支里dockerfile注释了。available分支里把dockerfile的注释符全部打开了，应该就可用。我就没有去生成image了。
* 热门项目：doudoubinga/openshift，从上面的项目来，不过也已经GEGE了，没了直接可用的image和CONFIG_JSON。点赞油管教程。

## 二、以下是doudoubing的说明：
```
v2ray 部署在 openshift starter
鉴于转载网友太多，甚至还发到了国内网站上宣传，为避免不必要麻烦，docker镜像已经删除，需要的请自行fork本 项目，然后照着这个视频 https://youtu.be/gImm4CfAnRs 自行部署镜像！ 2018/09/26
（fork于wangyi2005/v2ray修改前）
环境变量： CONFIG_JSON（配置）、
用notepad++将上述变量中 \r\n 替换为\n，变成一行，导入容器。
客户端： android Actinium、windows v2ray 可用同一个服务端。
[youtube频道](https://www.youtube.com/channel/UClceV39J1Z_9D4_mHkBZrMg)
```

## 三、我的实验报告
技术宅的尿性，这里讲一下最原始版（其实是因为已经有image）的使用方法。并不通俗易懂的。
* os建项目，点开选部署镜像。
* 镜像就是上面的原始image了，查找，部署。
    这点跟doudoubinga的视频不同，不用再单独传CONFIG变量。这个image里默认的CONFIG_JSON1、2已经配好，具体比较两个项目的dockerfile吧。
* pod开通后进配置页面，创建线路。【安全】-【安全的线路】，TLS默认【edge】，创建。返回配置页面右下角多了“路由链接”，创建好了打开为坏的请求说明成功了。
* 客户端上配也讲技巧，简单说下。
```
配置的主要依据和各版本的区别都源自于不同dockerfile里的CONFIG_JSON*
 首先，v2rayN上添加Vmess，BifrostV就是手动创建。
 地址是路由链接，注意不带https://。
 端口443。用户id就是UUID了。额外64.
 加密方式这里是没有的。doudoubing里是有的。
 传输协议是ws/websocket。
 底层传输是tls，BifrostV就是security TLS要选tls。
 done
```
