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
                        
                        
#ls
    
   *   Linux ls命令用于显示指定工作目录下之内容（列出目前工作目录所含之文件及子目录)。
   
   *    语法
        
             ls [-alrtAFR] [name...]
             
   *    参数 
             
             -a 显示所有文件及目录 ,列出隐藏文件
             
             -l 除文件名称外，亦将文件型态、权限、拥有者、文件大小等资讯详细列出
             
             -r 将文件以相反次序显示(原定依英文字母次序)
             
             -t 将文件依建立时间之先后次序列出
             
             -A 同 -a ，但不列出 "." (目前目录) 及 ".." (父目录)
             
             -F 在列出的文件名称后加一符号；例如可执行档则加 "*", 目录则加 "/"
             
             -R 若目录下有文件，则以下之文件亦皆依序列出
             
   *    例子
            
            eg:
                
                $ ls
                a  a.txt  b.txt
                
            eg: 
                
                 ls -a
                    .  ..  a  a.txt  b.txt  .test.txt         
                    
            eg:
                
                ls -l
                total 4
                d--------- 3 root     root     4096 Nov  1 10:13 a
                -rwxrwxrwx 1 root     users       0 Nov  1 10:09 a.txt
                lrwxrwxrwx 1 www-data www-data    5 Nov  6 11:53 b.txt -> a.txt
                
            eg:
                
                 ls -r
                b.txt  a.txt  a
            
            eg:
                
                 ls -t
                b.txt  a  a.txt
                
            eg:
                
                 ls -A
                a  a.txt  b.txt  .test.txt
            
            eg:
                
                ls-F              
                a/  a.txt*  b.txt@                                                                                                                         
                
            eg:
                
                 ls -R
                .:
                a  a.txt  b.txt
                
            eg:
                
                ls -AF
                a/  a.txt*  b.txt@  .test.txt
                
            eg:
                
                 ls -Alt
                total 4
                -rw-r--r-- 1 root     root        0 Nov  7 06:56 .test.txt
                lrwxrwxrwx 1 www-data www-data    5 Nov  6 11:53 b.txt -> a.txt
                d--------- 3 root     root     4096 Nov  1 10:13 a
                -rwxrwxrwx 1 root     users       0 Nov  1 10:09 a.txt
                
            eg:
                
                sudo ls -lR a/
                a/:
                total 4
                d--------- 3 root root 4096 Nov  1 10:13 b
                
                a/b:
                total 4
                d--------- 2 root root 4096 Nov  1 10:13 c
                
                a/b/c:
                total 0
                
            eg:
                
                 sudo ls -AlRf a/
                a/:
                ..  .  b
                
                a/b:
                ..  .  c
                
                a/b/c:
                ..  .
                
                
#cd
    
   *    cd是Change Directory的缩写，这是用来变换工作目录的命令。
    
   *    语法
        
            cd [dirName]  dirName：要切换的目标目录。
            
   *
               eg:
               
                cd
               ubuntu@ubuntu-xenial:~$
               
               eg:
               
               cd ~
               ubuntu@ubuntu-xenial:~$
               
               eg:
               
               cd /home/test/
               ubuntu@ubuntu-xenial:/home/test$
               
               eg:
               
               cd ..
               ubuntu@ubuntu-xenial:/home$
               
#pwd

   *   pwd 是 Print Working Directory 的缩写，也就是显示目前所在目录的命令。
   
   *   语法
   
        pwd [--help][--version]
        参数说明:
        
        -P ：显示出确实的路径，而非使用连结 (link) 路径。
        --help 在线帮助。
        --version 显示版本信息。
        
   *   例子
   
        eg:
            
            pwd
            /home/test
            
        eg:
            
             pwd -P
            /home/test
            
        eg:
            
            ubuntu@ubuntu-xenial:/var/lock$ pwd
            /var/lock
            ubuntu@ubuntu-xenial:/var/lock$ pwd -P
            /run/lock                    
                                                                 
                                                                
