#PRE download https://cdn.azul.com/zulu/bin/zulu11.56.19-ca-jre11.0.15-win_x64.zip
#PRE unarchive zulu11.56.19-ca-jre11.0.15-win_x64.zip jre
#PRE delete-file zulu11.56.19-ca-jre11.0.15-win_x64.zip

FROM mcr.microsoft.com/windows/nanoserver:10.0.19041.1415-amd64
LABEL zulu-version=11.56.19 java-version=11.0.15
COPY jre C:\\jre
USER ContainerUser
ENV JAVA_HOME=C:\\jre
ENV PATH=C:\\jre\\bin;C:\\Windows\\System32;C:\\Windows;
WORKDIR C:\\jre
ENTRYPOINT ["java.exe"]
CMD ["--version"]