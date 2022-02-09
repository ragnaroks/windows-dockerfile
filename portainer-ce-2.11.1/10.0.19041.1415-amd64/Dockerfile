#PRE pull portainer/portainer-ce:windows2004-amd64-2.11.1
#PRE create-dir app
#PRE copy portainer/portainer-ce:windows2004-amd64-2.11.1\\.\\HardDisk1\\public app
#PRE copy portainer/portainer-ce:windows2004-amd64-2.11.1\\.\\HardDisk1\\storybook app
#PRE copy portainer/portainer-ce:windows2004-amd64-2.11.1\\.\\HardDisk1\\*.exe app
#PRE copy portainer/portainer-ce:windows2004-amd64-2.11.1\\.\\HardDisk1\\*.dll app

FROM mcr.microsoft.com/windows/nanoserver:10.0.19041.1415-amd64
LABEL portainer-version=2.11.1
COPY app C:\\app
USER ContainerAdministrator
EXPOSE 9000
ENV PATH=C:\\app\\mingit\\cmd;C:\\Windows\\system32;C:\\Windows;
WORKDIR C:\\app
VOLUME C:\\data
ENTRYPOINT ["portainer.exe"]