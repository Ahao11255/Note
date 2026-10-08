---
title: Arch Linux 安装 JDK 14
tags:
  - Java
  - Java/环境
  - ArchLinux
  - JDK
aliases:
  - ArchLinux下的java-14-openjdk的安装
  - 安装JDK14
---

# Arch Linux 安装 JDK 14

## 需求

使用 RuoYi 时遇到需要 jdk-14 的需求，但在 Arch Linux 的官方仓库中并未提供 `jdk-14-openjdk` 软件包（jdk-14 不是 LTS 版本），而 AUR 中存在 `jdk-14-openjdk` 软件包。

![[AUR中的jdk14.png]]

但使用 AUR 仓库中的软件包时，出现 java 编译环境错误。

![[AUR安装jdk14是编译环境错误.png]]

切换本地默认 java 版本后依旧无法解决。

![[切换本地java版本1.png]]

![[切换本地java版本.png]]

## 解决方法

1. 前往 [OpenJDK 官网](https://openjdk.org/index.html) 下载 java-14-openjdk 源码自行编译安装（不利于系统的包管理，可能会造成后期的软件包冲突）。
2. 前往 [Oracle 官网](https://www.oracle.com/cn/) 下载 jdk14 的 deb 包，并使用 debtap 工具转换成 `.pkg.tar.zst` 包。

选择方案 2：

- 下载 java-14-openjdk.deb 包
- 克隆 [debtap 仓库](https://github.com/helixarch/debtap.git)
- 根据 issue，作者已经对脚本 bug 进行修改
- 给予 debtap 脚本可执行权限

```sh
cd Documents/debtap
sudo chmod +x ./debtap
```

- 使用其中的 debtap 脚本将 `.deb` 包转换为 `.pkg.tar.zst` 包

![[deb包的转化.png]]

- 使用 pacman 安装即可

```sh
sudo pacman -U jdk-14.0.2-14.0.2-1-x86_64.pkg.tar.zst
```

## 安装完成

检查本地 java 环境：

![[检查java环境.png]]

jdk14 已经完成安装。

## 相关笔记

- [[Java基础笔记]] —— 装好 JDK 后回到语言基础
- [[JUnit单元测试]] —— 环境就绪后开始写测试
