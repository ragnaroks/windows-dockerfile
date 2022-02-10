#PRE download https://github.com/ibmruntimes/semeru17-binaries/releases/download/jdk-17.0.2%2B8_openj9-0.30.0/ibm-semeru-open-jre_x64_windows_17.0.2_8_openj9-0.30.0.zip
#PRE unarchive ibm-semeru-open-jre_x64_windows_17.0.2_8_openj9-0.30.0.zip jre
#PRE delete-file ibm-semeru-open-jre_x64_windows_17.0.2_8_openj9-0.30.0.zip

FROM mcr.microsoft.com/windows/nanoserver:10.0.19041.1415-amd64
LABEL openj9-version=0.30.0 java-version=17.0.2+8
COPY jre C:\\jre
USER ContainerUser
ENV JAVA_HOME=C:\\jre
ENV PATH=C:\\jre\\bin;C:\\Windows\\System32;C:\\Windows;
WORKDIR C:\\jre
ENTRYPOINT ["java.exe"]
CMD ["--version"]