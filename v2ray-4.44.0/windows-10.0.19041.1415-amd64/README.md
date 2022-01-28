配置文件夹为 `C:\app\config`，未声明 volume，挂载后替换为用户的多文件配置即可

启动示例：`docker run --isolation=process --detach --name v2ray --publish 1080:1080 --publish 3128:3128 --volume v2ray-config:c:\app\config ragnaroks/windows-image-19044:v2ray-4.44.0`