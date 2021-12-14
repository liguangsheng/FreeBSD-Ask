# 第二节 配置

## 1. 准备工作

### 获取驱动

第一次进入系统后，OpenBSD 会自动检测无线、显卡和声卡，并下载相关驱动。静等几分钟，待其自行更新。由于国外网站连接比较慢，如果等待时间过长，可 `Ctrl` + `C` 取消，待进入系统后运行 `# fw_update` 重新获取驱动。

### 桌面支持

上一节安装时，我们屏蔽了桌面选项。这一步我们重新开启。打开 `/etc/sysctl.conf`，添加一行` machdep.allowaperture=2` 。

### 修改软件源

打开 `/etc/installurl` ，将默认源注释掉，改为 `https://mirrors.bfsu.edu.cn/OpenBSD` 。此处我们选择了北外源，用户也可选择 [清华镜像源](https://mirrors.tuna.tsinghua.edu.cn/OpenBSD)、 [阿里镜像源](https://mirrors.aliyun.com/openbsd)、 及[南京大学源](https://mirror.sjtu.edu.cn/OpenBSD) 等。

## 2. 系统更新

### 添加 sudo

终端命令：`# pkg_add sudo`

然后在终端输入 `# visudo` ，然后添加一行 $USER ALL=(ALL) SETENV: ALL （请将 $USER 替换为你的用户名)，保存后退出。

### 内核更新

内核更新：`# syspatch`

驱动升级：`# fw_update`

软件升级：`# pkg_add -u`

修改shell： `chsh`
 
 示例：
 
```    
  # chsh -s /usr/local/bin/bash $USER`
```

## 3. 软件管理

- 查找软件： `# pkg_info -Q foo`

- 安装软件： `# pkg_add foo`

- 升级软件： `# pkg_add -iu foo`


## 4. 主题和图标

以下仅举两个实例，[Qogir](https://www.gnome-look.org/p/1230631/) 主题、和 [Tela](https://www.gnome-look.org/p/1279924/) 图标，大家可访问[相关网站](https://www.gnome-look.org)，自行选择喜欢的主题和图标来安装。

### 提前准备

终端运行 # `pkg_add git bash`

### 主题安装

`git clone https://github.com/vinceliuice/Qogir-theme`
 
`cd Qogir-theme`

`vi .install.sh`，修改文件中的第一行 shebang 为 `#!/usr/local/bin/bash`

`bash ./install.sh`

### 图标安装

`git clone https://github.com/vinceliuice/Tela-icon-theme`

`cd Tela-icon-theme`

`vi .install.sh`，修改文件中的第一行 shebang 为 `#!/usr/local/bin/bash`

`bash ./install.sh`

## 5. 挂载可移动磁盘

### 新建挂载点

```
$ cd ~
$ mkdir media
$ cd media
# mkdir first second third forth
```
### 查看盘符

使用`dmesg`命令来查看新插入的盘符，如格式为 fat32 的 U盘，可能在 OpenBSD 系统里盘符为 sd1 。

### 检查分区

如插入的盘符为 sd1，则输入 `disklabel sd1` 查看分区情况。如下
```
#                size           offset  fstype [fsize bsize   cpg]
 c:         60062500                0  unused                    
 i:         60062244              256   MSDOS    
```

### 挂载

由上则可知分区为 i ，使用以下命令挂载：

`# mount /dev/sd1i /$USER/media/first` ，`$USER` 替换为当前用户名。

### 其它格式

OpenBSD 可挂载的外接硬盘格式有 NTFS、ext2/ext3 以及 CD 磁盘等，具体命令可参考如下：

```
# mount /dev/sd3i /$USER/media/first   # fat32
# mount /dev/sd2k /$USER/media/second  # ntfs
# mount /dev/sd1l /$USER/media/third   # ext2/ext3
# mount /dev/cd0a /$USER/media/forth   # CD
```

### 卸载磁盘

`# umount /$USER/media/first`

## 6. 无线测试

OpenBSD 里的无线网络，配置文件通常是 `hostname.if` ，其中 `if` 为无线驱动名称+序号。如一台笔记本无线型号为 rtl8188cu ，OpenBSD 下驱动为 rtwn ，序号从 0 开始。为了让系统自动加载无线，可打开
 `/etc/hostname.rtwn0` 文件 ，而后添加：

```
dhcp 
nwid '无线名称' wpakey '无线密码'
```
保存后即可。

## 7. 补遗

### 加载触摸板

打开 `/etc/wsconsctl.conf`， 添加一行`mouse.tp.tapping=1` 。

### 加载多线程

打开 `/etc/sysctl.conf` ，添加一行 `hw.smt=1` 。

### 相关资料

- OpenBSD FAQ  推荐

- Absolute OpenBSD 补充

_如果觉得 Firefox 运行不佳，试试 Chromium 。_