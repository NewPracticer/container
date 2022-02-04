# container
docker学习路径及踩坑 

## docker文档
+ [文档](https://dockertips.readthedocs.io/en/latest/)
+ docker命令行
    + docker image pull nginx 拉取一个镜像
    + docker container stop 停止一个容器/批量停止，后面追加多个container id
    + docker container run 运行一个容器
    + docker coontaier ls 列出所有的容器
    + docker container rm 删除一个容器
    + docker container run -it 创建一个容器并进入交互式模式
    + docker container exec -it 在一个已经运行的容器里执行一个额外的command
+ docker-compose
    + docker-compose 基本命令行
        + docker-compose pull
        + docker-compose up -d
        + docker-compose ps 
        + docker-compose -p myproject ps 
    + docker-compose镜像构建和获取
        + build: 
            + context: ./flask
            + dockerfile:Dockerfile.dev
    + docker-compose 更新
        + docker-compose up -d
        + docker-compose up -d --build 
        + docker-compose up -d --remove-orphans
    + docker-compose 水平扩展
        + docker-compose up -d --scale flask=3

### 学习课程 
+ https://coding.imooc.com/class/511.html
+ https://coding.imooc.com/class/189.html
+ 推荐理由 从基础的命令行，到docker-compose，以及docker-swam全覆盖。并且配有基本的实战演示。

### docker windows 家庭版踩坑
+ 无法安装Hyper-V
    + 报错 ：enable-windowsoptionalfeature : 功能名称 microsoft-hyper-v 未知。
    + 解决办法
        + 新建文本文档
        + pushd "%~dp0"
          dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt
          for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
          del hyper-v.txt
          Dism /online /enable-feature /featurename:Microsoft-Hyper-V-All /LimitAccess /ALL
        + 编辑完保存后将文件后缀改为.cmd，建议用因为命名文件名比如：Hyper-V
        + 保存完成后双击运行当前文件。文件执行完成后会在命令行提示重启电脑，在命令行输入y后电脑将自动重启
+ docker damon 无法运行
    + 管理员身份运行powershell。cd "C:\Program Files\Docker\Docker"  ./DockerCli.exe -SwitchDaemon
    + 重启后进入docker会提示下载 Linux 内核更新包
    
