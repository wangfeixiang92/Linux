#shutdown

*  介绍
       
       shutdown - Halt, power-off or reboot the machine  
       关机 - 停机，电源断开 或者重启机器

参数说明：

    -t seconds : 设定在几秒钟之后进行关机程序
    -k : 并不会真的关机，只是将警告讯息传送给所有只用者
    -r : 关机后重新开机
    -h : 关机后停机
    -n : 不采用正常程序来关机，用强迫的方式杀掉所有执行中的程序后自行关机
    -c : 取消目前已经进行中的关机动作
    -f : 关机时，不做 fcsk 动作(检查 Linux 档系统)
    -F : 关机时，强迫进行 fsck 动作
    time : 设定关机的时间
    message : 传送给所有使用者的警告讯息


* shutdown -h now  立刻关机
* shutdown  -r now 直接重启
* shutdown +1  1分钟后关机
* shutdown -r + 1 1分钟后重启
* shutdown -r 10:00 10点钟重启
* shutdown -h 10:00 10点钟关机
* shutdown -h +5 “System will shutdown after 5 minutes” //5分钟够关机并显示警告信息

#chgrp
    
* 介绍    
       chgrp命令用于变更文件或目录的所属群组。
        
 * 参数说明
    
        -c或者--change 效果类似于 "-v" 参数，但仅回报更改的部分
            
            例子：
                sudo chgrp -c root a/
                changed group of 'a/' from users to root
                
         -f或者--quie 或 --silent 不显示错误信息 
                
         -h或者--no-dereference 只对符号连接的文件作修改，而不更改其他任何相关文件。
         
            例子：chgrp -h users b.txt 
                  lrwxrwxrwx 1 root users    5 Nov  6 11:53 b.txt -> a.txt
           
         -R或者--recursive 递归处理，将指定目录下的所有文件及子目录一并处理
         
         -v或则--verbose 显示指令执行过程
              
            例子：
                chgrp -Rv users a/
                changed group of 'a/b/c' from root to users
                changed group of 'a/b' from root to users
                changed group of 'a/' from root to users
                
         --help 　在线帮助。
          
         --reference=<参考文件或目录> 　把指定文件或目录的所属群组全部设成和参考文件或目录的所属群组相同。
          
         --version 　显示版本信息。
    
