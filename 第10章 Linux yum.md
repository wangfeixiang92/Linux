#yum 命令
    
    yum（ Yellow dog Updater, Modified）是一个在Fedora和RedHat以及SUSE中的Shell前端软件包管理器。
    
    基於RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软体包，无须繁琐地一次次下载、安装。
    
    yum提供了查找、安装、删除某一个、一组甚至全部软件包的命令，而且命令简洁而又好记。
    
#yum语法
     
     yum [options] [command] [package ...]
     
     options：可选，选项包括-h（帮助），-y（当安装过程提示选择全部为"yes"），-q（不显示安装的过程）等等。
     command：要进行的操作。
     package操作的对象。
     
#yum 常用命令
      
  * yum check-update 列出所有可更新的软件清单
  
  * yum update  更新所有软件
  
  * yum install <package_name>  安装指定的软件命令
  
  * yum update <package_name> 更新指定的软件
  
  * yum list    列出所有的已经安装的软件的命令
  
  * yum list redis.*  匹配查找
  
  * yum remove <package_name>  删除软件
  
  * yum search <keyword>  查看已经软件
  
  * yum clean packages  清除缓存目录下的软件包
  
  * yum clean headers  清除缓存目录下的headers
  
  * yum clean oldheaders 清除缓存目录下旧的headers
  
  * yum clean           清除缓存目录下的软件包及旧的headers
  
  * yum clean all       清除缓存目录下的软件包及旧的headers
  
  
  * 列子
        
        
        yum install -y  pam-devel  安装pam--devel
        
        yum remove pam-devel  移除 pam-devel
        
        yum list pam*          找出pam开头的软件
        
        
   * 扩展
           


        配置本地Yum仓库
        
        实现此案例需要按照如下步骤进行。
        
        步骤一：搭建一个本地Yum，将RHEL6光盘手动挂载到/media
        
        命令操作如下所示：
        
        [root@localhost ~]# mount /dev/cdrom /media/
        mount: block device /dev/sr0 is write-protected, mounting read-only
        [root@localhost ~]# mount | tail -1
        /dev/sr0 on /media type iso9660 (ro)
        步骤二：将本地设置为客户端，进行Yum验证
        
        Yum客户端需编辑配置文件，命令操作如下所示：
        
        [root@localhost ~]# cd /etc/yum.repos.d/         //必须在这个路径下
        [root@localhost yum.repos.d]# ls                  //此路径下事先有配置文件的模板
        rhel-source.repo
        
        [root@localhost yum.repos.d]# cp rhel-source.repo rhel6.repo //配置文件必须以.repo结尾
        [root@localhost yum.repos.d]# vim rhel6.repo
        [rhel-6]                                     //中括号里内容要求唯一，但不要出现特殊字符
        name=Red Hat Enterprise Linux 6           //此为描述信息，可以看情况填写
        baseurl=file:///media/                     //此项为yum软件仓库位置，指向光盘挂载点
        enabled=1                                   //此项为是否开启，1为开启0为不开启
        gpgcheck=1                                  //此项为是否检查签名，1为监测0为不检测
        gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release  //签名认证信息的路径
        
        [root@localhost /]# yum repolist
        Loaded plugins: product-id, refresh-packagekit, security, subscription-manager
        This system is not registered to Red Hat Subscription Management. You can use subscription-manager to register.
        rhel-6                                            | 3.9 kB     00:00 ... 
        rhel-6/primary_db                                  | 3.1 MB     00:00 ... 
        repo id             repo name                                     status
        rhel-6              Red Hat Enterprise Linux 6                    3,690
        repolist: 3,690


   
  * 缺少依赖库
  
        对于 Linux 软件安装时提示缺失库的，可以使用 yum 的 provides 参数查看 libstdc++.so.6 的库文件包含在那个安装包中只需要执行：
        
        yum provides libstdc++.so.6
        然后按查询到安装包包名，使用 yum install 安装即可。
        
      