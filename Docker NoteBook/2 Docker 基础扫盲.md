2013年 Docker开源DockerEngine，定义了一个以镜像为标准的应用打包格式。

2014年 CoreOS推出rkt容器引擎。

2015年6月 Docker宣布成立OCI（Open Container Initiative）组织作为Linux基金会的协作项目，并将容器并将容器标准和runtime参考实现（runC）贡献出来。

2016年6月 Docker宣布开始在Docker Engine中内置Swarm mode

Google发起CRI（Container Runtime Interface，容器运行时接口）项目，通过shim的抽象层使得调度框架支持不同的容器引擎实现。

2016年12月14日，Docker宣布将Docker Engine的核心组件Containerd捐赠到一个新成开源社区。由于Containerd只包含最基本的容器管理能力，因此上层框架可以有更大的灵活性来提供容器的调度和编排能力。



## 容器与开发语言
Docker 是一个开源工具，它可以将你的应用打包成一个标准格式的镜像，并以容器的方式运行。
Docker 容器将一系列软件包装在一个完整的文件系统中，这个文件系统包含应用程序所需的一切：代码、运行时工具、系统工具、系统依赖。

所有的容器会共享一个Kernel，因此一个Kernel下可以运行各种Linux发行版的容器？ 


## 基础技术

## 构造容器

## 构造镜像


## 构造容器进阶


## 容器网络


## 高级实践
