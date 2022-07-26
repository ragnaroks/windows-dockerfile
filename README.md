# windows 容器镜像列表
进入各个文件夹查看详细使用说明

### 查看当前主机兼容内核
- 打开 `C:\Windows\System32\vmcompute.exe` 文件的属性，查看**文件版本**字段
- 执行 `docker info | findstr Kernel` 查看后面括号中的内容，例如 Kernel Version: 10.0 19044 (**19041.1.amd64**fre.vb_release.191206-1406)

### 已知版本匹配列表
> 由于 windows 命名混乱，如果不能准确匹配镜像版本，可以尝试修订版本相近的镜像  
> 跨版本镜像除部分版本莫名兼容外，默认均不兼容

|版本号|别名|适用镜像|
|-|-|-|
|10.0.17763|desktop 1809、server 2019|windows-10.0.17763.2458-amd64|
|10.0.19041|desktop 2004、desktop 21H1|windows-10.0.19041.1415-amd64、windows-10-2004-amd64|