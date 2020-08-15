![](https://i.loli.net/2020/05/16/yHTszl5Zr4pbEBQ.jpg)

#### Power Collector是一个结构简单，易操作的类包管理器
* 访问我的[博客](https://powerlean.top)
* 若要参考代码及原理，请移步至我的[网站资料库](https://github.com/EdgeS5352/EdgeS5352.github.io/blob/master/blob/poco)

## 🏁快速开始
`curl -s powerlean.top/blob/poco.setup | bash`

### 📋Usage：poco [命令] [参数] [后缀]
命令:
- help        查询有效参数
- install     从目标地址获取指定文件
- list        列出所有可供下载的文件
- remove      删除指定的可执行文件
- search      查找指定文件的描述

后缀:
- -y          跳过确认环节
- -s          静默模式，不产生输出

###  组成结构

|  poco的组成部分   | 作用 |
|  ----  | ------------------------------ |
| [poco](https://github.com/EdgeS5352/EdgeS5352.github.io/blob/master/blob/poco)  | Power Collector的主体部分 |
| [poco.setup](https://github.com/EdgeS5352/EdgeS5352.github.io/blob/master/blob/poco.setup) | 安装脚本，运行安装更新等操作 |
| [poco.update](https://github.com/EdgeS5352/EdgeS5352.github.io/blob/master/blob/poco.update) | 更新脚本，检测poco主体部分的版本 |
| [poco.list](https://github.com/EdgeS5352/EdgeS5352.github.io/blob/master/blob/poco.list) | 软件包列表，载入各个软件包的描述 |
| [poco.note](https://github.com/EdgeS5352/EdgeS5352.github.io/blob/master/blob/poco.note) | 更新日志，声明更新内容 |
| [poco-rescue](https://github.com/EdgeS5352/EdgeS5352.github.io/blob/master/blob/poco-rescue) | 修复文件，替换损坏的文件主体|
| [poco.conf](https://github.com/EdgeS5352/EdgeS5352.github.io/blob/master/blob/poco.conf) | 控制文件，存放指向路径|

### 功能概览
|     功能    | 支持 |
| -------|---- |
| 自动编译 | × |
| 匹配依赖 | √ |
| 搜索查找 | √ |
| 自动更新 | √ |

### 部署可用下载源

Power Collector原理简单，部署下载源也非常容易，只需要一个有效网站便可部署。

**你需要在网站的根目录`/`下创建两个目录:**

- blob/
- tree/

*当然，文件夹也可以设置成其他名称，但需注意将两者进行区分。*
*请将软件包及其依赖全部存放至`blob/`目录。*
*[单击此处](https://github.com/EdgeS5352/Power-Collector/blob/master/README.md#依赖声明文件的编写格式)了解`tree/`目录的文件编写规范。*

**在`blob/`目录下创建以下两个文件：**

- poco.conf
- poco.list

*请自行编写可执行文件将用户原先的`poco.conf`替换为你所编写的版本，请按照该文件内的批注规范填写指向地址。*
*请参考本项目中的[poco.list](https://github.com/EdgeS5352/EdgeS5352.github.io/blob/master/blob/poco.list)格式来了解如何编写软件包列表。*

### 依赖声明文件的编写格式

每个软件包都必须对应一个**依赖声明文件**，它们的命名有一个固定的格式：

假设`blob/`目录下现存放有文件`XXX`,那么它的对应依赖声明文件必须命名为`XXX.tree`。

**依赖声明文件**的内容也有固定的格式，格式如下:

`export depends="XXX XXX XXX"`

**实例**:
现有一个名为`poco`的程序，它需要依赖于`poco.conf`和`poco-rescue`才能运行，则需要在它的依赖声明文件`poco.tree`中编写以下内容:

`export depends="poco.conf poco-rescue"`

*列表中的两个依赖程序名称之间用一个空格分隔*


假设某程序不需要任何依赖，则将变量内容留空:

`export depends=""`

*程序不需要依赖的情况下仍然须填写依赖声明文件，否则`poco`将被引导到错误的路径*

**现在你可以开始部署你的下载源了！**

### 以上。
