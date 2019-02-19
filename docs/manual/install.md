## 安装

### 二进制安装

请从[Release](https://github.com/FISCO-BCOS/FISCO-BCOS/releases)页面下载最新的二进制程序，我们提供静态的二进制程序，在Ubuntu16.04和CentOS7经过测试。

### 源码编译

```eval_rst
.. important::
    
    源码编译适合于有开发经验的用户，编译过程中需要下载依赖库，编译耗时受网络和机器配置的影响在10-20分钟不等。
```

FSICO-BCOS使用通用[CMake](https://cmake.org)构建系统生成特定平台的构建文件，这意味着无论您使用什么操作系统工作流都非常相似：
1. 安装构建工具和依赖包（依赖于平台）
1. 从[FISCO-BCOS][FSICO-BCOS-GitHub]克隆代码
1. 运行`cmake`生成构建文件并编译

#### 依赖安装

- Ubuntu

推荐Ubuntu 16.04以上版本，16.04以下的版本没有经过测试，源码编译时依赖于编译工具、`leveldb`和`libssl`。

```bash
$ sudo apt install -y libssl-dev libleveldb-dev openssl cmake git build-essential texinfo
```

- CentOS

推荐使用CentOS7以上版本。

```bash
$ sudo yum install -y epel-release
$ sudo yum install -y openssl-devel leveldb-devel openssl cmake3 gcc-c++ git
```

- macOS

推荐xcode10以上版本。macOS依赖包安装依赖于[Homebrew](https://brew.sh/)。

```bash
$ brew install -y leveldb openssl git
```

#### 克隆代码

```bash
$ git clone https://github.com/FISCO-BCOS/FISCO-BCOS.git
```

#### 编译

编译完成后二进制文件位于`FISCO-BCOS/build/bin/fisco-bcos`。

```bash
$ cd FISCO-BCOS
# 切换到release-2.0.1分支
$ git checkout release-2.0.1
$ mkdir build && cd build
# CentOS请使用cmake3
$ cmake ..
# 高性能机器可添加-j4使用4核加速编译
$ make
```

#### 编译选项介绍

- BUILD_GM，默认off，国密编译开关。通过`cmake -DBUILD_GM=on ..`打开国密开关。

- TESTS，默认off，单元测试编译开关。通过`cmake -DTESTS=on ..`打开单元测试开关。

- STATIC_BUILD，默认off，静态编译开关，只支持Ubuntu。通过`cmake -DSTATIC_BUILD=on ..`打开静态编译开关。

- 生成源码文档。
    ```bash
    # 安装Doxygen
    $ sudo apt install -y doxygen graphviz
    # 生成源码文档 生成的源码文档位于build/doc
    $ make doc
    ```

[FSICO-BCOS-GitHub]:https://github.com/FISCO-BCOS/FISCO-BCOS