#mkdir
        
        如果想要创建新的目录的话，那么就使用mkdir (make directory)吧。
        
   *    语法
            
            mkdir [-mp] 目录名称
            
   * 参数
            
            -m ：配置文件的权限喔！直接配置，不需要看默认权限 (umask) 的脸色～
            -p ：帮助你直接将所需要的目录(包含上一级目录)递归创建起来！
            
   *  例子
            
            eg:
            
            sudo mkdir -m 777 test1
                ubuntu@ubuntu-xenial:/home/test$ ll
                total 16
                drwxr-xr-x 4 root     root     4096 Nov  7 07:30 ./
                drwxr-xr-x 4 root     root     4096 Nov  1 10:08 ../
                d--------- 3 root     root     4096 Nov  1 10:13 a/
                -rwxrwxrwx 1 root     users       0 Nov  1 10:09 a.txt*
                lrwxrwxrwx 1 www-data www-data    5 Nov  6 11:53 b.txt -> a.txt*
                drwxrwxrwx 2 root     root     4096 Nov  7 07:30 test1/
                -rw-r--r-- 1 root     root        0 Nov  7 06:56 .test.txt    
              
              
              eg:
                
            sudo mkdir -p b1/b2/b3
                ubuntu@ubuntu-xenial:/home/test$ ll
                total 28
                drwxr-xr-x 7 root     root     4096 Nov  7 07:33 ./
                drwxr-xr-x 4 root     root     4096 Nov  1 10:08 ../
                d--------- 3 root     root     4096 Nov  1 10:13 a/
                drwxr-xr-x 3 root     root     4096 Nov  7 07:32 a1/
                -rwxrwxrwx 1 root     users       0 Nov  1 10:09 a.txt*
                drwxr-xr-x 3 root     root     4096 Nov  7 07:33 b1/
                lrwxrwxrwx 1 www-data www-data    5 Nov  6 11:53 b.txt -> a.txt*
                drwxr-xr-x 3 root     root     4096 Nov  7 07:31 t1/
                drwxrwxrwx 2 root     root     4096 Nov  7 07:30 test1/
                -rw-r--r-- 1 root     root        0 Nov  7 06:56 .test.txt  
                
            eg:
                
                sudo mkdir -pm 770 a1/b1/c1  
                
                -p 和-m 一起执行，只有-p会生效
                

#rmdir 
        
   * 删除空目录
           
            
   * 语法  
   
             rmdir [-p] 目录名称
             
             -p ：连同上一级『空的』目录也一起删除
    
   * 例子 
   
            eg:
            
                 sudo rmdir test1/
                 
            eg:
            
                udo rmdir a  
                rmdir: failed to remove 'a': Directory not empty
                
             eg:
              sudo rmdir -p b1/b2/b3/
              ubuntu@ubuntu-xenial:/home/test$ ll
              total 16
              drwxr-xr-x 4 root     root     4096 Nov  7 08:31 ./
              drwxr-xr-x 4 root     root     4096 Nov  1 10:08 ../
              d--------- 3 root     root     4096 Nov  1 10:13 a/
              -rwxrwxrwx 1 root     users       0 Nov  1 10:09 a.txt*
              lrwxrwxrwx 1 www-data www-data    5 Nov  6 11:53 b.txt -> a.txt*
              drwxr-xr-x 3 root     root     4096 Nov  7 07:31 t1/
              -rw-r--r-- 1 root     root        0 Nov  7 06:56 .test.txt
              
              不过要注意的是，这个 rmdir 仅能删除空的目录，你可以使用 rm 命令来删除非空目录。
              

