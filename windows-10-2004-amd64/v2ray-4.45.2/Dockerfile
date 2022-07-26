#PRE download https://github.com/v2fly/v2ray-core/releases/download/v4.45.2/v2ray-windows-64.zip
#PRE unarchive v2ray-windows-64.zip tempdir
#PRE copy-file tempdir\\geoip.dat app\\
#PRE copy-file tempdir\\geoip-only-cn-private.dat app\\
#PRE copy-file tempdir\\geosite.dat app\\
#PRE copy-file tempdir\\v2ctl.exe app\\
#PRE copy-file tempdir\\v2ray.exe app\\

FROM mcr.microsoft.com/windows/nanoserver:2004-amd64
LABEL windows-version=2004-amd64 v2ray-version=4.45.2
ENV V2RAY_CONF_GEOLOADER=memconservative
COPY app C:\\app
WORKDIR C:\\app
USER ContainerUser
ENTRYPOINT ["v2ray.exe"]
CMD ["-confdir","config"]