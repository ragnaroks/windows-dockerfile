#PRE download https://github.com/aria2/aria2/releases/download/release-1.36.0/aria2-1.36.0-aarch64-linux-android-build1.zip
#PRE unarchive aria2-1.36.0-aarch64-linux-android-build1.zip app
#PRE delete-file aria2-1.36.0-aarch64-linux-android-build1.zip

FROM mcr.microsoft.com/windows/nanoserver:10.0.19041.1415-amd64
LABEL windows-version=10.0.19041.1415-amd64 aria2-version=1.36.0
COPY app C:\\app
USER ContainerUser
WORKDIR C:\\app
VOLUME C:\\app\\download
EXPOSE 6800
ENTRYPOINT ["aria2c.exe"]
CMD ["--conf-path","C:\\app\\config\\aria2c.conf"]