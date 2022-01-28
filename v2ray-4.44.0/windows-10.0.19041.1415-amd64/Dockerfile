#PRE download https://github.com/v2fly/v2ray-core/releases/download/v4.44.0/v2ray-windows-64.zip
#PRE unarchive v2ray-windows-64.zip app
#PRE delete v2ray-windows-64.zip
#PRE delete app\\*.json
#PRE delete app\\wv2ray.exe

FROM mcr.microsoft.com/windows/nanoserver:10.0.19041.1415-amd64
LABEL windows-version=10.0.19041.1415-amd64 v2ray-version=4.44.0
COPY app C:\\app
USER ContainerUser
ENV V2RAY_CONF_GEOLOADER=memconservative
WORKDIR C:\\app
ENTRYPOINT ["v2ray.exe"]
CMD ["-confdir","config"]