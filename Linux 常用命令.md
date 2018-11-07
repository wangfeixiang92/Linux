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
    
 # chown 
           
  *   更改文件宿主，同时也可以更改文件属组
        
            chown [-R] 属主名 文件名
            chown [-R] 属主名：属组名 文件名
  - 语法
            
            chown [-cfhvR] [--help] [--version] user[:group] file...
            
            user : 新的文件拥有者的使用者 ID
            
            group : 新的文件拥有者的使用者组(group)
            
            -c : 显示更改的部分的信息
            
            -f : 忽略错误信息
            
            -h :修复符号链接
            
            -v : 显示详细的处理信息
            
            -R : 处理指定目录以及其子目录下的所有文件
            
            --help : 显示辅助说明
            
            --version : 显示版本
 *  例子
            
            eg:
                sudo chown -Rv  root a/
                ownership of 'a/b/c' retained as root
                ownership of 'a/b' retained as root
                ownership of 'a/' retained as root
                
            eg:
            
                sudo chown -Rv root:root a/
                changed ownership of 'a/b/c' from www-data:www-data to root:root
                changed ownership of 'a/b' from www-data:www-data to root:root
                changed ownership of 'a/' from www-data:www-data to root:root
             
            eg:
                sudo chown -vh www-data b.txt
                changed ownership of 'b.txt' from root to www-data
                

# chmod
            
   *    Linux/Unix 的文件调用权限分为三级 : 文件拥有者、群组、其他。利用 chmod 可以藉以控制文件如何被他人所调用。
        
        使用权限 : 所有使用者更改文件9个属性            
    
   *    语法
        
            chmod [-cfvR] [--help] [--version] mode file... 
            
            其中：
            
            u 表示该文件的拥有者，g 表示与该文件的拥有者属于同一个群体(group)者，o 表示其他以外的人，a 表示这三者皆是。
            
            + 表示增加权限、- 表示取消权限、= 表示唯一设定权限。
            
            r 表示可读取，w 表示可写入，x 表示可执行，X 表示只有当该文件是个子目录或者该文件已经被设定过为可执行。
            
            
            其他参数说明：
            
            -c : 若该文件权限确实已经更改，才显示其更改动作
            
            -f : 若该文件权限无法被更改也不要显示错误讯息
            
            -v : 显示权限变更的详细资料
            
            -R : 对目前目录下的所有文件与子目录进行相同的权限变更(即以递回的方式逐个变更)
            
            --help : 显示辅助说明
            
            --version : 显示版本
            
   *    例子
        
                   eg:
                       sudo chmod  -Rv ugo+r a/
                       mode of 'a/' changed from 0000 (---------) to 0444 (r--r--r--)
                       mode of 'a/b' changed from 0000 (---------) to 0444 (r--r--r--)
                       mode of 'a/b/c' changed from 0000 (---------) to 0444 (r--r--r--)     
                       
                   eg:
                        
                        sudo chmod -Rv u=rwx,g+w,o-r a/
                        mode of 'a/' changed from 0444 (r--r--r--) to 0760 (rwxrw----)
                        mode of 'a/b' changed from 0444 (r--r--r--) to 0760 (rwxrw----)
                        mode of 'a/b/c' changed from 0444 (r--r--r--) to 0760 (rwxrw----)
                        
                   eg:
                        
                        sudo chmod -Rv 000 a/
                        mode of 'a/' changed from 0760 (rwxrw----) to 0000 (---------)
                        mode of 'a/b' changed from 0760 (rwxrw----) to 0000 (---------)
                        mode of 'a/b/c' changed from 0760 (rwxrw----) to 0000 (---------)
                        
                    eg:
                        
                        sudo chmod -Rv 777 a.txt
                        mode of 'a.txt' changed from 0644 (rw-r--r--) to 0777 (rwxrwxrwx)