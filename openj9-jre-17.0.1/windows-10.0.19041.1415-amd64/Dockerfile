#PRE download https://github.com/ibmruntimes/semeru17-binaries/releases/download/jdk-17.0.1%2B12_openj9-0.29.1/ibm-semeru-open-jre_x64_windows_17.0.1_12_openj9-0.29.1.zip
#PRE unarchive ibm-semeru-open-jre_x64_windows_17.0.1_12_openj9-0.29.1.zip jre
#PRE delete ibm-semeru-open-jre_x64_windows_17.0.1_12_openj9-0.29.1.zip

FROM mcr.microsoft.com/windows/nanoserver:10.0.19041.1415-amd64
LABEL windows-version=10.0.19041.1415-amd64 openj9-version=0.29.1 java-version=17.0.1+12
COPY jre C:\\jre
USER ContainerUser
ENV JAVA_HOME C:\\jre
ENV PATH %PATH%;C:\\jre\\bin
WORKDIR C:\\jre
ENTRYPOINT ["java.exe"]
CMD ["--version"]