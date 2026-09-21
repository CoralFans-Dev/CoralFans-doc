# CoralFans安装

## 0.阅读并同意免责声明

作为用户首先需要明确: 使用CoralFans带来的功能就意味着承担第三方软件带来​​的风险.为了不给开发者带来不必要的麻烦,请阅读以下的免责声明,如果您使用了CoralFans就意味着您自动同意了该声明.

> ### 免责声明
>
> CoralFans(以下简称cf)是一个基于LeviLamina开发的我的世界基岩版辅助插件,它提供了令人惊叹的方便玩家的功能,给生电玩家创造了便利.另外,cf本身是开源免费的,内部没有任何恶意代码,原则上也不会对存档造成任何损害.
>
> 但考虑到此类软件的特殊性,开发者无法完全保证对用户的存档不造成任何破坏,万一发生意外情况,开发者不会也没有能力对用户造成的损失负责.
>
> 如果您继续使用cf插件,那么就代表您同意了该声明(或者说叫用户协议),如果您不想承担此类风险,请停止使用cf插件.

## 1.安装LeviLamina

CoralFans插件依赖于LeviLamina加载器,所以在使用本插件前,你需要安装LeviLamina。

+ Windows安装参考[LeviLamina中文安装教程](https://levilamina.liteldev.com/zh/install/)

### 补充

+ **不建议中文路径**
  + 这可能会导致意料之外的行为,不建议中文路径
+ **关闭cmd快速编辑**
  + windows默认cmd窗口启用快速编辑模式,这大概率会导致你的BDS程序阻塞,右键窗口选择**属性**,将**快速编辑模式**关闭即可

## 2.下载并安装前置

1. 使用lip进行安装: `lip install github.com/OEOTYAN/BedrockServerClientInterface` .

## 3.下载并安装插件本体

+ 使用lip进行安装: `lip install github.com/CoralFans-Dev/CoralFans` .
+ 也可以手动安装
  1. 前往[CoralFans的下载页面](https://github.com/CoralFans-Dev/CoralFans/releases)下载发布的release文件
  2. 将解压后的插件放入服务端根目录下的 `plugins` 文件夹

### 客户端版

+ 自26.10起，CoralFans同时提供客户端版本，可配合客户端版LeviLamina使用
+ 使用leviLauncher安装：在leviLauncher的Bedrinth界面中找到CoralFans进行安装
+ 使用lip进行安装: `lip install github.com/CoralFans-Dev/CoralFans#client`
+ 手动安装时，将客户端版压缩包解压后放入客户端 `mods` 文件夹

## 4.配置配置文件

你可能需要根据需求关闭部分功能(如 `tick` ，漏斗计数器等)

## 5.开服

本地服务器**ip**一栏填写 `127.0.0.1` 或者 `localhost`

云服务器**ip**一栏填写其公网ip(不知道的问服务商),端口按照服务器配置文件里面改，默认 `19132`
