#PRE download https://github.com/v2fly/v2ray-core/releases/download/v4.44.0/v2ray-windows-64.zip
#PRE unarchive v2ray-windows-64.zip app
#PRE delete-file v2ray-windows-64.zip
#PRE delete-file app\\*.json
#PRE delete-file app\\wv2ray.exe

FROM mcr.microsoft.com/windows/nanoserver:10.0.17763.2458-amd64
LABEL v2ray-version=4.44.0
COPY app c:\\app
USER ContainerUser
ENV V2RAY_CONF_GEOLOADER=memconservative
WORKDIR c:\\app
ENTRYPOINT ["v2ray.exe"]
CMD ["-confdir","config"]