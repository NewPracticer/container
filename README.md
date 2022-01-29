# container
docker学习路径，及踩坑 

## docker文档
+ [文档](https://dockertips.readthedocs.io/en/latest/)




#### docker windows 家庭版踩坑
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
    
