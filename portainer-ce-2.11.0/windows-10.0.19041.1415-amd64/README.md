无特别说明

启动示例：`docker run --isolation=process --detach --name portainer --publish 9000:9000 --volume \\.\pipe\docker_engine:\\.\pipe\docker_engine --volume portainer-data:c:\data ragnaroks/windows-image-19044:portainer-ce-2.11.0`