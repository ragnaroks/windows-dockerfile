#PRE download https://cdn.mysql.com/Downloads/MySQL-5.7/mysql-5.7.38-winx64.zip
#PRE unarchive mysql-5.7.38-winx64.zip app
#PRE delete-file mysql-5.7.38-winx64.zip
#PRE delete-dir app\\include
#PRE delete-dir app\\lib
#PRE delete-file app\\bin\\mysqld.pdb
#PRE create-file app\\my.ini
#PRE create-dir app\\config
#PRE create-file app\\config\\mysqld.ini
#PRE create-dir app\\data

FROM mcr.microsoft.com/windows/nanoserver:10.0.19041.1415-amd64
LABEL mysql-version=5.7.38
COPY app c:\\app
USER ContainerUser
WORKDIR c:\\app
VOLUME c:\\app\\data c:\\app\\config
EXPOSE 3306
ENTRYPOINT ["cmd.exe"]