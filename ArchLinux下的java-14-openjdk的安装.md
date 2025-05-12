# 需求

	使用RuoYi是遇到需要jdk-14的需求，但在Archlinux的官方仓库中并为提供jdk-14-openjdk软件包（jdk-14不是LTS版本），但在AUR中存在jdk-14-openjdk软件包

![[AUR中的jdk14.png]]

	但使用AUR仓库中的软件包时，出现java编译环境错误

![[AUR安装jdk14是编译环境错误.png]]

	切换本地默认java版本后依旧无法实现

![[切换本地java版本1.png]]
![[切换本地java版本.png]]

# 解决方法

1. 前往[openjdk官网](https://openjdk.org/index.html)下载java-14-openjdk源码自行编译安装(不利于系统的包管理，可能会造成后期的软件包冲突)
2. 前往[oriicle官网](https://www.oracle.com/cn/)下载jdk14的deb包，并使用debtap工具转换成.pkg.tar.zst包

	选择方案2

- 下载java-14-openjdk.deb包
- 克隆[GitHub仓库](https://github.com/helixarch/debtap.git)
- 根据issue,作者已经对脚本bug进行修改
- 给予debtap脚本可执行权限
```sh
cd Document/debtap
sudo chmod -R +x ./debtap
```
- 使用其中的debtap脚本将.deb包转换为.pkg.tar.zst包
![[deb包的转化.png]]
- 使用pacman安装即可
```sh
sudo pacman -U jdk-14.0.2-14.0.2-1-x86_64.pkg.tar.zst
```

# 安装完成

 检查本地java环境
![[检查java环境.png]]
jdk14已经完成安装