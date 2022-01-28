### ragnaroks/openj9-jre-17.0.1:10.0.19041.1415-amd64

### 提醒
- 默认 ENTRYPOINT 为 java.exe，默认 CMD 为 --version，即默认参数下容器会输出版本号后立刻终止
- 数据文件夹为 `C:\app\data`，未声明 volume

### 部署步骤
- 执行 `docker volume create my-java-app` 创建数据卷
- 执行 `docker run --isolation process --detach --name openj9-jre-17.0.1 --volume my-java-app:c:\app ragnaroks/openj9-jre-17.0.1:10.0.19041.1415-amd64 --jar c:\app\main.jar` 部署