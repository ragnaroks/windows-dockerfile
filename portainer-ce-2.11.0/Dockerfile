PRE pull portainer/portainer-ce:2.11.0
PRE mkdir app
PRE copy portainer/portainer-ce:2.11.0\\.\\HardDisk1\\public app
PRE copy portainer/portainer-ce:2.11.0\\.\\HardDisk1\\storybook app
PRE copy portainer/portainer-ce:2.11.0\\.\\HardDisk1\\*.exe app
PRE copy portainer/portainer-ce:2.11.0\\.\\HardDisk1\\*.dll app

FROM mcr.microsoft.com/windows/nanoserver:10.0.19041.1415-amd64
LABEL windows-kernel=19044 portainer-version=2.11.0
COPY app C:\\app
USER ContainerAdministrator
WORKDIR C:\\app
ENV PATH=C:\\mingit\\cmd;C:\\Windows\\system32;C:\\Windows;
VOLUME ["C:\\data"]
EXPOSE 9000
ENTRYPOINT ["portainer.exe"]