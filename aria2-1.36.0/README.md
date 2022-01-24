配置文件夹为 `C:\app\config`，未声明 volume，无特别需求使用无需挂载此文件夹进行修改，默认 rpc-secret 为 `https://github.com/aria2/aria2`，默认 rpc-port 为 `6800`；配置文件夹中也会存放会话文件，不可设置为只读

存储文件夹为 `C:\app\download`，已声明 volume，可自行创建命名 volume 挂载

启动示例：`docker run --isolation=process --detach --name aria2 --publish 6800:6800 --volume aria2-download:C:\app\download --volume aria2-config:C:\app\config ragnaroks/windows-image-19044:aria2-1.36.0`