---
background: https://source.unsplash.com/collection/94734566/1920x1080
class: 'text-center'
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
---

# 前端观察

2022-06-16

---

# 本周分享: Linux 基础学习笔记

<img src="FE_Weekly_2022_06_16/images/p1.jpeg" />

---
class: 'text-center'
---

# 一、计算机

---

## 五大单元

- 输入
- CPU
- 主板
- 存储
- 输出

---
layout: two-cols
---

::default::

## 容量单位

- bit - 0/1
- Byte - 8bit
- Kilo - 1024Byte
- Mega - 1024Kilo
- Giga - 1024Mega
- Tera - 1024Giga
- Peta - 1024Tera
- Exa - 1024Peta
- Zetta - 1024Exa

::right::

## 速度单位

- CPU的运算速度
  - Hz
  - MHz
  - GHz
- 网络传输
  - Mb

---

# 显卡接口

- D-Sub/VGA端子
  - 640x350px @70Hz
  - 1280x1024px @85Hz
  - 2048x1536px @85Hz
- DVI
  - 1920x1200px @60Hz
  - 2560x1600px @60Hz
- HDMI - 同时传送影像与声音
- Display Port - 同时传送影像与声音

---

# USB接口

- USB1.0 - 1.5MByte/s
- USB2.0 - 60MByte/s
- USB3.0 - 500MByte/s
- USB3.1 - 1000MByte/s

---

# CPU架构

- 精简指令集（RISC）
  - 甲骨文 SPARC 系列 - `学术领域的大型工作站/银行金融体系的主要服务器`
  - IBM PowerArchitecture(PowerPC) 系列 - `索尼PS3`
  - 安谋 ARM 系列 - `手机/PDA/导航系统/网络设备/交换器/路由器等(世界上使用范围最广的CPU)`
- 复杂指令集（CISC）
   - AMD/Intel/VIA等的x86架构的CPU - `大量使用于个人电脑`

---

# 二、Linux的历史

- 1960年代初期麻省理工学院（MIT）： 相容分时系统（CTSS）
- 1965年前后，Bell/MIT/GE共同发起了Multics计划
- 1973年：Unix的正式诞生
- 1977年：重要的Unix分支--BSD的诞生
- 1979年：Unix版权宣告，不对学生提供源码
- 1984年：GNU计划与FSF基金会的成立
- 1988年：图形接口XFree86计划
- 1991年：芬兰大学生Linus Torvalds在X86上成功开发了Linux
- 1994年：Linux 内核 1.0 发布，同年Red Hat成立

---
class: 'text-center'
---

# 三、Linux文件权限与属性

---

# Linux文件属性

```
ls -l

-rw-r--r--.  1    root  root    1864  May 4 18:01 initial-setup-ks.cfg
```

---
layout: two-cols
---

::default::

```
-rw-r--r--.  1    root  root    1864  May 4 18:01 initial-setup-ks.cfg
```

- -rw-r--r--
  - 第一个字符
    - d 目录
    - \- 文件
    - l 链接文件
    - b 装置文件里面的可供储存的接口设备
    - c 装置文件里面的串行端口设备，如键盘、鼠标

::right::

  - 接下来以三个为一组，且均为『rwx』的组合
    - r 代表可读(read)
    - w 代表可写(write)
    - x 代表可执行(execute)
    - \- 代表没有权限
    - 第一组『文件拥有者可具备的权限』
    - 第二组『加入此群组之账号的权限』
    - 第三组『非本人且没有加入本群组之其他账号的权限』

---

```
-rw-r--r--.  1    root  root    1864  May 4 18:01 initial-setup-ks.cfg
```

- 第二栏表示有多少文件名连结到此节点(i-node)
- 第三栏表示这个文件(或目录)的『拥有者账号』
- 第四栏表示这个文件的所属群组
- 第五栏为这个文件的容量大小，默认单位为bytes
- 第六栏为这个文件的创建日期或者是最近的修改日期
- 第七栏为这个文件的文件名

---

# 改变文件属性与权限

- **chgrp ：改变文件所属群组**
  - `chgrp [-R] dirname/filename`
- **chown ：改变文件拥有者**
  - `chown [-R] 账号名称 文件或目录`
- **chmod ：改变文件的权限, SUID, SGID, SBIT等等的特性**
  - `chmod [-R] xyz 文件或目录`

---
layout: two-cols
---

::default::

# chmod

- **数字类型改变文件权限**
  - 各权限的分数对照表
    - r: 4
    - w: 2
    - x: 1
  - 每种身份(owner/group/others)各自的三个权限(r/w/x)分数需要累加
    - owner = rwx = 4+2+1 = 7
    - group = rwx = 4+2+1 = 7
    - others= --- = 0+0+0 = 0

```
chmod [-R] xyz 文件或目录
```

::right::

- **符号类型改变文件权限**
  - u, g, o 来代表三种身份的权限
  - a 则代表  all 亦即全部的身份
  - 读写的权限就可以写成 r, w, x

```
chmod  u=rwx,go=rx  .bashrc
chmod  a+w  .bashrc
chmod  a-w  .bashrc
```

---

# 文件种类

- 文件 [-]
  - 纯文本档(ASCII)
  - 二进制文件(binary)
  - 数据格式文件(data)
- 目录 [d]
- 连结档(l) - `类似Windows系统底下的快捷方式`
- 设备与装置文件(device)
  - 区块(block)设备档 [b] - `硬盘与软盘`
  - 字符(character)设备文件 [c] - `键盘鼠标`
- 资料接口文件(sockets) [s]
- 数据输送文件(FIFO, pipe) [p]

---

