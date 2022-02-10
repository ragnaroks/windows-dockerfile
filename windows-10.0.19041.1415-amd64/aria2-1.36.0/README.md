### ragnaroks/windows-10.0.19041.1415-amd64:aria2-1.36.0
> 使用前必读  
> 由于 [WCOW 的 BUG](https://www.ragnaroks.site/posts/45/)，使用此镜像需要手动处理 volume  

### 提醒
- 配置文件夹为 `C:\app\config`，未声明 volume，无特别需求则无需挂载，默认 rpc-secret 为 `https://github.com/aria2/aria2`，默认 rpc-port 为 `6800`
- 配置文件夹中也会存放会话文件，不可设置为只读
- 存储文件夹为 `C:\app\download`，已声明 volume，可自行挂载或绑定到目录

### 部署步骤
- 执行 `docker volume create aria2-config` 创建数据卷
- （可选）执行 `docker volume create aria2-download` 创建数据卷
- 在 aria2-config 数据卷中放入配置文件 aria2c.conf
- 执行 `docker run --isolation process --detach --name aria2 --publish 6800:6800 --volume aria2-download:c:\app\download --volume aria2-config:c:\app\config ragnaroks/windows-10.0.19041.1415-amd64:aria2-1.36.0` 正式部署

### 默认 c:\app\config\aria2.conf
```ini
### 基本设置 ###
#配置文件路径
#conf-path=
#下载路径, 默认为当前启动位置[必改]
dir=C:\app\download\
#日志文件路径，默认输出到控制台
log=-
#最大同时下载数(任务数),建议:3
max-concurrent-downloads=3
#检查完整性
check-integrity=true
#断点续传
continue=true

### HTTP/FTP/SFTP 设置 ###
#代理服务器
#all-proxy=[http://][USER:PASSWORD@]HOST[:PORT]
#代理服务器用户名
#all-proxy-user=username
#代理服务器密码
#all-proxy-passwd=password
#连接超时时间
#connect-timeout=60
#模拟运行
dry-run=false
#最小速度限制,低于此速度的链接将被关闭
lowest-speed-limit=16K
#单服务器最大连接数
max-connection-per-server=8
#文件未找到重试次数
max-file-not-found=1
#最大尝试次数
max-tries=3
#最小文件分片大小
min-split-size=16M
#.netrc 文件路径
#netrc-path=
#禁用 netrc
no-netrc=true
#不使用代理服务器列表
#no-proxy=192.168.0.0/16,12.34.56.78,hostname,example.com
#代理服务器请求方法,get/tunnel
proxy-method=tunnel
#获取服务器文件时间
remote-time=false
#URI 复用
reuse-uri=true
#重试等待时间,单位秒
retry-wait=3
#服务器状态保存文件
#server-stat-of=
#服务器状态超时
#server-stat-timeout=
#单任务连接数
split=4
#分片选择算法
#stream-piece-selector=
#超时时间
#timeout=60
#URI 选择算法
#uri-selector=

### HTTP 设置 ###
#检查证书
check-certificate=false
#支持 GZip
http-accept-gzip=true
#认证质询
#http-auth-challenge=
#禁用缓存
#http-no-cache=
#HTTP 默认用户名
#http-user=username
#HTTP 默认密码
#http-passwd=passwoord
#HTTP 代理服务器
#http-proxy=
#HTTP 代理服务器用户名
#http-proxy-user=
#HTTP 代理服务器密码
#http-proxy-passwd=
#HTTPS 代理服务器
#https-proxy=
#HTTPS 代理服务器用户名
#https-proxy-user=
#HTTPS 代理服务器密码
#https-proxy-passwd=
#请求来源
referer=*
#启用持久连接
enable-http-keep-alive=true
#启用 HTTP 管线化
enable-http-pipelining=true
#自定义请求头
#header=header1:value1\nheader2:value2\nheader3:value3
#Cookies 保存路径
#save-cookies=
#启用 HEAD 方法
use-head=true
#自定义 User Agent
user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/84.0.4147.105 Safari/537.36

### FTP/SFTP 设置 ####
#FTP 默认用户名
#ftp-user=
#FTP 默认密码
#ftp-passwd=
#被动模式
#ftp-pasv=true
#FTP 代理服务器
#ftp-proxy=
#FTP 代理服务器用户名
#ftp-proxy-user=
#FTP 代理服务器密码
#ftp-proxy-passwd=
#传输类型
#ftp-type=
#连接复用
#ftp-reuse-connection=true
#SSH 公钥校验和
#ssh-host-key-md=

### BitTorrent 设置 ####
#分离仅做种任务
#bt-detach-seed-only=
#启用哈希检查完成事件
bt-enable-hook-after-hash-check=false
#启用本地节点发现  (LPD)
#bt-enable-lpd=true
#BT 排除服务器地址
#bt-exclude-tracker=
#外部 IP 地址
#bt-external-ip=
#强制加密
#bt-force-encryption=false
#做种前检查文件哈希
bt-hash-check-seed=true
#加载已保存的元数据文件
bt-load-saved-metadata=true
#最多打开文件数
bt-max-open-files=4096
#最大连接节点数
bt-max-peers=4096
#仅下载种子文件
#bt-metadata-only=false
#最低加密级别
#bt-min-crypto-level=
#优先下载
#bt-prioritize-piece=
#删除未选择的文件
#bt-remove-unselected-file=
#需要加密
#bt-require-crypto=
#期望下载速度
bt-request-peer-speed-limit=128K
#保存种子文件
#bt-save-metadata=false
#不检查已经下载的文件
#bt-seed-unverified=false
#无速度时自动停止时间
#bt-stop-timeout=
#BT 服务器地址
bt-tracker=
#BT 服务器连接超时时间
#bt-tracker-connect-timeout=
#BT 服务器连接间隔时间
#bt-tracker-interval=
#BT 服务器超时时间
#bt-tracker-timeout=
#DHT (IPv4) 文件
dht-file-path=C:\app\config\dht.dat
#DHT (IPv6) 文件
dht-file-path6=C:\app\config\dht6.dat
#DHT 监听端口
#dht-listen-port=
#DHT 消息超时时间
#dht-message-timeout=
#启用 DHT (IPv4)
enable-dht=true
#启用 DHT (IPv6)
enable-dht6=true
#启用节点交换
#enable-peer-exchange=true
#下载种子中的文件
#follow-torrent=true
#监听端口
#listen-port=
#全局最大上传速度
max-overall-upload-limit=1
#最大上传速度
max-upload-limit=1
#节点 ID 前缀
peer-id-prefix=-TR133X-
#Peer Agent
#peer-agent=
#最小分享率
seed-ratio=0.0001
#最小做种时间
seed-time=0

### Metalink 设置 ###
#下载 Metalink 中的文件
#follow-metalink=true
#基础 URI
#metalink-base-uri=
#语言
#metalink-language=
#首选服务器位置
#metalink-location=us,cn,hk
#操作系统
#metalink-os=
#版本号
#metalink-version=
#首选使用协议
#metalink-preferred-protocol=
#仅使用唯一协议
#metalink-enable-unique-protocol=

### RPC 设置 ###
#启用 JSON-RPC/XML-RPC 服务器
enable-rpc=true
#种子文件下载完后暂停
#pause-metadata=false
#接受所有远程请求
rpc-allow-origin-all=true
#在所有网卡上监听
rpc-listen-all=true
#监听端口
rpc-listen-port=6800
#最大请求大小
rpc-max-request-size=8K
#保存上传的种子文件
#rpc-save-upload-metadata=true
#启用 SSL/TLS
rpc-secure=false
#token验证
rpc-secret=https://github.com/aria2/aria2

### 高级设置 ###
#允许覆盖
#allow-overwrite=false
#允许分片大小变化
#allow-piece-length-change=false
#始终断点续传
#always-resume=true
#异步 DNS，如果启用此项则代理配置失效
#async-dns=true
#文件自动重命名
#auto-file-renaming=true
#自动保存间隔,单位秒
auto-save-interval=30
#条件下载
#conditional-get=false
#控制台日志级别
#console-log-level=
#使用 UTF-8 处理 Content-Disposition
#content-disposition-default-utf8=false
#启用后台进程
#daemon=false
#延迟加载
#deferred-input=false
#禁用 IPv6
#disable-ipv6=false
#磁盘缓存
disk-cache=64M
#下载结果
#download-result=
#DSCP
#dscp=46
#最多打开的文件描述符
#rlimit-nofile=
#终端输出使用颜色
#enable-color=
#启用 MMap
#enable-mmap=
#事件轮询方法
#event-poll=
#文件分配方法
file-allocation=falloc
#强制保存
#force-save=false
#保存未找到的文件
#save-not-found=false
#仅哈希检查
#hash-check-only=
#控制台可读输出
human-readable=true
#保留未完成的任务
#keep-unfinished-download-result=
#最多下载结果
#max-download-result=
#MMap 最大限制
#max-mmap-limit=
#最大断点续传尝试次数
#max-resume-failure-tries=0
#最低 TLS 版本
#min-tls-version=
#日志级别
#log-level=
#优化并发下载
optimize-concurrent-downloads=true
#文件分片大小
piece-length=4M
#显示控制台输出
#show-console-readout=
#下载摘要输出间隔,单位秒
#summary-interval=60
#全局最大下载速度
#max-overall-download-limit=0
#最大下载速度
#max-download-limit=0
#禁用配置文件
#no-conf=false
#文件分配限制
no-file-allocation-limit=64M
#启用参数化 URI 支持
#parameterized-uri=false
#禁用控制台输出
#quiet=false
#实时数据块验证
#realtime-chunk-checksum=true
#删除控制文件
#remove-control-file=false
#状态保存文件
save-session=C:\app\config\aria2.session
#保存状态间隔,单位秒
save-session-interval=30
#Socket 接收缓冲区大小
#socket-recv-buffer-size=
#自动关闭时间
#stop=
#缩短控制台输出内容
#truncate-console-readout=
```