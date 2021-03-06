#shell 教程
    
    Shell 是一个用 C 语言编写的程序，它是用户使用 Linux 的桥梁。Shell 既是一种命令语言，又是一种程序设计语言。
    
    Shell 是指一种应用程序，这个应用程序提供了一个界面，用户通过这个界面访问操作系统内核的服务。
    
    Ken Thompson 的 sh 是第一种 Unix Shell，Windows Explorer 是一个典型的图形界面 Shell。
    
#shell 脚本
       
       Shell 脚本（shell script），是一种为 shell 编写的脚本程序。
       
       业界所说的 shell 通常都是指 shell 脚本，但读者朋友要知道，shell 和 shell script 是两个不同的概念。
       
       由于习惯的原因，简洁起见，本文出现的 "shell编程" 都是指 shell 脚本编程，不是指开发 shell 自身。
       
#shell 和shell的区别？
       
      shell和shell脚本有什么区别？确切一点说，Shell就是一个命令行解释器,它的作用就是遵循一定的语法将输入的命令加以解释并传给系统。它为用户提供了一个向Linux发送请求以便运行程序的接口系统级程序，用户可以用Shell来启动、挂起、停止甚至是编写一些程序。 Shell本身是一个用C语言编写的程序，它是用户使用Linux的桥梁。Shell既是一种命令语言，又是一种程序设计语言(就是你所说的shell脚本)。作为命令语言，它互动式地解释和执行用户输入的命令；作为程序设计语言，它定义了各种变量和参数，并提供了许多在高阶语言中才具有的控制结构，包括循环和分支。它虽然不是 Linux系统内核的一部分，但它调用了系统内核的大部分功能来执行程序、创建文档并以并行的方式协调各个程序的运行。
      
#第一个shell脚本
        
        #!bin/bash
        echo 'Hello world !'
        
        #! 是一个约定的标记，它告诉系统这个脚本需要什么解释器来执行，即用哪一种 Shell。
        
        Linux 教程
        Linux 教程
        Linux 简介
        Linux 安装
        Linux 系统启动过程
        Linux 系统目录结构
        Linux 忘记密码解决方法
        Linux 远程登录
        Linux 文件基本属性
        Linux 文件与目录管理
        Linux 用户和用户组管理
        Linux 磁盘管理
        Linux vi/vim
        linux yum 命令
        
        Shell 教程
        Shell 教程
        Shell 变量
        Shell 传递参数
        Shell 数组
        Shell 运算符
        Shell echo命令
        Shell printf命令
        Shell test 命令
        Shell 流程控制
        Shell 函数
        Shell 输入/输出重定向
        Shell 文件包含
        
        Linux 参考手册
        Linux 命令大全
        Nginx 安装配置
        MySQL 安装配置
         linux yum 命令 Shell 变量 
        Shell 教程
        Shell 是一个用 C 语言编写的程序，它是用户使用 Linux 的桥梁。Shell 既是一种命令语言，又是一种程序设计语言。
        
        Shell 是指一种应用程序，这个应用程序提供了一个界面，用户通过这个界面访问操作系统内核的服务。
        
        Ken Thompson 的 sh 是第一种 Unix Shell，Windows Explorer 是一个典型的图形界面 Shell。
        
        Shell 在线工具
        
        Shell 脚本
        Shell 脚本（shell script），是一种为 shell 编写的脚本程序。
        
        业界所说的 shell 通常都是指 shell 脚本，但读者朋友要知道，shell 和 shell script 是两个不同的概念。
        
        由于习惯的原因，简洁起见，本文出现的 "shell编程" 都是指 shell 脚本编程，不是指开发 shell 自身。
        
        Shell 环境
        Shell 编程跟 java、php 编程一样，只要有一个能编写代码的文本编辑器和一个能解释执行的脚本解释器就可以了。
        
        Linux 的 Shell 种类众多，常见的有：
        
        Bourne Shell（/usr/bin/sh或/bin/sh）
        Bourne Again Shell（/bin/bash）
        C Shell（/usr/bin/csh）
        K Shell（/usr/bin/ksh）
        Shell for Root（/sbin/sh）
        ……
        本教程关注的是 Bash，也就是 Bourne Again Shell，由于易用和免费，Bash 在日常工作中被广泛使用。同时，Bash 也是大多数Linux 系统默认的 Shell。
        
        在一般情况下，人们并不区分 Bourne Shell 和 Bourne Again Shell，所以，像 #!/bin/sh，它同样也可以改为 #!/bin/bash。
        
        #! 告诉系统其后路径所指定的程序即是解释此脚本文件的 Shell 程序。
        
        第一个shell脚本
        打开文本编辑器(可以使用 vi/vim 命令来创建文件)，新建一个文件 test.sh，扩展名为 sh（sh代表shell），扩展名并不影响脚本执行，见名知意就好，如果你用 php 写 shell 脚本，扩展名就用 php 好了。
        
        输入一些代码，第一行一般是这样：
        
        实例
        #!/bin/bash
        echo "Hello World !"
        
        运行实例 »
        #! 是一个约定的标记，它告诉系统这个脚本需要什么解释器来执行，即使用哪一种 Shell。
        
        echo 命令用于向窗口输出文本。
        
 # 运行 Shell 脚本有两种方法：
  * 1、作为可执行程序
        
        将上面的代码保存为 test.sh，并 cd 到相应目录：
        
        chmod +x ./test.sh  #使脚本具有执行权限
        ./test.sh  #执行脚本
        
        注意，一定要写成 ./test.sh，而不是 test.sh，运行其它二进制的程序也一样，直接写 test.sh，linux 系统会去 PATH 里寻找有没有叫 test.sh 的，而只有 /bin, /sbin, /usr/bin，/usr/sbin 等在 PATH 里，你的当前目录通常不在 PATH 里，所以写成 test.sh 是会找不到命令的，要用 ./test.sh 告诉系统说，就在当前目录找。
        
        
  * 2、作为解释器参数
  
             获取去掉#!/bin/bash
           
             然后 执行/bin/sh hello.sh
             
             这种方式运行的脚本，不需要在第一行指定解释器信息，写了也没用。