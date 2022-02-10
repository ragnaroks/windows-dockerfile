### ragnaroks/windows-10.0.19041.1415-amd64:v2ray-4.44.0
> 使用前必读  
> 由于 [WCOW 的 BUG](https://www.ragnaroks.site/posts/45/)，使用此镜像需要手动处理 volume  

### 提醒
- 配置文件夹为 `C:\app\config`，未声明 volume
- 已配置 V2RAY_CONF_GEOLOADER 环境变量为 memconservative，小内存机器可用

### 部署步骤
- 执行 `docker volume create v2ray-config` 创建数据卷
- 在 v2ray-config 数据卷中放入[多文件配置](https://www.v2fly.org/config/multiple_config.html)即可
- 执行 `docker run --isolation process --detach --name v2ray-4.44.0 --publish 1080:1080 --publish 3128:3128 --volume v2ray-config:c:\app\config:ro ragnaroks/windows-10.0.19041.1415-amd64:v2ray-4.44.0` 部署使用

### 默认 c:\app\config\01_log.json
```json
{
    "log": {
        "access": null,
        "error": null,
        "loglevel": "debug"
    }
}
```

### 默认 c:\app\config\02_api.json
```json
{
    "api": null
}
```

### 默认 c:\app\config\03_dns.json
```json
{
    "dns": null
}
```

### 默认 c:\app\config\04_policy.json
```json
{
    "levels": {
        "0": {
            "handshake": 4,
            "connIdle": 300,
            "uplinkOnly": 0,
            "downlinkOnly": 0,
            "statsUserUplink": false,
            "statsUserDownlink": false,
            "bufferSize": 10240
        }
    },
    "system": {
        "statsInboundUplink": false,
        "statsInboundDownlink": false,
        "statsOutboundUplink": false,
        "statsOutboundDownlink": false
    }
}
```

### 默认 c:\app\config\05_inbounds.json
```json
{
    "inbounds": [
        {
            "tag": "in-proxy-http",
            "protocol": "http",
            "listen": "0.0.0.0",
            "port": 3128,
            "settings": {
                "timeout": 60,
                "allowTransparent": false,
                "userLevel": 0
            },
            "sniffing": {
                "enabled": false,
                "destOverride": [
                    "http",
                    "tls"
                ]
            }
        },
        {
            "tag": "in-proxy-socks5",
            "protocol": "socks",
            "listen": "0.0.0.0",
            "port": 1080,
            "settings": {
                "auth": "noauth",
                "udp": true
            }
        }
    ]
}
```

### 默认 c:\app\config\06_outbounds.json
```json
{
    "outbounds": [
        {
            "tag": "out-direct",
            "protocol": "freedom",
            "settings": {
                "domainStrategy": "AsIs"
            }
        },
        {
            "tag": "out-block",
            "protocol": "blackhole"
        }
    ]
}
```

### 默认 c:\app\config\07_routing.json
```json
{
    "routing": {
        "domainStrategy": "AsIs",
        "rules": [
            {
                "type": "field",
                "ip": ["geoip:private"],
                "outboundTag": "out-block"
            },
            {
                "type": "field",
                "inboundTag": ["in-proxy-socks5","in-proxy-http"],
                "outboundTag": "out-direct"
            }
        ]
    }
}
```

### 默认 c:\app\config\08_transport.json
```json
{
    "transport":null
}
```

### 默认 c:\app\config\09_stats.json
```json
{
    "stats":null
}
```

### 默认 c:\app\config\10_reverse.json
```json
{
    "reverse": null
}
```

### 默认 c:\app\config\11_transport.json
```json
{
    "transport":null
}
```

### 默认 c:\app\config\12_fakedns.json
```json
{
    "fakedns":[
        {
            "ipPool":"100.64.0.0/16",
            "poolSize":65535
        },
        {
            "ipPool":"FC00::/112",
            "poolSize":65535
        }
    ]
}
```

### 默认 c:\app\config\13_browserForwarder.json
```json
{
    "browserForwarder":null
}
```

### 默认 c:\app\config\14_observatory.json
```json
{
    "observatory":null
}
```