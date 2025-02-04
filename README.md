# **使用说明：**  
## 一、请先打开下面网站，一键生成ALLINONE部署命令：
## **[点击打开命令生成器](https://imgtool.v1.mk/allinone.html)**
### 设置自动更新ALLINONE，如果你使用Docker部署方式，在部署完成后，建议再配置watchtower自动监听allinone镜像更新，同步Docker-Hub仓库！！！注意，你需要先去生成器生成部署命令执行后再配置自动更新：
```
docker run -d --name watchtower --restart=always -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower allinone  --cleanup --interval 3600
```
## 二、详细使用方法
## **Gaoma和Itv以及Rptv聚合M3U获取：**
**声明：如果你是在公网服务器部署，不愿意开启聚合TV直播服务，在运行裸程序或者Docker时，加上参数 -tv=false 即可不开启直播服务（仅对gaoma、itv、rptv生效，migu走的是302重定向，没有代理流量），具体可[点击参考命令生成器](https://imgtool.v1.mk/allinone.html)**
```
http://你的IP:35455/tv.m3u
如果你的allinone服务被部署至服务器上，并且使用https域名反代了IP+端口，那么你的链接要变成：
https://你的反代域名/tv.m3u(?url=https://你的反代域名)   举个例子：https://www.feiyang.com/tv.m3u?url=https://www.feiyang.com
括号中为可选参数，用来方便替换列表前缀为https的，如果反代域名中含有特殊符号的，先去urlencode，如果反代后的域名依旧存在端口，那就把端口照样加上去，比如url=https://feiyang.com:12345，不加url参数默认是http协议
```
## **直播源格式化工具**
**[点击查看直播源格式化工具，将重复频道格式化处理](https://hub.docker.com/r/yuexuangu/allinone_format)**
## **BiliBili、虎牙、斗鱼、YY实时M3U获取：**
### BiliBili生活：
```
http://你的IP:35455/bililive.m3u
如果你的allinone服务被部署至服务器上，并且使用https域名反代了IP+端口，那么你的链接要变成：
https://你的反代域名/bililive.m3u(?url=https://你的反代域名)   举个例子：https://www.feiyang.com/bililive.m3u?url=https://www.feiyang.com
括号中为可选参数，用来方便替换列表前缀为https的，如果反代域名中含有特殊符号的，先去urlencode，如果反代后的域名依旧存在端口，那就把端口照样加上去，比如url=https://feiyang.com:12345，不加url参数默认是http协议
```
### 虎牙一起看：
```
http://你的IP:35455/huyayqk.m3u
如果你的allinone服务被部署至服务器上，并且使用https域名反代了IP+端口，那么你的链接要变成：
https://你的反代域名/huyayqk.m3u(?url=https://你的反代域名)   举个例子：https://www.feiyang.com/huyayqk.m3u?url=https://www.feiyang.com
括号中为可选参数，用来方便替换列表前缀为https的，如果反代域名中含有特殊符号的，先去urlencode，如果反代后的域名依旧存在端口，那就把端口照样加上去，比如url=https://feiyang.com:12345，不加url参数默认是http协议
```
### 斗鱼一起看：
```
http://你的IP:35455/douyuyqk.m3u
如果你的allinone服务被部署至服务器上，并且使用https域名反代了IP+端口，那么你的链接要变成：
https://你的反代域名/douyuyqk.m3u(?url=https://你的反代域名)   举个例子：https://www.feiyang.com/douyuyqk.m3u?url=https://www.feiyang.com
括号中为可选参数，用来方便替换列表前缀为https的，如果反代域名中含有特殊符号的，先去urlencode，如果反代后的域名依旧存在端口，那就把端口照样加上去，比如url=https://feiyang.com:12345，不加url参数默认是http协议
```
### YY轮播：
```
http://你的IP:35455/yylunbo.m3u
如果你的allinone服务被部署至服务器上，并且使用https域名反代了IP+端口，那么你的链接要变成：
https://你的反代域名/yylunbo.m3u(?url=https://你的反代域名)   举个例子：https://www.feiyang.com/yylunbo.m3u?url=https://www.feiyang.com
括号中为可选参数，用来方便替换列表前缀为https的，如果反代域名中含有特殊符号的，先去urlencode，如果反代后的域名依旧存在端口，那就把端口照样加上去，比如url=https://feiyang.com:12345，不加url参数默认是http协议
```
## **抖音：**
### 默认最高画质，浏览器打开并复制`(live.douyin.com/)xxxxxx`，只需要复制后面的xxxxx即可（可选flv和hls两种种流媒体传输方式，默认flv）：
```
http://你的IP:35455/douyin/xxxxx(?stream=hls)
```
## **斗鱼：**
### 1，可选m3u8和flv以及xs三种流媒体传输方式【`(www.douyu.com/)xxxxxx 或 (www.douyu.com/xx/xx?rid=)xxxxxx`，默认flv】：
```
http://你的IP:35455/douyu/xxxxx(?stream=flv)
```
## **BiliBili`(live.bilibili.com/)xxxxxx`：**
### 1，平台platform参数选择（默认web，如果有问题，可以切换h5平台）：
```
"flv"   => "FLV"
"hls"    => "M3U8"
```
### 2，线路line参数选择（默认线路二，如果卡顿/看不了，请切换线路一或者三，一般直播间只会提供两条线路，所以建议线路一/二之间切换）：
```
"first"  => "线路一"
"second" => "线路二"
"third"  => "线路三"
```
### 3，画质quality参数选择（默认原画，可以看什么画质去直播间看看，能选什么画质就能加什么参数，参数错误一定不能播放）：
```
"4" => "原画质"
"3" => "低画质"
```
### 4，最后的代理链接示例：
```
http://你的IP:35455/bilibili/xxxxxx(?platform=hls&line=first&quality=4)
```
## **虎牙`(huya.com/)xxxxxx`：**  
### 1，查看可用CDN：
```
http://你的IP:35455/huya/xxxxx?type=json
```
### 2，切换媒体类型（默认flv，可选flv、hls）： 
```
http://你的IP:35455/huya/xxxxx?media=hls
```
### 3，切换CDN（默认hwcdn，可选hycdn、alicdn、txcdn、hwcdn、hscdn、wscdn，具体可先访问1获取）：
```
http://你的IP:35455/huya/xxxxx?cdn=alicdn
```
### 4，最后的代理链接示例：
```
http://你的IP:35455/huya/xxxxx(?media=xxx&cdn=xxx)
```
## **YouTube:**
```
https://www.youtube.com/watch?v=cK4LemjoFd0
Rid: cK4LemjoFd0
http://你的IP:35455/youtube/cK4LemjoFd0(?quality=1080/720...)
```
## **YY（默认最高画质，参数为4）:**
```
https://www.yy.com/xxxx
http://你的IP:35455/yy/xxxx(?quality=1/2/3/4...)
```
## 更多平台后续会酌情添加
# 免责声明：本程序仅供学习交流，源码均搜集自互联网，禁止使用其谋取利益或者进行不正当行为，禁止在大陆自媒体平台分享本程序，否则本程序不背任何责任，如有侵权请联系，将会直接下架移除本程序！
