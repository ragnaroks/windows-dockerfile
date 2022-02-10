### ragnaroks/windows-10.0.17763.2458-amd64:mysql-5.7.36
> 使用前必读  
> 由于 [WCOW 的 BUG](https://www.ragnaroks.site/posts/45/)，使用此镜像需要手动处理 volume  

### 提醒
- 配置文件夹为 `C:\app\config`，未声明 volume
- 数据文件夹为 `C:\app\data`，未声明 volume

### 部署步骤
- 执行 `docker volume create mysql-config` 创建数据卷
- 执行 `docker volume create mysql-data` 创建数据卷
- 在 mysql-config 数据卷中放入配置文件 mysqld.ini
- 执行 `docker run --isolation process --name mysql-5.7.36-temp --detach --publish 6800:6800 --volume mysql-config:c:\app\config:ro --volume mysql-data:c:\app\data ragnaroks/windows-10.0.17763.2458-amd64:mysql-5.7.36` 创建一个初始化专用容器（此时运行的是 cmd.exe）
- 附加进容器后执行 `C:\app\bin\mysqld.exe --initialize-insecure` 初始化数据库
- 附加进容器后执行 `C:\app\bin\mysqld.exe` 启动服务
- （可选）附加进容器后执行 `C:\app\bin\mysql.exe -u root` 进入本机管理员会话
  - 执行 `mysql> CREATE USER 'root'@'%' IDENTIFIED BY 'root';` 创建任意来源的用户，用户名和密码都是 **root**
  - 执行 `mysql> GRANT ALL ON *.* TO 'root'@'%';` 给此用户授权
  - 执行 `mysql> FLUSH PRIVILEGES;` 刷新权限
- 测试容器运行正常后，停止并移除此容器，**注意不要移除数据卷**
- 执行 `docker run --isolation process --name mysql-5.7.36 --detach --publish 6800:6800 --volume mysql-config:c:\app\config:ro --volume mysql-data:c:\app\data ragnaroks/windows-10.0.17763.2458-amd64:mysql-5.7.36 c:\app\bin\mysqld.exe` 正式部署

### 默认 c:\app\my.ini
```ini
[mysqldump]
quick
quote-names
max-allowed-packet=16M

[mysqld]
#skip-host-cache
#skip-name-resolve
port=3306
basedir=c:\app
datadir=c:\app\data
server-id=1
explicit-defaults-for-timestamp=on
general_log=ON
general_log_file=app.log
log-syslog=OFF
log_error=app-error.log
log_bin=ON
log_bin_basename=app-bin
log_bin_index=app-bin.index
slow_query_log_file=app.slow
slow_query_log=1
long_query_time=3
expire_logs_days=7
max_binlog_size=1G
binlog_cache_size=4M

!includedir c:\app\config
```

### 默认 c:\app\config\mysqld.ini
```ini
[mysqld]
character_set_server=utf8mb4
sql_mode=ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION
open_files_limit=16384
max_connect_errors=1024
thread_cache_size=8
max_connections=4096
back_log=64
query_cache_min_res_unit=32K
query_cache_wlock_invalidate=ON
query_cache_size=16M
table_open_cache=1024
table_definition_cache=1024
tmp_table_size=4M
max_heap_table_size=4M
innodb_thread_concurrency=0
innodb_buffer_pool_size=1G
innodb_write_io_threads=16
innodb_log_buffer_size=8M
innodb_log_file_size=4M
innodb_flush_log_at_trx_commit=2
innodb_read_io_threads=16
join_buffer_size=128K
key_buffer_size=2M
sort_buffer_size=2M
read_buffer_size=128K
read_rnd_buffer_size=256K
thread_stack=256K
query_cache_limit=8M
query_cache_type=2
net_buffer_length=1M
lc_messages=zh_CN
lc_time_names=zh_CN
```