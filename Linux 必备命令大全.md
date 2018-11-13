# Linux命令

* 文件管理
* 文档编辑
* 文件传输
* 磁盘管理
* 磁盘维护
* 网络通讯
* 系统管理
* 系统设置
* 备份压缩
* 设备管理
* 其他命令

#文件管理

#cat      用于连接文件并打印到标准输出设备上

* cat -n a.txt  对内容进行行号编码
* cat -b a.txt  对内容进行行号编码 不编码空白行
* cat -s a.txt  当遇到有连续两行以上的空白行，就代换为一行的空白行
* cat -bs a.txt >a.log  对a.txt里的内容进行行号编码然后输出到a.log里
* cat -bs a.txt  b.txt  > a.log 把a.txt b.txt的内容编码输入到a.log里  
* cat /dev/null > a.log  把a.log 清空


#chgrp  变更文件或者目录的所属权限

* chgrp -R wfx a/  遍历更改a/目录的属组为wfx

#chmod 修改文件或者目录的权限

* chmod -R 777 a/   遍历更改a/的权限为777
* sudo chmod -R u=rwx,g+rw,o-wx a/  遍历给 a/赋权限

#chown 变更文件或者目录的所有者或者所属组

*  sudo chown -R wfx a/ 遍历变更a/的所有者
*  sudo chown -R root:root a/ 遍历变更 a/的所有者，所有组

#cksum 检查文件的CRC是否正确。确保文件从一个系统传输给另外一个系统的过程中不被损坏。

* cksum a.txt
* sudo cksum /dev/sda2

#cmp 用于比较两个文件是否有差异

* cmp a.txt b.txt  比较a.txt b.txt 之间是否存在差异

#diff 逐行比较文件差异

* diff a.txt b.tx  比较两个文本之间的差异
* diff -y  a.txt b.txt  以并列的方式显示两个文本的差异
* diff a.txt b.tx -y -W 50 以并列50个字符的宽度展示两个文本之间的差异




# 系统管理

#shutdown   关机
    
* shutdown -h now  立刻关机
* shutdown -r now 立刻重启
* shutdown +10  10分钟后关机
* shutdown -r +10 10分钟后重启
* shutdown -h 10:00 10点关机
* shutdown -r 10:00 10点重启
* shutdown -h +10 'this system will closed after 10 min' 10分钟后关机并发送消息给所有人

#halt   关闭系统

* halt  关闭系统

#reboot 重启系统

* reboot  重启系统