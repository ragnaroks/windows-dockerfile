### ragnaroks/portainer-ce-2.11.1:10.0.19041.1415-amd64

### 提醒
- 数据文件夹为 `C:\data`，已声明 volume

### 部署步骤
- 执行 `docker volume create portainer-data` 创建数据卷
- 执行 `docker run --isolation process --detach --name portainer-ce-2.11.1 --publish 9000:9000 --volume portainer-data:c:\data --volume \\.\pipe\docker_engine:\\.\pipe\docker_engine ragnaroks/portainer-ce-2.11.1:10.0.19041.1415-amd64` 部署