#cp
        
   *    复制文件或者目录       
   
   * 语法
            
            cp [-adfilprsu] 来源档(source) 目标档(destination)
            
   *  参数
            
            -a：相当於 -pdr 的意思，至於 pdr 请参考下列说明；(常用)
            
            -d：若来源档为连结档的属性(link file)，则复制连结档属性而非文件本身；
            
            -f：为强制(force)的意思，若目标文件已经存在且无法开启，则移除后再尝试一次；
            
            -i：若目标档(destination)已经存在时，在覆盖时会先询问动作的进行(常用)
            
            -l：进行硬式连结(hard link)的连结档创建，而非复制文件本身；
            
            -p：连同文件的属性一起复制过去，而非使用默认属性(备份常用)；
            
            -r：递归持续复制，用於目录的复制行为；(常用)
            
            -s：复制成为符号连结档 (symbolic link)，亦即『捷径』文件；
            
            -u：若 destination 比 source 旧才升级 destination ！
            
   * 例子
            
                                                  
            eg:
                
                sudo cp -d b.txt c.txt
                ubuntu@ubuntu-xenial:/home/test$ ll
                total 8
                drwxr-xr-x 2 root     root     4096 Nov  7 08:47 ./
                drwxr-xr-x 4 root     root     4096 Nov  1 10:08 ../
                -rwxrwxrwx 1 www-data www-data    0 Nov  7 08:43 a.txt*
                lrwxrwxrwx 1 root     root        5 Nov  7 08:46 b.txt -> a.txt*
                lrwxrwxrwx 1 root     root        5 Nov  7 08:47 c.txt -> a.txt*      
                
                正常复制的话，cp 会直接复制a.txt 产生一点新文件  -d 的的参数则表示只复制链接文件 而不是复制原来的文件
            
           
            eg:
                
                sudo cp -f a.txt d.txt
                ubuntu@ubuntu-xenial:/home/test$ ll
                total 16
                drwxr-xr-x 2 root     root     4096 Nov  7 09:00 ./
                drwxr-xr-x 4 root     root     4096 Nov  1 10:08 ../
                -rwxrwxrwx 1 www-data www-data   15 Nov  7 09:00 a.txt*
                lrwxrwxrwx 1 root     root        5 Nov  7 08:46 b.txt -> a.txt*
                lrwxrwxrwx 1 root     root        5 Nov  7 08:47 c.txt -> a.txt*
                -rwxr-xr-x 1 root     root       15 Nov  7 09:01 d.txt*
                lrwxrwxrwx 1 root     root        5 Nov  7 08:55 e.txt -> a.txt*
                -rwxr-xr-x 1 root     root        0 Nov  7 08:55 f.txt*
                -rwxr-xr-x 1 root     root        0 Nov  7 08:59 h.txt*
                
                     
                     
             eg:
                     
                 /home/test$ sudo cp -i a.txt h.txt
                     cp: overwrite 'h.txt'? y
                     ubuntu@ubuntu-xenial:/home/test$ ll
                     total 20
                     drwxr-xr-x 2 root     root     4096 Nov  7 09:00 ./
                     drwxr-xr-x 4 root     root     4096 Nov  1 10:08 ../
                     -rwxrwxrwx 1 www-data www-data   15 Nov  7 09:00 a.txt*
                     lrwxrwxrwx 1 root     root        5 Nov  7 08:46 b.txt -> a.txt*
                     lrwxrwxrwx 1 root     root        5 Nov  7 08:47 c.txt -> a.txt*
                     -rwxr-xr-x 1 root     root       15 Nov  7 09:01 d.txt*
                     lrwxrwxrwx 1 root     root        5 Nov  7 08:55 e.txt -> a.txt*
                     -rwxr-xr-x 1 root     root        0 Nov  7 08:55 f.txt*
                     -rwxr-xr-x 1 root     root       15 Nov  7 09:03 h.txt*                                                       
                                                
                                                
              eg:
                    
                    -l：进行硬式连结(hard link)的连结档创建，而非复制文件本身；
                    
              eg:
                
                    sudo cp -p a.txt  h.txt
                    ubuntu@ubuntu-xenial:/home/test$ ll
                    total 20
                    drwxr-xr-x 2 root     root     4096 Nov  7 09:00 ./
                    drwxr-xr-x 4 root     root     4096 Nov  1 10:08 ../
                    -rwxrwxrwx 1 www-data www-data   15 Nov  7 09:00 a.txt*
                    lrwxrwxrwx 1 root     root        5 Nov  7 08:46 b.txt -> a.txt*
                    lrwxrwxrwx 1 root     root        5 Nov  7 08:47 c.txt -> a.txt*
                    -rwxr-xr-x 1 root     root       15 Nov  7 09:01 d.txt*
                    lrwxrwxrwx 1 root     root        5 Nov  7 08:55 e.txt -> a.txt*
                    -rwxr-xr-x 1 root     root        0 Nov  7 08:55 f.txt*
                    -rwxrwxrwx 1 www-data www-data   15 Nov  7 09:00 h.txt*
                    
              eg:
                    
                    sudo cp -r a/ aa/
                    ubuntu@ubuntu-xenial:/home/test$ ls
                    a  aa
                    ubuntu@ubuntu-xenial:/home/test$ ls aa
                    b                                                                                        
                            
                            
                eg：
                    ubuntu@ubuntu-xenial:/home/test$ sudo cp -s 1.txt  2.txt
                    ubuntu@ubuntu-xenial:/home/test$ ll
                    total 16
                    drwxr-xr-x 4 root root 4096 Nov  7 09:14 ./
                    drwxr-xr-x 4 root root 4096 Nov  1 10:08 ../
                    -rw-r--r-- 1 root root    0 Nov  7 09:14 1.txt
                    lrwxrwxrwx 1 root root    5 Nov  7 09:14 2.txt -> 1.txt
                    
                 eg:
                    
                    sudo cp -u 1.txt 3.txt
                    ubuntu@ubuntu-xenial:/home/test$ ll
                    total 24
                    drwxr-xr-x 4 root root 4096 Nov  7 09:17 ./
                    drwxr-xr-x 4 root root 4096 Nov  1 10:08 ../
                    -rw-r--r-- 1 root root    5 Nov  7 09:17 1.txt
                    lrwxrwxrwx 1 root root    5 Nov  7 09:14 2.txt -> 1.txt
                    -rw-r--r-- 1 root root    5 Nov  7 09:18 3.txt
                    drwxr-xr-x 3 root root 4096 Nov  7 09:12 a/
                    drwxr-xr-x 3 root root 4096 Nov  7 09:12 aa/     
                    
                  eg:
                    
                    sudo cp -a aaa bbb
                    ubuntu@ubuntu-xenial:/home/test$ ll
                    total 24
                    drwxr-xr-x 4 root root 4096 Nov  7 09:20 ./
                    drwxr-xr-x 4 root root 4096 Nov  1 10:08 ../
                    -rw-r--r-- 1 root root    5 Nov  7 09:17 1.txt
                    lrwxrwxrwx 1 root root    5 Nov  7 09:14 2.txt -> 1.txt
                    -rw-r--r-- 1 root root    5 Nov  7 09:18 3.txt
                    drwxr-xr-x 3 root root 4096 Nov  7 09:12 a/
                    drwxr-xr-x 3 root root 4096 Nov  7 09:12 aa/
                    lrwxrwxrwx 1 root root    2 Nov  7 09:20 aaa -> a//
                    lrwxrwxrwx 1 root root    2 Nov  7 09:20 bbb -> a//
                    

