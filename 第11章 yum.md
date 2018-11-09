#linux yum 命令
    
    yum（ Yellow dog Updater, Modified）是一个在Fedora和RedHat以及SUSE中的Shell前端软件包管理器。
    
    基於RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软体包，无须繁琐地一次次下载、安装。
    
    yum提供了查找、安装、删除某一个、一组甚至全部软件包的命令，而且命令简洁而又好记。

* yum 语法
  
    yum [options] [command] [package ...]
    
    options：可选，选项包括-h（帮助），-y（当安装过程提示选择全部为"yes"），-q（不显示安装的过程）等等。
    
    command：要进行的操作。
    
    package操作的对象。