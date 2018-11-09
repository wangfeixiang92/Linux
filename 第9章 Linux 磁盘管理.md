#Linux 磁盘管理

    Linux磁盘管理好坏直接关系到整个系统的性能问题。
    
    Linux磁盘管理常用三个命令为df、du和fdisk。
    
    df：列出文件系统的整体磁盘使用量
    du：检查磁盘空间使用量
    fdisk：用于磁盘分区
    
    
#df  检查文件系统的磁盘空间占用情况
    
        可以利用该命令来获取硬盘被占用了多少空间，目前还剩下多少空间等信息。
        
* 语法
    
        df [-ahikHTm] [目录或文件名]
        
* 选项    
        
        -a ：列出所有的文件系统，包括系统特有的 /proc 等文件系统；
        -k ：以 KBytes 的容量显示各文件系统；
        -m ：以 MBytes 的容量显示各文件系统；
        -h ：以人们较易阅读的 GBytes, MBytes, KBytes 等格式自行显示；
        -H ：以 M=1000K 取代 M=1024K 的进位方式；
        -T ：显示文件系统类型, 连同该 partition 的 filesystem 名称 (例如 ext3) 也列出；
        -i ：不用硬盘容量，而以 inode 的数量来显示
        
* 例子    
        
        eg:
            
             df -ah
            Filesystem      Size  Used Avail Use% Mounted on
            sysfs              0     0     0    - /sys
            proc               0     0     0    - /proc
            udev            487M     0  487M   0% /dev
            devpts             0     0     0    - /dev/pts
            tmpfs           100M  4.4M   95M   5% /run
            /dev/sda1       9.7G  2.3G  7.4G  24% /
            securityfs         0     0     0    - /sys/kernel/security
            tmpfs           497M     0  497M   0% /dev/shm
            tmpfs           5.0M     0  5.0M   0% /run/lock
            tmpfs           497M     0  497M   0% /sys/fs/cgroup
            cgroup             0     0     0    - /sys/fs/cgroup/systemd
            pstore             0     0     0    - /sys/fs/pstore
            cgroup             0     0     0    - /sys/fs/cgroup/blkio
            cgroup             0     0     0    - /sys/fs/cgroup/cpuset
            cgroup             0     0     0    - /sys/fs/cgroup/freezer
            cgroup             0     0     0    - /sys/fs/cgroup/hugetlb
            cgroup             0     0     0    - /sys/fs/cgroup/cpu,cpuacct
            cgroup             0     0     0    - /sys/fs/cgroup/net_cls,net_prio
            cgroup             0     0     0    - /sys/fs/cgroup/perf_event
            cgroup             0     0     0    - /sys/fs/cgroup/devices
            cgroup             0     0     0    - /sys/fs/cgroup/memory
            cgroup             0     0     0    - /sys/fs/cgroup/pids
            systemd-1          -     -     -    - /proc/sys/fs/binfmt_misc
            debugfs            0     0     0    - /sys/kernel/debug
            mqueue             0     0     0    - /dev/mqueue
            hugetlbfs          0     0     0    - /dev/hugepages
            fusectl            0     0     0    - /sys/fs/fuse/connections
            lxcfs              0     0     0    - /var/lib/lxcfs
            vagrant         416G  3.0G  413G   1% /vagrant
            vagrant_data    416G  3.0G  413G   1% /vagrant_data
            binfmt_misc        0     0     0    - /proc/sys/fs/binfmt_misc
            tmpfs           100M     0  100M   0% /run/user/1000
            
            eg:
                
            df -h /etc/
            Filesystem      Size  Used Avail Use% Mounted on
            /dev/sda1       9.7G  2.3G  7.4G  24% /