#rm
    
   * 移除文件或目录
   
   *  rm [-fir] 文件或目录
   
   * 参数
        
        -f ：就是 force 的意思，忽略不存在的文件，不会出现警告信息；
        
        -i ：互动模式，在删除前会询问使用者是否动作
        
        -r ：递归删除啊！最常用在目录的删除了！这是非常危险的选项！！！    
        
   *  例子
        
            eg:
                
                rm a.txt
                rm: remove write-protected regular empty file 'a.txt'?
                
            eg:
                
                sudo rm -i a.txt
                rm: remove regular empty file 'a.txt'? y
                
            eg:
                
                sudo rm -f b.txt
                ubuntu@ubuntu-xenial:/home/test$ sudo rm  b.txt
                rm: cannot remove 'b.txt': No such file or directory
                
            eg:
                
                sudo rm -r a/
                ubuntu@ubuntu-xenial:/home/test$ ls                
                
                
#mv
        
   *    移动文件与目录，或修改名称
   
   *    语法
            
             mv [-fiu] source destination
             
             mv [options] source1 source2 source3 .... directory      
             
   *      参数
            
            -f ：force 强制的意思，如果目标文件已经存在，不会询问而直接覆盖；
            
            -i ：若目标文件 (destination) 已经存在时，就会询问是否覆盖！
            
            -u ：若目标文件已经存在，且 source 比较新，才会升级 (update)
            
   *        例子
   
               eg:
                    
               $ sudo mv a.txt b.txt
               ubuntu@ubuntu-xenial:/home/test$ ls
               b.txt         
                
                不带参数 如果目标存在，也不会询问直接覆盖
               eg:
               
                mv -i c.txt b.txt
                mv: overwrite 'b.txt'?
                
                eg:
                sudo mv -f c.txt  b.txt
                ubuntu@ubuntu-xenial:/home/test$ ll
                total 12
                drwxr-xr-x 2 root root 4096 Nov  7 10:35 ./
                drwxr-xr-x 4 root root 4096 Nov  1 10:08 ../
                -rw-r--r-- 1 root root   15 Nov  7 10:23 b.txt
                
                eg:
                
                  sudo mv -u c.txt b.txt
                  ubuntu@ubuntu-xenial:/home/test$ ll
                  total 16
                  drwxr-xr-x 2 root root 4096 Nov  7 10:38 ./
                  drwxr-xr-x 4 root root 4096 Nov  1 10:08 ../
                  -rw-r--r-- 1 root root   15 Nov  7 10:23 a.txt
                  -rw-r--r-- 1 root root   13 Nov  7 10:38 b.txt
                
                 mv -c 是按时间顺序 不是看填充内容                        