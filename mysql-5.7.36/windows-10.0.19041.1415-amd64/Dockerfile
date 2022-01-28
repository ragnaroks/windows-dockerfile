PRE download https://cdn.mysql.com/archives/mysql-5.7/mysql-5.7.36-winx64.zip
PRE unarchive mysql-5.7.36-winx64.zip app
PRE delete mysql-5.7.36-winx64.zip
PRE delete app\\include
PRE delete app\\lib
PRE mkfile app\\my.ini
PRE mkdir app\\config
PRE mkfile app\\config\\mysqld.ini
PRE mkdir app\\data

FROM mcr.microsoft.com/windows/nanoserver:10.0.19041.1415-amd64
LABEL windows-version=10.0.19041.1415-amd64 mysql-version=5.7.36
COPY app C:\\app
USER ContainerUser
WORKDIR C:\\app
#VOLUME C:\\app\\data C:\\app\\config
EXPOSE 3306
ENTRYPOINT ["cmd.exe"]