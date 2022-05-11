# HUAWEI Atlas 200 DK学习笔记

所需工具：Atlas 200开发板、读卡器、SD卡、网线、type-c数据线、笔记本电脑、路由器

文中的安装路径修改后记得修改环境变量中对应的**${install_path}**

## 运行环境搭建（电脑）

**方式1：**通过VMware虚拟机搭建本地Ubuntu服务器（熟悉VMware虚拟机操作的可选择性阅读）

【这一种方式相对复杂但是可以有图形化界面Mindstudio进行编写程序，且本地服务器搭建好，后期烧录SD卡速度也更快，只是第一次搭建麻烦些】

**方式2：**使用DD镜像烧录SD卡，具体可参考【https://bbs.huaweicloud.com/forum/thread-139685-1-1.html】里面所分享的文件在网盘，如下图，网盘下载慢（有会员的可以考虑这种方式，比较省事，就是可开发功能性少一些），而且后期想要使用Mindstudio编程软件只能在开发环境上设置（占内存），不能在运行环境上设置（方式2没有运行环境）。

>## 方式1
>
>**注：**【我本地使用的是18.04.5Ubuntu-desktop-**amd64**版本，给Atlas200板子用的18.04Ubuntu-desktop-**arm64**版本】
>
>### 1、下载Ubuntu镜像
>
>通过[Ubuntu官网](https://ubuntu.com/)下载18.04-desktop版本的镜像（18.04、18.04.5、18.04.6版本都可以），以及Atlas 200班子所需要的server-arm版本的镜像，步骤相同，如下：
>
>【或者直接点此链接到对应的18.04.5-desktop版本下载链接：http://old-releases.ubuntu.com/releases/18.04.5/】
>
>​	Download-->Ubuntu Desktop-->[see our alternative downloads](https://ubuntu.com/download/alternative-downloads)-->[Past releases](https://releases.ubuntu.com/)-->[old-releases.ubuntu.com](http://old-releases.ubuntu.com/releases/)
>
>![image-20220428160628310](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428160628310.png)
>
>![image-20220428160753998](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428160753998.png)
>
>![image-20220428160850592](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428160850592.png)
>
>![image-20220428160929158](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428160929158.png)
>
>![image-20220428161028743](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428161028743.png)
>
>![image-20220428161246081](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428161246081.png)
>
>![image-20220428161515727](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428161515727.png)
>
>### 2、下载VMware workstations软件搭建本地开发环境
>
>[Vmware官网](https://www.vmware.com/)下载步骤：
>
>【激活秘钥：ZF3R0-FHED2-M80TY-8QYGC-NPKYF（如果失效可自行百度搜）】
>
>下载安装完成之后，参考文章【https://www.cnblogs.com/kesu/p/15023239.html】进行本地搭建
>
>![image-20220428162133348](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428162133348.png)
>
>![image-20220428162313072](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428162313072.png)
>
>![image-20220428162342047](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428162342047.png)
>
>### 3、【以下操作在虚拟机中进行】安装成功之后进入桌面进行以下套件包下载
>
>（1）打开虚拟机浏览器进入如下网站下载几个套件包，共7个包两个脚本文件（包括上一步的Ubuntu18.04--server--arm包）(下载的包都在/home/hostname/Download下，尽量将下载的包都放在一起，在制SD卡的步骤更方便)
>
>- [昇腾官网](https://www.hiascend.com/)
>
>这个网站的中英文选项有些差距，英文状态下更好找需要的包，下载步骤如图所示：
>
>**【安装包】**选择硬件平台--固件与驱动
>
>![image-20220428163819711](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428163819711.png)
>
>选择对应版本，我选择的是5.0.2alpha003---1.0.10alpha版本，可以保持一致方便以后的步骤
>
>![image-20220428163940442](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428163940442.png)
>
>**【安装包】**选择软件平台---异构计算架构---CANN
>
>![image-20220428164212764](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428164212764.png)
>
>![image-20220428164442432](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428164442432.png)
>
>![image-20220428164651594](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428164651594.png)
>
>![image-20220428164629625](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428164629625.png)
>
>选择与上一步硬件平台一样的版本5.0.2alpha003，下载arm版本的nnrt和tookit两个包
>
>![image-20220428164844106](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428164844106.png)
>
>下载对应本地虚拟机的X86_X64的软件包
>
>![image-20220428165143489](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428165143489.png)
>
>（2）下载制作SD卡操作系统的脚本
>
>```python
>#下载制卡入口脚本“make_sd_card.py”。
>#从gitee下载：
>wget https://gitee.com/ascend/tools/raw/master/makesd/for_1.0.10.alpha/make_sd_card.p
>#从github下载：
>wget https://raw.githubusercontent.com/Ascend/tools/master/makesd/for_1.0.10.alpha/make_sd_card.py
>```
>
>```python
>#下载制作SD卡操作系统的脚本“make_ubuntu_sd.sh”
>#从gitee下载：
>wget https://gitee.com/ascend/tools/raw/master/makesd/for_1.0.10.alpha/make_ubuntu_sd.sh
>#从github下载：
>wget https://raw.githubusercontent.com/Ascend/tools/master/makesd/for_1.0.10.alpha/make_ubuntu_sd.sh
>```
>
>（3）下载Python3.7.5源码包
>
>```
>wget https://www.python.org/ftp/python/3.7.5/Python-3.7.5.tgz
>```
>
>（4）下载Mindstudio
>
>昇腾官网--软件平台--Mindstudio--Download--选择下载Linux版本
>
>![image-20220428170847441](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428170847441.png)
>
>![image-20220428170952192](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428170952192.png)
>
>下载完所有的包如下：
>
>![image-20220429112218462](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429112218462.png)
>
>###  4、环境配置
>
>（1）安装Python3.7.5及相关依赖
>
>​	 安装依赖包
>
>```python
>sudo apt-get install -y gcc g++ make cmake zlib1g zlib1g-dev libbz2-dev libsqlite3-dev libssl-dev libxslt1-dev libffi-dev unzip pciutils net-tools libncursesw5-dev 
>```
>
>​	  进入下载目录下，解压源码包
>
>```python 
>tar -zxvf Python-3.7.5.tgz
>```
>
>​	  进入解压后的文件夹，执行配置、编译和安装命令
>
>```python
>cd Python-3.7.5
>./configure --prefix=/usr/local/python3.7.5 --enable-loadable-sqlite-extensions --enable-shared
>#j后边的数字具体看自己的电脑配置，数字越大编译更快些
>make -j8 
>sudo make install
>```
>
>​	 设置软链接
>
>```python
>sudo ln -s /usr/local/python3.7.5/bin/python3 /usr/local/python3.7.5/bin/python3.7.5
>sudo ln -s /usr/local/python3.7.5/bin/pip3 /usr/local/python3.7.5/bin/pip3.7.5
>```
>
>​	 配置python3.7.5的环境变量
>
>```python
>#打开.bashrc文件
>vi ~/.bashrc
>#按i插入，在末尾添加以下几行内容
>
>#用于设置python3.7.5库文件路径
>export LD_LIBRARY_PATH=/usr/local/python3.7.5/lib:$LD_LIBRARY_PATH
>#如果用户环境存在多个python3版本，则指定使用python3.7.5版本
>export PATH=/usr/local/python3.7.5/bin:$PATH
>
>#esc退出编辑模式，命令保存文件并退出
>:wq!
>#执行命令使其立即生效
>source ~/.bashrc
>```
>
>​	 验证是否安装成功
>
>```python
>#返回相关版本信息，则说明安装成功
>python3.7.5 --version
>pip3.7.5  --version
>```
>
>（2）安装开发套件包
>
>​	 创建非root用户
>
>```python
>#这里以HwHiAiUser用户为例
>groupadd HwHiAiUser
>useradd -g HwHiAiUser -d /home/HwHiAiUser -m HwHiAiUser -s /bin/bash
>#设置非root用户密码
>passwd HwHiAiUser
>```
>
>​	 安装套件包
>
>![image-20220429110026649](C:\Users\Kould\AppData\Roaming\Typora\typora-user-images\image-20220429110026649.png)
>
>```python
>#进入套件包下载目录，我的统一放在/home/hostname/Download下
>cd /home/hostname/Download
>ll
>#更改run文件为可执行文件，执行后run文件变为绿色可执行文件，如上图
>chmod +x *.run
>ll
>
>
>#安装.run文件
>./Ascend-cann-toolkit_5.0.2.alpha005_linux-x86_64.run --install
>#将相关环境变量保存，后续使用
>vi env.txt
>#按i进入编辑模式，右键粘贴即可,保存退出
>:wq!
>#继续安装套件依赖包
>./Ascend-cann-nnrt_5.0.2.alpha005_linux-aarch64.run --install
>./Ascend-cann-toolkit_5.0.2.alpha005_linux-aarch64.run --install
>```
>
>安装过程图如下：
>
>![image-20220429105448712](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429105448712-16520659922021.png)
>
>![image-20220429105732011](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429105732011.png)
>
>（3）安装Mindstudio
>
>```python
>#解压安装包
>tar -zxvf MindStudio_{version}_linux.tar.gz
>#进入解压后的MindStudio/bin目录，进行安装sh文件
>cd MindStudio/bin
>./MindStudio.sh #这一步会检查环境变量的依赖，会提示failure，因为缺少的相关依赖，直接按照提示命令执行安装即可
>#部分依赖包由于网站在国外，无法连接下载，可以在我的CSDN中下载我已经下好上传的依赖包文件
>#CSDN链接：
>```
>
>![image-20220429105323394](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429105323394.png) 
>
>缺少的几个fonts包下载之后，通过以下命令安装，安装过程如图所示
>
>```python
>dpkg -i "包的名字"
>```
>
>![image-20220429111438132](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429111438132.png)
>
>可能会遇到的问题，没有遇到可跳过这一步
>
>提示需要安装jdk，按照以下命令安装和添加环境变量
>
>```python
>#安装jdk相关依赖包
>sudo apt-get install -y openjdk-11-jdk
>#添加环境变量
>vi ~/.bashrc
>#在.bashrc文件末添加下面几行内容
>export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64 
>export PATH=$JAVA_HOME/bin:$PATH
>#保存退出
>:wq!
>source ~/.bashrc
>
>#验证JDK是否安装成功以及环境变量是否生效
>echo $JAVA_HOME
>/usr/lib/jvm/java-11-openjdk-amd64  #返回信息是这个则说明安装成功，否则表示JDK安装失败。
>which jconsole
>/usr/lib/jvm/java-11-openjdk-amd64/bin/jconsole  #输出这个信息表示安装成功，否则表示JDK安装失败。
>```
>
>安装JDK之后，在此运行启动Mindstudio
>
>```python
>./MindStudio.sh
>#这次检查环境变量等会出现success
>```
>
>![image-20220429110812458](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429110812458.png)
>
>![image-20220510092909553](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220510092909553.png)
>
>进入Mindstudio之后，按照如下图所示进行操作:
>
>![image-20220510092957693](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220510092957693.png)
>
>设置一下ssh设备管理
>
>![image-20220510094009787](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220510094009787.png)
>
>保存时会提示在输入依次密码
>
>![image-20220510094130050](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220510094130050.png)
>
>成功之后会显示如下：
>
>![image-20220510094156629](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220510094156629.png)
>
>### 5、制作SD卡
>
>（1）将准备好的SD卡插入读卡器，读卡器插入笔记本电脑，在弹出的选项中选择连接到虚拟机
>
>![image-20220429110504751](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429110504751.png)
>
>（2）执行命令检查SD卡的设备号，并执行之前下载好的make_sd_card.py和make_ubuntu_sd.sh
>
>```python
>#查看SD卡设备号
>fdisk -l
>```
>
>![image-20220429110952590](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429110952590.png)
>
>```python
>#执行制卡脚本
>python3 make_sd_card.py local /dev/sdb
>#中间可能会弹出缺少一些依赖包，然后进行安装相关依赖包之后，在此执行制卡脚本命令
>#如果没有弹出缺少依赖包，则跳过下面两条安装依赖的命令
>pip3 install pyyaml
>
>apt-get install qemu-user-static binfmt-support python3-yaml squashfs-tools gcc-aarch64-linux-gnu g++-aarch64-linux-gnu
>
>
>#提示选择Y，然后会执行一段时间，等待即可，制卡成功会出现Make SD Card successfully!如下图
>```
>
>![image-20220429111112561](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429111112561.png)

制卡成功后，运行环境的工作就暂时告一段落，接下来将SD插入Atlas 200Dk的开发板上，并同时接通电源，此时在开发板后边会有四个灯，开发板通电之后LED1和LED2会亮，3和4会通过读系统依次点亮，**首次安装读系统整个过程大概需要5-10分钟**

![image-20220429112702245](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429112702245.png)

![image-20220429112332405](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429112332405.png)

![image-20220429112304973](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429112304973.png)

如果遇到某一个灯没有亮，参考下图，找原因

![image-20220429112726103](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429112726103.png)

**必须等四个灯全部点亮**之后，再依次接入网线和type-c线（另一端USB接入笔记本电脑），接入之后依旧会让选择接入设备

![image-20220429110504751](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429110504751-16520661896612.png)

选择linux-ubuntu之后 ，执行以下命令进行检测开发板是否接入，有一个ens16或者35开头的网口就代表接入成功。

![image-20220429114950326](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429114950326.png)

然后执行configure_usb_ethernet.sh命令配置开发板接入电脑的USB端网口,会拿到一个USB的IP地址（一般都是192.168.1.166）

```
bash configure_usb_ethernet.sh
```

![image-20220429115404173](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429115404173.png)

通过ssh命令进行链接Atlas200DK开发板，**登录时有些时候很慢或者连接失败，可能是因为还没有拿到IP地址，稍等片刻再试**

```python
ssh HwHiAiUser@192.168.1.2    #开发板默认登录名称和IP,登录名称为上面设置的非root用户
Mind@123   #默认登录密码
```

 登陆成功之后会进入HwHiAiUser@davinci-mini账户（代表进入开发板成功）显示如下：

![image-20220429113736227](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429113736227.png)               

## 开发环境搭建（Atlas 200 DK）

>### 1、联网
>
>进入开发板之后先进行联网操作（使用网线通过路由器连接Ubuntu服务器，路由器的地址一般均为192.168.1.X段）**确保Ubuntu服务器（电脑）ip网段和开发板eth0的ip都在一个网段**（通过路由器连接开发板的好处：Ubuntu服务器和开发板建立通信的同时还可以访问www.baidu.com）
>
>首次登录时，系统将提示密码已过期：可以先不管
>
>```python
>WARNING:Your password has expired.
>```
>
>进入root用户，密码就是默认密码Mind@123
>
>```python
>su root
>#进入/etc/netplan目录，修改01-netcfg.yaml文件配置
>cd /etc/netplan
>vi 01-netcfg.yaml
>#将文件中对应部分修改为如下内容
>eth0:
>dhcp4: true
>addresses: []
>optional: true
>#保存退出
>:wq!
>#执行如下命令重启网络服务
>netplan apply
>#执行ifconfig命令获取eth0网卡的IP地址,并进行测试是否介入网络
>ping www.baidu.com  #ping通则说明接入互联网成功
>```
>
>网络之前老是会遇到问题，所示摸索之后成功接入，用手机拍的
>
>![image-20220429120512012](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429120512012.png)
>
>按照上述命令配置可以很快正常接入网络，避免踩坑
>
>### 2、更新源和下载相关依赖包
>
>```python
>#更新源
>apt-get install update
>#安装相关依赖包
>#1、检查系统是否安装python依赖以及gcc等软件
>gcc --version
>g++ --version
>make --version
>cmake --version
>dpkg -l zlib1g| grep zlib1g| grep ii
>dpkg -l zlib1g-dev| grep zlib1g-dev| grep ii
>dpkg -l libsqlite3-dev| grep libsqlite3-dev| grep ii
>dpkg -l openssl| grep openssl| grep ii
>dpkg -l libssl-dev| grep libssl-dev| grep ii
>dpkg -l libffi-dev| grep libffi-dev| grep ii
>dpkg -l unzip| grep unzip| grep ii
>dpkg -l pciutils| grep pciutils| grep ii
>dpkg -l net-tools| grep net-tools| grep ii
>dpkg -l libblas-dev| grep libblas-dev| grep ii
>dpkg -l gfortran| grep gfortran| grep ii
>dpkg -l libblas3| grep libblas3| grep ii
>dpkg -l libopenblas-dev| grep libopenblas-dev| grep ii
>#若分别返回如下信息则说明已经安装，进入下一步（版本号可能会有些许差异）
>gcc (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0
>g++ (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0
>GNU Make 4.1
>cmake version 3.10.2
>ii  zlib1g:arm64   1:1.2.11.dfsg-0ubuntu2.1 arm64        compression library - runtime
>ii  zlib1g-dev:arm64 1:1.2.11.dfsg-0ubuntu2.1 arm64        compression library - development
>ii  libsqlite3-dev:arm64 3.22.0-1ubuntu0.5 arm64        SQLite 3 development files
>ii  openssl        1.1.0g-2ubuntu4 arm64        Secure Sockets Layer toolkit - cryptographic utility
>ii  libssl-dev:arm64 1.1.1-1ubuntu2.1~18.04.17 arm64        Secure Sockets Layer toolkit - development files
>ii  libffi-dev:arm64 3.2.1-8      arm64        Foreign Function Interface library (development files)
>ii  unzip          6.0-21ubuntu1.1 arm64        De-archiver for .zip files
>ii  pciutils       1:3.5.2-1ubuntu1 arm64        Linux PCI Utilities
>ii  net-tools      1.60+git20161116.90da8a0-1ubuntu1 arm64        NET-3 networking toolkit
>ii  libblas-dev:arm64 3.7.1-4ubuntu1 arm64        Basic Linear Algebra Subroutines 3, static library
>ii  gfortran       4:7.4.0-1ubuntu2.3 arm64        GNU Fortran 95 compiler
>ii  libblas3:arm64 3.7.1-4ubuntu1 arm64        Basic Linear Algebra Reference implementations, shared library
>ii  libopenblas-dev:arm64 0.2.20+ds-4  arm64        Optimized BLAS (linear algebra) library (development files)
>#如果其中一个没有返回相关信息，可以通过apt-get安装缺少的依赖
>apt-get install -y gcc g++ make cmake zlib1g zlib1g-dev openssl libsqlite3-dev libssl-dev libffi-dev unzip pciutils net-tools libblas-dev gfortran libblas3 libopenblas-dev  #（按需选择）
>```
>
>>注意
>
>>- 如果使用root用户安装依赖，安装依赖时不需要加sudo
>>- libsqlite3-dev需要在python安装之前安装，如果用户操作系统已经安装python3.7.5环境，在此之后再安装libsqlite3-dev，则需要重新编译python环境。
>
>![image-20220509153818433](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220509153818433.png)
>
>### 3、python环境
>
>执行命令**python3.7 --version**，如果返回信息满足python版本要求（3.7.0~ 3.7.9），则直接进入下一步。
>
>否则可参考如下方式安装python3.7.5。
>
>（1）使用wget下载python3.7.5源码包，可以下载到安装环境的任意目录，命令为：
>
>```python
>wget https://www.python.org/ftp/python/3.7.5/Python-3.7.5.tgz
>```
>
>（2）进入下载后的目录，解压源码包，命令为：
>
>```python
>tar -zxvf Python-3.7.5.tgz
>```
>
>（3）进入解压后的文件夹，执行配置、编译和安装命令：
>
>```python
>cd Python-3.7.5
>./configure --prefix=/usr/local/python3.7.5 --enable-loadable-sqlite-extensions --enable-shared
>make
>sudo make install
>```
>
>其中“--prefix”参数用于指定python安装路径，用户根据实际情况进行修改。“--enable-shared”参数用于编译出libpython3.7m.so.1.0动态库。“--enable-loadable-sqlite-extensions”参数用于加载libsqlite3-dev依赖。
>
>本手册以--prefix=/usr/local/python3.7.5路径为例进行说明。执行配置、编译和安装命令后，安装包在/usr/local/python3.7.5路径，libpython3.7m.so.1.0动态库在/usr/local/python3.7.5/lib/libpython3.7m.so.1.0路径。
>
>（4）执行如下命令设置软链接：
>
>```python
>sudo ln -s /usr/local/python3.7.5/bin/python3 /usr/local/python3.7.5/bin/python3.7.5
>sudo ln -s /usr/local/python3.7.5/bin/pip3 /usr/local/python3.7.5/bin/pip3.7.5
>```
>
>（5）设置python3.7.5环境变量。
>
>```python
>#用于设置python3.7.5库文件路径
>export LD_LIBRARY_PATH=/usr/local/python3.7.5/lib:$LD_LIBRARY_PATH
>#如果用户环境存在多个python3版本，则指定使用python3.7.5版本
>export PATH=/usr/local/python3.7.5/bin:$PATH
>```
>
>（6）安装完成之后，执行如下命令查看安装版本，如果返回相关版本信息，则说明安装成功。
>
>```python
>python3.7 --version
>pip3.7 --version
>```
>
>（7）安装前请先使用**pip3.7 list**命令检查是否安装相关依赖，若已经安装，则请跳过该步骤；若未安装，则安装命令如下（如果只有部分软件未安装，则如下命令修改为只安装还未安装的软件即可）。
>
>- 请在安装前配置好pip源，具体可参考[配置pip源](https://www.hiascend.com/document/detail/zh/CANNCommunityEdition/deploy502alpha3/atlasdeploy_03_0103.html#ZH-CN_TOPIC_0000001118879830)。
>- 安装前，建议执行命令**pip3.7 install --upgrade pip**进行升级，避免因pip版本过低导致安装失败。
>- 如下命令如果使用非root用户安装，需要在安装命令后加上**--user**，例如：**pip3.7 install attrs** **--user，**安装命令可在任意路径下执行。
>- 要求numpy版本大于等于1.13.3且小于1.20，推荐numpy版本为1.17.2。
>
>```python
>pip3.7 install attrs
>pip3.7 install numpy==1.17.2
>pip3.7 install decorator
>pip3.7 install sympy
>pip3.7 install cffi
>pip3.7 install pyyaml
>pip3.7 install pathlib2
>pip3.7 install psutil
>pip3.7 install protobuf
>pip3.7 install scipy
>pip3.7 install requests
>```
>
>### 4、昇腾套件包安装
>
>（1）将第一大步运行环境搭建中的如下（红框框住的）开发套件包上传到安装环境（Atlas 200DK）任意路径
>
>![image-20220509154015763](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220509154015763.png)
>
>这一步在Ubuntu虚拟机中的运行环境中操作
>
>```python
>scp /home/hai/Downloads/Ascend-cann-toolkit_5.0.2.alpha005_linux-x86_64.run HwHiAiUser@192.168.1.2:/home/HwHiAiUser/"你自己定义的目录文件夹"
>scp /home/hai/Downloads/Ascend-cann-toolkit_5.0.2.alpha005_linux-aarch64.run HwHiAiUser@192.168.1.2:/home/HwHiAiUser/"你自己定义的目录文件夹"    
>```
>
>（2）进入开发环境Atlas200DK中的软件包所在路径--即：/home/HwHiAiUser/"你自己定义的目录文件夹"    。
>
>增加对软件包的可执行权限。
>
>```
>chmod +x *.run
>```
>
>执行如下命令校验软件包安装文件的一致性和完整性。
>
>```python
>./Ascend-cann-toolkit_5.0.2.alpha005_linux-x86_64.run --check
>./Ascend-cann-toolkit_5.0.2.alpha005_linux-aarch64.run --check
>#检查后完整会返回以下信息
>Verifying archive integrity...  100%   SHA256 checksums are OK. All good.
>#执行套件包的安装
>./Ascend-cann-toolkit_5.0.2.alpha005_linux-x86_64.run --install --chip=Ascend310-minirc --blacklist=nnae
>./Ascend-cann-toolkit_5.0.2.alpha005_linux-aarch64.run --install --chip=Ascend310-minirc --blacklist=nnae
>```
>
>安装完成后，若显示如下信息，则说明软件安装成功：
>
>```python
>[INFO] xxx install success
>```
>
>>- --chip=Ascend310-minirc：指定芯片型号为Ascend310 Soc芯片（RC模式启动，作为主控CPU）。
>>
>>	配置了此参数，则会部署Ascend310RC形态的AI CPU软件包。
>>
>>- --blacklist=nnae：安装时屏蔽离线推理、在线推理、训练及IR构图的部分特性
>
>### 5、安装后处理
>
>（1）配置交叉编译环境
>
>因为开发环境与运行环境的架构不同，所以需要在开发环境安装交叉编译工具
>
>在开发环境和运行环境中执行**aarch64-linux-gnu-g++ --version**命令检查是否已安装g++交叉编译器，若有如下回显信息，则表示已经安装。
>
>```python
>aarch64-linux-gnu-g++ (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0
>
>#若未安装g++交叉编译器，则需要进行安装，安装命令示例如下（以下命令仅为示例，请用户根据实际情况替换）：
>sudo apt-get install g++-aarch64-linux-gnu
>```
>
>（2）配置环境变量
>
>安装完成后，需要设置如下环境变量才能进行正常开发流程（如下环境变量中${install_path}以软件包使用默认安装路径为例进行说明）：
>
>通过export方式设置环境变量，该种方式设置的环境变量只在当前窗口有效，设置完成后立即生效。建议用**vi ~/.bashrc**方式修改,如下：
>
>>用户也可以通过修改~/.bashrc文件方式设置永久环境变量，如下以bash shell为例进行说明：
>>
>>1. 以安装用户在任意目录下执行**vi ~/.bashrc**命令，打开**.bashrc**文件，在文件最后一行后面添加上述内容。
>>2. 执行**:wq!**命令保存文件并退出。
>>3. 执行**source ~/.bashrc**命令使其立即生效
>
>```python
>export install_path=/home/HwHiAiUser/Ascend/ascend-toolkit/latest     
>export ASCEND_OPP_PATH=${install_path}/opp
>export ASCEND_AICPU_PATH=${install_path}
>export TOOLCHAIN_HOME=${install_path}/toolkit
>
>#进行模型转换/算子编译时配置
>export LD_LIBRARY_PATH=${install_path}/atc/lib64:$LD_LIBRARY_PATH
>export PATH=/usr/local/python3.7.5/bin:${install_path}/atc/ccec_compiler/bin:${install_path}/atc/bin:$PATH   # python3.7.5安装路径请根据实际情况替换
>export PYTHONPATH=${install_path}/atc/python/site-packages:${install_path}/toolkit/python/site-packages:$PYTHONPATH
>
># 编译AscendCL应用程序时配置
>export DDK_PATH=${install_path}/arm64-linux
>export NPU_HOST_LIB=${install_path}/arm64-linux/acllib/lib64/stub
>
># 安装toolkit包时配置
>. /usr/local/Ascend/ascend-toolkit/set_env.sh    
>```
>
>【**建议开发环境和运行环境均设置一下上述环境变量**】
>
>
>
>### 6、按照自己需要安装相关依赖包（记得创建隔离环境）

## 案例1-- crowd_count_picture

### 1、案例所需环境准备和依赖安装

#### （1）在运行环境本地电脑进行相关环境变量导入

```python
#打开.bashrc文件
vi ~/.bashrc
#添加以下环境变量
export install_path=$HOME/Ascend/ascend-toolkit/latest

export PATH=/usr/local/python3.7.5/bin:${install_path}/atc/ccec_compiler/bin:${install_path}/atc/bin:$PATH

export ASCEND_OPP_PATH=${install_path}/opp

export LD_LIBRARY_PATH=${install_path}/atc/lib64

export PYTHONPATH=${install_path}/atc/python/site-packages/te:${install_path}/atc/python/site-packages/topi:$PYTHONPATH
#保存退出
:wq!
#使环境变量生效
source ~/.bashrc
```

#### （2）在开发环境开发板上安装依赖

```python
#连接登录开发板
ssh HwHiAiUser@192.168.1.2    #开发板默认登录名称和IP,登录名称为上面设置的非root用户
Mind@123   #默认登录密码
#切换为root用户 （root用户默认密码：Mind@123）
su root
#给sudoer文件配置写权限，并打开该文件
chmod u+w /etc/sudoers
vi /etc/sudoers

#在该文件 # User privilege specification 下面增加如下内容：
HwHiAiUser ALL=(ALL:ALL) ALL

#完成后，执行以下命令取消/etc/sudoers文件的写权限，并切换回普通用户
chmod u-w /etc/sudoers
exit
```

![image-20220429144402971](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429144402971.png)

#### （3）开发板设置联网--（上面配置过，可跳过）

```python
su root
#进入/etc/netplan目录，修改01-netcfg.yaml文件配置
cd /etc/netplan
vi 01-netcfg.yaml
#将文件中对应部分修改为如下内容
    eth0:
      dhcp4: true
      addresses: []
      optional: true
#保存退出
:wq!
#执行如下命令重启网络服务
netplan apply
#执行ifconfig命令获取eth0网卡的IP地址,并进行测试是否介入网络
ping www.baidu.com  #ping通则说明接入互联网成功
```

#### （4）开发者板apt更换下载源

**以下给出两种源，选择其中一种使用，如更新源失败，请自行更换可用Ubuntu 18.04 arm源**

- ubuntu18.04-arm华为源

  执行以下换源操作
  **sudo wget -O /etc/apt/sources.list [https://repo.huaweicloud.com/repository/conf/Ubuntu-Ports-bionic.list](https://gitee.com/link?target=https%3A%2F%2Frepo.huaweicloud.com%2Frepository%2Fconf%2FUbuntu-Ports-bionic.list)**

  更新源
  **sudo apt-get update**

- ubuntu18.04-arm官方源

  修改源文件--添加阿里云镜像（注意是bionic类型，不是和平时笔记本上的下载源）

  ```python
  cp /etc/apt/sources.list /etc/apt/sources.list.back
  sudo vi /etc/apt/sources.list
  #添加镜像源
  deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
  deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
  deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
  deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
  deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
  deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
  deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
  deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
  deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
  deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
  ```

  也可以将源文件内容替换为以下ubuntu-arm官方源

  ```python
  deb http://ports.ubuntu.com/ bionic main restricted universe multiverse
  deb-src http://ports.ubuntu.com/ bionic main restricted universe multiverse
  deb http://ports.ubuntu.com/ bionic-updates main restricted universe multiverse
  deb-src http://ports.ubuntu.com/ bionic-updates main restricted universe multiverse
  deb http://ports.ubuntu.com/ bionic-security main restricted universe multiverse
  deb-src http://ports.ubuntu.com/ bionic-security main restricted universe multiverse
  deb http://ports.ubuntu.com/ bionic-backports main restricted universe multiverse
  deb-src http://ports.ubuntu.com/ bionic-backports main restricted universe multiverse
  deb http://ports.ubuntu.com/ubuntu-ports/ bionic main universe restricted
  deb-src http://ports.ubuntu.com/ubuntu-ports/ bionic main universe restricted  
  ```

  ```python
  #更新源。
  sudo apt-get update
  ```

  #### （5）部署PyACL
  在开发环境执行 `find / -name pyACL` 命令,将arm64-linux_gcc7.3.0路径下的 **pyACL** 目录拷贝到运行环境的/home/HwHiAiUser/Ascend/路径下。

  添加环境变量

  ```python
  #在运行环境添加环境变量，用于运行工程。
  #打开.bashrc文件
  vim ~/.bashrc
  #在文件中添加以下环境变量
  export LD_LIBRARY_PATH=/home/HwHiAiUser/ascend_ddk/arm/lib:/home/HwHiAiUser/Ascend/acllib/lib64:$LD_LIBRARY_PATH
  export PYTHONPATH=/home/HwHiAiUser/Ascend/pyACL/python/site-packages/acl:$PYTHONPATH
  
  #保存退出
  wq!
  
  #执行如下命令使环境变量生效。
  source ~/.bashrc
  ```

  #### （6）安装Python库

  ```python
  #安装pip3
  sudo apt-get install python3-pip
  #安装pillow 的依赖
  sudo apt-get install libtiff5-dev libjpeg8-dev zlib1g-dev libfreetype6-dev liblcms2-dev libwebp-dev tcl8.6-dev tk8.6-dev python-tk
  #安装python库
  python3.6 -m pip install --upgrade pip --user -i https://mirrors.huaweicloud.com/repository/pypi/simple
  python3.6 -m pip install Cython numpy pillow tornado==5.1.0 protobuf --user -i https://mirrors.huaweicloud.com/repository/pypi/simple
  #若apt-get安装依赖出现类似报错（dpkg: error processing package *** (--configure)） ，请参考FAQ来解决。
  #若Python包安装失败，可以试用其他源 https://bbs.huaweicloud.com/forum/thread-97632-1-1.html 或不加-i 参数使用默认pip源
  
  #安装python3-opencv
  sudo apt-get install python3-opencv
  
  #安装ffmpeg
  Python样例中的atlas_util库会调用ffmpeg的so文件。
  
  #创建文件夹，用于存放编译后的文件
  mkdir -p /home/HwHiAiUser/ascend_ddk/arm
  
  #下载ffmpeg
  cd $HOME
  wget http://www.ffmpeg.org/releases/ffmpeg-4.1.3.tar.gz
  tar -zxvf ffmpeg-4.1.3.tar.gz
  cd ffmpeg-4.1.3
  
  #安装ffmpeg
  ./configure --enable-shared --enable-pic --enable-static --disable-x86asm --prefix=/home/HwHiAiUser/ascend_ddk/arm
  make -j8  
  make install
  
  #将ffmpeg添加到系统环境变量中，使得其他程序能够找到ffmpeg环境
  su root
  vim /etc/ld.so.conf.d/ffmpeg.conf
  #在末尾添加一行
  /home/HwHiAiUser/ascend_ddk/arm/lib
  #使配置生效
  ldconfig
  
  #配置profile系统文件
  vim /etc/profile
  #在末尾添加一行
  export PATH=$PATH:/home/HwHiAiUser/ascend_ddk/arm/bin
  #使配置文件生效
  source /etc/profile
  #使opencv能找到ffmpeg
  cp /home/HwHiAiUser/ascend_ddk/arm/lib/pkgconfig/* /usr/share/pkgconfig
  #退出root用户
  exit
  ```

  #### （7） python atlasutil 安装说明

  参考https://gitee.com/ascend/samples/blob/v0.4.0/python/common/atlas_utils/README.md

### 2、获取源码包

（1）命令行方式下载，开发环境，非root用户命令行中执行以下命令下载源码仓

```python
mkdir yourfilename
cd yourfilename
git clone https://gitee.com/ascend/samples.git
```

（2）获取此应用中所需要的模型

参考下表获取此应用中所用到的模型，并将其存放到开发环境普通用户下的工程目录：

```
cd /home/HwHiAiUser/yourfilename/samples/python/contrib/crowd_count_picture/model
```

参考https://gitee.com/ascend/ModelZoo-TensorFlow/tree/master/TensorFlow/contrib/cv/crowdCount/ATC_count_person_caffe_AE 原始模型，下载**原始模型**及**对应的cfg文件**。并存放在model文件夹下。

（3）将原始模型转换为Davinci模型

**注：请确认环境变量已经在[环境准备和依赖安装](https://gitee.com/ascend/samples/blob/master/python/environment)中配置完成**

```python
#设置LD_LIBRARY_PATH环境变量。
#由于LD_LIBRARY_PATH环境变量在使用atc工具和运行样例时会产生冲突，所以需要在命令行单独设置此环境变量，方便修改。
export LD_LIBRARY_PATH=${install_path}/atc/lib64
#执行以下命令使用atc命令进行模型转换。（root下可能会提示没有atc命令，这个时候需要退出root模式，在普通用户模式下进行操作即可）
atc --input_shape="blob1:1,3,800,1408" --weight="count_person.caffe.caffemodel" --input_format=NCHW --output="count_person.caffe" --soc_version=Ascend310 --insert_op_conf=insert_op.cfg --framework=0 --model="count_person.caffe.prototxt" 
```

（4）获取样例需要的测试图片

执行以下命令，进入样例的data文件夹中，下载对应的测试图片。

``` export LD_LIBRARY_PATH=
cd /home/HwHiAiUser/yourfilename/samples/python/contrib/crowd_count_picture/data
wget https://c7xcode.obs.cn-north-4.myhuaweicloud.com/models/crowdCount/crowd.jpg
```

### 3、 样例运行

**注：已经通过ssh登录Atlas请跳过步骤(1)，直接执行步骤(2)即可。**

（1）执行以下命令,将开发环境的**samples**目录上传到运行环境中，例如 **/home/HwHiAiUser**，并以HwHiAiUser（运行用户）登录运行环境（Host）。

```python
scp -r $HOME/samples  HwHiAiUser@xxx.xxx.xxx.xxx:/home/HwHiAiUser
ssh HwHiAiUser@xxx.xxx.xxx.xxx
#xxx.xxx.xxx.xxx为运行环境ip，200DK在USB连接时一般为192.168.1.2
```

（2）运行可执行文件。

执行以下命令，设置运行环境变量，并切换目录。

```python
cd /home/HwHiAiUser/yourfilename/samples/python/contrib/crowd_count_picture/src
#切换目录后，执行以下命令运行样例。
python3 main.py ../data/
```

如果是开发环境与运行环境合一部署，执行以下命令切换目录。

```python
 export LD_LIBRARY_PATH=
 source ~/.bashrc
 cd /home/HwHiAiUser/yourfilename/samples/python/contrib/crowd_count_picture/src
 python3 main.py ../data/
```

### 4、运行结果

![image-20220429151214522](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429151214522.png)

## 案例2--**resnet50_imagenet_classificationi**

整体结构

```
resnet50_imagenet_classification
├──src
│ ├── acl_net.py //运行文件
│ └── constant.py //常量定义
├── data
│ ├── dog1_1024_683.jpg //测试图片数据
│ └── dog2_1024_683.jpg //测试图片数据
├── caffe_model
│ ├── resnet50.caffemodel //resnet50模型
│ └── resnet50.prototxt // resnet50模型的网络文件
└── model
  └── resnet50.om //转换后的模型文件
```

### 1、**Atlas 200 AI加速模块（ RC场景）：**

（1）安装minirc版本的acllib包，以安装在默认路径“/usr/local/Ascend”为例：配置LD_LIBRARY_PATH，将“/usr/local/Ascend/acllib/lib64”加入到LD_LIBRARY_PATH中。命令示例如下：

```python
export LD_LIBRARY_PATH=/usr/local/Ascend/acllib/lib64:$LD_LIBRARY_PATH
```

（2）获取aarch64架构的cann-nnrt软件包，在服务器上解压，在软件包所在目录下的解压命令如下：

```python
./Ascend-cann-nnrt_xxx_linux-aarch64.run --noexec --extract="解压目标路径"
```

在解压目标路径下找到“run_package/Ascend-pyACL-xxx-linux.aarch64.run”，在软件包所在目录下的解压命令如下：

```python
./Ascend-pyACL-xxx-linux.aarch64.run --noexec --extract="解压目标路径"
```

在解压路径下找到“python/site-packages/acl/acl.so”，将acl.so上传至200RC上，例如，上传至“ /usr/local/Ascend/pyACL/python/site-packages/acl”目录下，配置PYTHON环境变量，将“ /usr/local/Ascend/pyACL/python/site-packages/acl”加入到PYTHON中。命令示例如下：

```python
export PYTHONPATH=/usr/local/Ascend/pyACL/python/site-packages/acl:$PYTHONPATH
```

### 2、模型运行

1. 模型转换。

   （1）以HwHiAiUser（运行用户）登录开发环境。

   （2）ATC转换工具主要注意一下几点：

   >- 使用export方式设置环境变量后，环境变量只在当前窗口有效。**如果用户之前在.bashrc文件中设置过ATC软件包安装路径的环境变量，则在执行命令之前，需要先手动注释掉原来设置的ATC安装路径环境变量**。
   >
   >- 若开发环境架构为Arm（aarch64），模型转换耗时较长，则可以参考[开发环境架构为Arm（aarch64），模型转换耗时较长](https://support.huawei.com/enterprise/zh/doc/EDOC1100206690?section=j00u)解决。
   >
   >- 该工具对Python版本的支持为3.7.0-3.7.9，本手册以Python3.7.5为例进行介绍，相应环境变量和安装命令以实际安装Python版本为准。
   >
   >- 使用ATC工具进行模型转换的过程中，会自动将ATC工具所在位置“../../python/site-packages”目录下算子编译依赖的TBE Python库写入PYTHONPATH环境变量。
   >
   >	若算子实现时用户引入了TBE模块外的其他Python依赖，请自行添加PYTHONPATH的环境变量，配置引入的Python依赖所在路径，如下所示：
   >
   >	export PYTHONPATH=xxxx:$PYTHONPATH

   可参考《[CANN 开发辅助工具指南](https://gitee.com/link?target=https%3A%2F%2Fsupport.huawei.com%2Fenterprise%2Fzh%2Fdoc%2FEDOC1100206690%3FidPath%3D23710424%7C251366513%7C22892968%7C251168373)》中的“ATC工具使用指南”章节中的ATC工具使用环境搭建，获取ATC工具并设置环境变量。

   （3）准备数据。 从以下链接获取ResNet-50网络的权重文件（*.caffemodel）、模型文件（resnet50.prototxt），并以HwHiAiUser（运行用户）将获取的文件上传至开发环境的“resnet50_imagenet_classification/caffe_model”目录下。

   >- 从gitee上获取：单击[Link](https://gitee.com/ascend/ModelZoo-TensorFlow/tree/master/TensorFlow/contrib/cv/resnet50/ATC_resnet50_caffe_AE)，查看README.md，查找获取原始模型的链接。
   >- 从GitHub上获取：单击[Link](https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2Fascend%2Fmodelzoo%2Ftree%2Fmaster%2Fcontrib%2FTensorFlow%2FResearch%2Fcv%2Fresnet50%2FATC_resnet50_caffe_AE)，查看README.md，查找获取原始模型的链接。

   （4）将ResNet-50网络转换为适配昇腾AI处理器的离线模型（*.om文件）。 切换到“resnet50_imagenet_classification”目录，执行如下命令。 Ascendxxx为使用的昇腾AI处理器型号，请用户自行替换。

   ```
   atc --model=caffe_model/resnet50.prototxt --weight=caffe_model/resnet50.caffemodel --framework=0 --output=model/resnet50 --soc_version=Ascend310 --input_format=NCHW --input_fp16_nodes=data --output_type=FP32 --out_nodes=prob:0
   ```

   >- --output参数：生成的resnet50.om文件存放在“resnet50_imagenet_classification/model”目录下。
   >- 使用atc命令时用户需保证对resnet50_imagenet_classification目录有写权限。

2. 运行应用

   （1）准备测试数据。 请从以下链接获取该样例的输入图片，并以运行用户将获取的文件上传至开发环境的“resnet50_imagenet_classification/data”目录下。如果目录不存在，需自行创建。
   [https://c7xcode.obs.cn-north-4.myhuaweicloud.com/models/aclsample/dog1_1024_683.jpg](https://gitee.com/link?target=https%3A%2F%2Fc7xcode.obs.cn-north-4.myhuaweicloud.com%2Fmodels%2Faclsample%2Fdog1_1024_683.jpg)
   [https://c7xcode.obs.cn-north-4.myhuaweicloud.com/models/aclsample/dog2_1024_683.jpg](https://gitee.com/link?target=https%3A%2F%2Fc7xcode.obs.cn-north-4.myhuaweicloud.com%2Fmodels%2Faclsample%2Fdog2_1024_683.jpg)
   
   （2）在resnet50_imagenet_classification路径下执行如下命令：

   ```
   python3 ./src/acl_net.py
   ```

### 3、运行结果

![image-20220509090553735](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220509090553735.png)

## 使用Mindstudio建立工程

## Mindstudio工程构建

1. 准备工程。

	按照对应样例下的命令行方式运行的README软件准备章节，准备好源码、模型、测试文件。

2. 非root用户命令行中执行以下命令，打开Mindstudio。

	**cd ~/MindStudio-ubuntu/bin**

	**./MindStudio.sh**

	![icon-note.gif](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/160652_6146f6a4_5395865.gif) **说明：**

	> - 打开Mindstudio时如果有报错，请在普通用户下按照红色报错命令安装相关依赖后重新打开Mindstudio。

3. 构建Mindstudio工程。

	请检查想要使用Mindstudio运行的工程中是否包含.project和*.iml文件。
	**如果包含，则可以直接使用Mindstudio打开工程，以googlenet_imagenet_picture为例说明。**
	**如果不包含，需要构建Mindstudio工程，以colorization_picture为例说明。**

	- 直接使用Mindstudio打开工程。【googlenet_imagenet_picture】

		- 首次登录MindStudio：单击**Open or Import**，然后选择对应工程，如googlenet_imagenet_picture。
		- 非首次登录MindStudio：在顶部菜单栏中选择**File > Open**，然后选择对应工程，如googlenet_imagenet_picture。

	- 构建Mindstudio工程。【colorization_picture】

		1. 进入工程创建页面。

			- 首次登录MindStudio：单击**Create New Project**。
			- 非首次登录MindStudio：在顶部菜单栏中选择**File > New > Project...**。

		2. 在**New Project**窗口中，选择**Ascend App**，填写工程名称，例如**colorization_picture**。然后点击**Next**。

		3. 在**New Project**窗口中，选择工程类型为**Empty Project**，创建一个仅包括开发框架的工程，不含具体的代码逻辑。单击**Finish**，完成工程创建。

		4. 命令行中执行以下命令，将samples源码复制到Mindstudio空工程中。

			**cp -r ~/samples/c++/level2_simple_inference/6_other/colorization_picture/\* ~/AscendProject/colorization_picture**

		5. 在Mindstudio中右击工程，选择**Reload from Disk**刷新工程即可。

### 样例编译

在Mindstudio右上角点击 Build->Edit Build Configuration... ,进行编译配置。

- 使用产品为200DK开发者板，选择 Target Architecture为aarch64。

选择完成后点击Build开始编译,编译完成后，会在工程中生成build和out文件夹。

### 样例运行

1. 在Mindstudio右上角点击 **Run->Edit Configurations...** ,进行运行配置。

	**Target Host Ip** 选择为已经配置好的运行环境ip地址。一般USB方式连接的200DK为192.168.1.2。

	**Command Arguments** 填写为：**../data**。

	参数填写完成后，点击右下角的**Apply**，再点击**OK**。
	​
	![icon-note.gif](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/160652_6146f6a4_5395865.gif) **说明：**

	> - 如果**Target Host Ip**没有取值，请点击后面的加号图标，自行配置运行环境。

	获取此应用中所需要的原始网络模型。

	参考下表获取此应用中所用到的原始网络模型及其对应的权重文件，并将其存放到开发环境普通用户下的任意目录，例如：$HOME/models/colorization。

	| **模型名称** | **模型说明**           | **模型下载路径**                                             |
	| ------------ | ---------------------- | ------------------------------------------------------------ |
	| colorization | 黑白图像上色推理模型。 | 请参考https://gitee.com/ascend/ModelZoo-TensorFlow/tree/master/TensorFlow/contrib/cv/colorization/ATC_colorization_caffe_AE目录中README.md下载原始模型章节下载模型和权重文件。 |

	![icon-note.gif](https://images.gitee.com/uploads/images/2020/1106/160652_6146f6a4_5395865.gif) **说明：**

	> - modelzoo中提供了转换好的om模型，但此模型不匹配当前样例，所以需要下载原始模型和权重文件后重新进行模型转换。

	将原始模型转换为Davinci模型。

	**注：请确认环境变量已经在[环境准备和依赖安装](https://gitee.com/ascend/samples/blob/v0.4.0/python/environment)中配置完成**

	1. 设置LD_LIBRARY_PATH环境变量。

		![image-20220510112708751](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220510112708751.png)

		

2. 在Mindstudio右上角点击 **Run->Run 'XXX'** ,运行样例。

	运行过程中，会将开发环境中的**data、out、model**文件夹上传到运行环境。并使用**adc**工具执行编译出来的**run.sh**脚本。

3. 查看结果。

	运行完成后，会在Mindstudio中打印输出，部分样例会在Mindstudio的out目录下回传推理处理后的图片













【官方参考文档】[昇腾官网](https://www.hiascend.com/)

>进入昇腾官网--硬件平台--开发者硬件文档
>
>![image-20220428165657125](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428165657125.png)
>
>![image-20220428165813300](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428165813300.png)
>
>这一步设置为中文不影响，可以更直观
>
>![image-20220428165842649](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428165842649.png)
>
>![image-20220428165948908](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220428165948908.png)
>
>- [华为云官网](https://www.huaweicloud.com/)
>
>进入华为云官网，点击右上角的文档--弹出的搜索框中搜索”Mindstudio“--找到涉及版本3.0.1的文档点进去--点击附录--安装依赖包--点击第一个往下拉--找到安装JDK部分进行安装
>
>![image-20220429103134618](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429103134618.png)
>
>![image-20220429103220916](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429103220916.png)
>
>![image-20220429103253627](HUAWEI%20Atlas%20200%20DK%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/image-20220429103253627.png)