# Linux目录

- /usr - `软件放置处`
- /opt - `第三方协力软件`
- /etc - `配置文件`
- /boot - `开机与核心档`
- /var/mail - `使用者邮件信箱`
- /var/spool/news - `新闻组`
- /var/run - `程序相关`
- /var/lock - `程序相关`

---
class: 'text-center'
---

# 四、Linux 文件与目录

---

# 比较特殊的目录

- .   `代表此层目录`
- ..   `代表上一层目录`
- \-   `代表前一个工作目录`
- ~   `代表『目前用户身份』所在的家目录`
- ~account   ` 代表account 这个用户的家目录(account是个账号名称)`

---

# 常见的处理目录的指令

 - cd   `变换目录`
 - pwd   `显示当前目录`
 - mkdir   `建立一个新的目录`
   - \-p `   帮助你直接将所需要的目录(包含上层目录)递归建立起来！`
 - rmdir   `删除一个空的目录`
   - \-p `   连同『上层』『空的』目录也一起删除`

---

# 有关文件与目录的一些基础管理部分

- ls   `文件与目录的检视`
- cp   `复制文件或目录`
- rm   `移除文件或目录`
- mv   `移动文件与目录，或更名`
- basename   `取得路径的文件名`
- dirname   `取得路径的目录名称`

---

# 文件内容查阅

- cat  `  由第一行开始显示文件内容`
- tac  `  从最后一行开始显示，可以看出 tac 是cat 的倒着写！`
- nl  `   显示的时候，顺道输出行号！`
- more  ` 一页一页的显示文件内容`
- less  ` 与 more 类似，但是比 more 更好的是，他可以往前翻页！`
- head  ` 只看头几行`
- tail  ` 只看尾巴几行`
- od  `   以二进制的方式读取文件内容！`
- touch  `修改文件时间或建置新档`

---
class: 'text-center'
---

# 五、压缩,打包

---

# 常见的压缩文件扩展名

- *.Z         `compress 程序压缩的文件`
- *.zip       `zip 程序压缩的文件`
- *.gz        `gzip 程序压缩的文件`
- *.bz2       `bzip2 程序压缩的文件`
- *.xz        `xz 程序压缩的文件`
- *.tar       `tar 程序打包的数据，并没有压缩过`
- *.tar.gz    `tar 程序打包的文件，其中并且经过gzip 的压缩`
- *.tar.bz2   `tar 程序打包的文件，其中并且经过bzip2 的压缩`
- *.tar.xz    `tar 程序打包的文件，其中并且经过xz 的压缩`

---

# Linux 系统常见的压缩指令

- gzip `可以说是应用度最广的压缩指令，为了取代compress`
- bzip2 `则是为了取代  gzip 并提供更佳的压缩比`
- xz `压缩比更高的软件`
- tar `打包指令`
  - 压缩：`tar -zcv -f filename.tar.gz 要被压缩的文件或目录名称`
  - 查询：`tar -ztv -f filename.tar.gz`
  - 解压缩：`tar -zxv -f filename.tar.gz -C 欲解压缩的目录`

---
class: 'text-center'
---

# 六、BASH

---

# bash 默认的组合键

- Ctrl + C `终止目前的命令`
- Ctrl + D `输入结束(EOF)，例如邮件结束的时候；`
- Ctrl + M `就是Enter 啦！`
- Ctrl + S `暂停屏幕的输出`
- Ctrl + Q `恢复屏幕的输出`
- Ctrl + U `在提示字符下，将整列命令删除`
- Ctrl + Z `『暂停』目前的命令`

---

# 数据流重导向

- 标准输入(stdin) ：代码为 0 ，使用 `< 或 <<`
- 标准输出(stdout)：代码为 1 ，使用 `> 或 >>`
- 标准错误输出(stderr)：代码为 2 ，使用 `2> 或2>>`

---

# 命令执行的判断依据

- ; `不考虑指令相关性的连续指令下达`
- && `如果前一个命令执行成功，则执行后一个命令`
- || `如果前一个命令执行失败，则执行后一个命令`
- $? `命令执行的结果`

---
class: 'text-center'
---

# 七、Shell Scripts

---

# 如何执行脚本

- 直接指令下达：  `shell.sh 文件必须要具备可读与可执行(rx) 的权限`
  - 绝对路径：`使用  /home/dmtsai/shell.sh 来下达指令`
  - 相对路径：`假设工作目录在  /home/dmtsai/ ，则使用  ./shell.sh 来执行`
  - 变量『PATH』功能：`将  shell.sh 放在  PATH 指定的目录内，例如：  ~/bin/`
- 以bash 程序来执行：`透过『  bash shell.sh 』或『sh shell.sh 』来执行`
- 利用  source  来执行脚本：`在父程序中执行`

---

# Shell script 的默认变数($0, $1...)

- $0, $1... `数字变量`
- $# ：`代表后接的参数『个数』，以上表为例这里显示为『 4 』`
- $@ ：`代表『 "$1" "$2" "$3" "$4" 』之意，每个变量是独立的(用双引号括起来)`
- $* ：`代表『"$1c   $2c$3c$4" 』，其中 c 为分隔字符，默认为空格键`
- shift：`造成参数变量号码偏移`

---

# 判断

- 利用  test  指令的测试功能 `test -e filename` 来判断文件是否存在
- 判断符号  [ -e filename ]

---

# 条件判断式

- 单层、简单条件判断式: 

```
if [条件判断式]; then 
... 
fi
```

- 多重、复杂条件判断式: 

```
if [条件判断式]; then 
... 
elif [条件判断式二]; then 
... 
else 
... 
fi
```