DVB_VOD
=======

数字电视机顶盒改造成本地流媒体播放系统

##实现原理##

家里的数字电视机顶盒里面装了iPanel v3.0系统，具有VOD点播功能。iPanel可以解析一般网页内容，还提供了几个Javascript API进行VOD流媒体点播操作。如果连上网络，它会自动读取固定网页URL，所以只要劫持DNS并替换成自己的网页就可以进行破解。

##具体操作##

1. 抓包获得机顶盒的访问的URL，在本地搭建DNS缓存服务器dnsmasq，在dnsmasq把那个URL映射到本地。
2. 本地搭建Apache服务器。
3. 本地搭建流媒体服务器，我用的是开源的live555或用vlc。

##TODO##

现在界面实现完毕，播放rtsp流媒体不行，这方面也没有相关文档，进展缓慢，我用的是如下代码播放rtsp，但可耻的失败了-_-!!!。

    var url = "rtsp://192.168.1.111:8554/next.mp3";
    media.AV.open(url, "VOD");