#du  查看使用空间
    
    du命令也是查看使用空间的，但是与df命令不同的是Linux du命令是对文件和目录磁盘使用的空间的查看，还是和df命令有一些区别的
    
   * du [-ahskm] 文件或目录名称
   
        -a ：列出所有的文件与目录容量，因为默认仅统计目录底下的文件量而已。
        -h ：以人们较易读的容量格式 (G/M) 显示；
        -s ：列出总量而已，而不列出每个各别的目录占用容量；
        -S ：不包括子目录下的总计，与 -s 有点差别。
        -k ：以 KBytes 列出容量显示；
        -m ：以 MBytes 列出容量显示；
        
   * 例子
        
            eg:
                sudo du -hs /etc/
                24M     /etc/
            
            eg:
            sudo du -sm /etc/
            24      /etc/
            
            eg:
            sudo du -sk /etc/
            24104   /etc/                        

#fdisk  fdisk是Linux的磁盘分区表操作工具

    fdisk [-l] 装置名称
    
    -l ：输出后面接的装置所有的分区内容。若仅有 fdisk -l 时， 则系统将会把整个系统内能够搜寻到的装置的分区均列出来。                    
        
    eg:
        
         sudo fdisk -l
        Disk /dev/sda: 10 GiB, 10737418240 bytes, 20971520 sectors
        Units: sectors of 1 * 512 = 512 bytes
        Sector size (logical/physical): 512 bytes / 512 bytes
        I/O size (minimum/optimal): 512 bytes / 512 bytes
        Disklabel type: dos
        Disk identifier: 0x22d6be0a
        
        Device     Boot Start      End  Sectors Size Id Type
        /dev/sda1  *     2048 20971486 20969439  10G 83 Linux
        
        
        Disk /dev/sdb: 10 MiB, 10485760 bytes, 20480 sectors
        Units: sectors of 1 * 512 = 512 bytes
        Sector size (logical/physical): 512 bytes / 512 bytes
        I/O size (minimum/optimal): 512 bytes / 512 bytes
        
#mkfs 磁盘格式化

    磁盘分割完毕后自然就是要进行文件系统的格式化，格式化的命令非常的简单，使用 mkfs（make filesystem） 命令。
    
    语法：mkfs [-t 文件系统格式] 装置文件名
    
    选项与参数：
    
    -t ：可以接文件系统格式，例如 ext3, ext2, vfat 等(系统有支持才会生效)
       
#fsck 磁盘检验

    fsck（file system check）用来检查和维护不一致的文件系统。
    
    若系统掉电或磁盘发生问题，可利用fsck命令对文件系统进行检查。
    
    语法：
     
     fsck [-t 文件系统] [-ACay] 装置名称
     
  * 选项
      
      -t : 给定档案系统的型式，若在 /etc/fstab 中已有定义或 kernel 本身已支援的则不需加上此参数
      -s : 依序一个一个地执行 fsck 的指令来检查
      -A : 对/etc/fstab 中所有列出来的 分区（partition）做检查
      -C : 显示完整的检查进度
      -d : 打印出 e2fsck 的 debug 结果
      -p : 同时有 -A 条件时，同时有多个 fsck 的检查一起执行
      -R : 同时有 -A 条件时，省略 / 不检查
      -V : 详细显示模式
      -a : 如果检查有错则自动修复
      -r : 如果检查有错则由使用者回答是否修复
      -y : 选项指定检测每个文件是自动输入yes，在不确定那些是不正常的时候，可以执行 # fsck -y 全部检查修复。
      
#mount  磁盘的挂载与卸载
        
        Linux 的磁盘挂载使用 mount 命令，卸载使用 umount 命令。
        
        磁盘挂载语法：
        
        mount [-t 文件系统] [-L Label名] [-o 额外选项] [-n]  装置文件名  挂载点
        
#umont 磁盘的卸载命令
        
        umount [-fn] 装置文件名或挂载点
        
        -f ：强制卸除！可用在类似网络文件系统 (NFS) 无法读取到的情况下；
        -n ：不升级 /etc/mtab 情况下卸除。                              