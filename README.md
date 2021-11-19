# nvjdc
安装教程

## 提示
[TG 频道](https://t.me/joinchat/Yv6TIsjs8QUxM2I9) 

[TG 群组](https://t.me/joinchat/drvRtM-bqjYzOTE9) 

由于我自己的环境是centos x86，arm并未测试

## 支持的架构
![image](https://user-images.githubusercontent.com/87279659/137679751-7c2e901f-0429-4c5c-a6d2-120b8848048f.png)
查看地址:https://github.com/dotnet/core/blob/main/release-notes/5.0/5.0-supported-os.md


## 安装教程
1 执行命令

```
yum install wget unzip -y
```

2创建一个目录放配置以及chromium

```
mkdir nolanjdc && cd nolanjdc
```

3下载config.json 配置文件 并且修改自己的配置 不能缺少

```
wget -O Config.json  https://raw.githubusercontent.com/fai1988/nvjdc/main/Config.json
```
国内请使用
 ```
wget -O Config.json   https://ghproxy.com/https://raw.githubusercontent.com/fai1988/nvjdc/main/Config.json
```

4 创建chromium文件夹并进入

```
mkdir -p  .local-chromium/Linux-884014 && cd .local-chromium/Linux-884014
```

5下载 chromium 

```
wget https://mirrors.huaweicloud.com/chromium-browser-snapshots/Linux_x64/884014/chrome-linux.zip && unzip chrome-linux.zip
```

6删除刚刚下载的压缩包 

```
rm  -f chrome-linux.zip
```

7 回到刚刚创建的目录

```
cd  /root/nolanjdc
```

8拉镜像

```
sudo docker pull nolanjdc/nvjdc:latest
```

9启动镜像

```
sudo docker run --name nolanjdc -p 5701:80 -d -v  "$(pwd)"/Config.json:/app/Config/Config.json:ro \
-v  "$(pwd)"/.local-chromium:/app/.local-chromium \
-it --privileged=true nolanjdc/nvjdc:latest
```

10查看 日志 

```
docker logs -f nolanjdc 

```

  

出现 NETJDC  started 即可 



## 更新

删除容器
```
docker rm -f nolanjdc 
```
删除镜像
```
docker rmi -f nolanjdc/nvjdc
```

进入你以前下载过 浏览器 和JSON配置的文件夹中 
如原来在 root 下 nolanjdc 文件夹中 下载的配置与浏览器
```
cd /root/nolanjdc 
``` 
然后重复后续步骤即可
## 注意事项

容器启动后第一次获取验证码的时候可能卡住刷新一下即可

Config.json 是配置文件 可以热更新 修改后不用重启容器



# nvjdcforwin


# 第一步安装ASP.NET Core Runtime 5.0.12

安装地址:https://dotnet.microsoft.com/download/dotnet/5.0
下载之后无脑下一步

#下载WEB压缩包  

下载地址：https://www.lanzouw.com/iPZFDwczhef

在仓库里解压压缩修改配置文件夹中的Config.json

# 下载浏览器

在解压的WEB文件夹中根目录创建一个.local-chromium\Win64-884014\chrome-win 这些文件夹

下载浏览器地址:https://mirrors.huaweicloud.com/chromium-browser-snapshots/

根据自己情况选择 884014 版本的浏览器 有WIN win64的 下载完成解压到.local-chromium\Win64-884014\里


# 最后启动 
 管理员打开CMD CD到web文件夹中  输入 dotnet NETJDC.dll --urls=http://*:5000
