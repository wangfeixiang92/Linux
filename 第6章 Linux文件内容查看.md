#Linux文件内容查看
    
   *    cat 由第一行开始显示文件内容
   *    tac 由最后一行开始显示，可以看作是cat的道写。
   *    nl 显示的时候，顺道输出行号。
   *    more 一页一页的显示内容
   *    less 与more类似，但是比more好的是，他可以往前翻页
   *    head 只看头几行
   *    tail只看尾几行
   
   
#cat        由第一行显示文件内容
   
   * 语法
        
        cat [-AbEnTv]
   
   * 选项与参数：
        
        -A ：相当於 -vET 的整合选项，可列出一些特殊字符而不是空白而已；
        -b ：列出行号，仅针对非空白行做行号显示，空白行不标行号！
        -E ：将结尾的断行字节 $ 显示出来；
        -n ：列印出行号，连同空白行也会有行号，与 -b 的选项不同；
        -T ：将 [tab] 按键以 ^I 显示出来；
        -v ：列出一些看不出来的特殊字符
        
        
   * 例子
        
         eg:
                     
            cat -A /vagrant_data/nginx.conf.default
            $
            #user  nobody;$
            worker_processes  1;$
            $
            #error_log  logs/error.log;$
            #error_log  logs/error.log  notice;$
            #error_log  logs/error.log  info;$
            $
            #pid        logs/nginx.pid;$
            $
            $
            
            
          eg:
          
             cat -b /vagrant_data/nginx.conf.default
            
                 1  #user  nobody;
                 2  worker_processes  1;
            
                 3  #error_log  logs/error.log;
                 4  #error_log  logs/error.log  notice;
                 5  #error_log  logs/error.log  info;
            
                 6  #pid        logs/nginx.pid;
            
            
                 7  events {
                 8      worker_connections  1024;
                 9  }
            
             eg:
             
             cat -E /vagrant_data/nginx.conf.default
             $
             #user  nobody;$
             worker_processes  1;$
             $
             #error_log  logs/error.log;$
             #error_log  logs/error.log  notice;$
             #error_log  logs/error.log  info;$
             $
             #pid        logs/nginx.pid;$
             $
             $
             events {$
                 worker_connections  1024;$
             }$
             $
             
             eg:
                
                 cat -n /vagrant_data/nginx.conf.default
                     1
                     2  #user  nobody;
                     3  worker_processes  1;
                     4
                     5  #error_log  logs/error.log;
                     6  #error_log  logs/error.log  notice;
                     7  #error_log  logs/error.log  info;
                     8
                     9  #pid        logs/nginx.pid;
                    10
                    11
                    12  events {
                    13      worker_connections  1024;
                    14  }
                    15
                    
             eg:
                    
                     cat -T /vagrant_data/nginx.conf.default
                    
                    #user  nobody;
                    worker_processes  1;
                    
                    #error_log  logs/error.log;
                    #error_log  logs/error.log  notice;
                    #error_log  logs/error.log  info;
                    
                    #pid        logs/nginx.pid;
                    
                    
                    events {
                        worker_connections  1024;
                    }
              
              eg:
                    
                     cat -v /vagrant_data/nginx.conf.default
                    
                    #user  nobody;
                    worker_processes  1;
                    
                    #error_log  logs/error.log;
                    #error_log  logs/error.log  notice;
                    #error_log  logs/error.log  info;
                    
                    #pid        logs/nginx.pid;
                    
                    
                    events {
                        worker_connections  1024;
                    }
                
                
                eg;
                    
                     cat -nb /vagrant_data/nginx.conf.default
                    
                         1  #user  nobody;
                         2  worker_processes  1;
                    
                         3  #error_log  logs/error.log;
                         4  #error_log  logs/error.log  notice;
                         5  #error_log  logs/error.log  info;
                    
                         6  #pid        logs/nginx.pid;
                         
# tac      文件内容从最后一行开始显示
                    
    
   *    例子
        
            eg:
                
                tac /vagrant_data/nginx.conf.default
                 fastcgi_pass unix:/tmp/php-cgi.sock;
                
                }
                
                    #}
                    #    }
                    #        index  index.html index.htm;
                    #        root   html;
                    #    location / {
                
                    #    ssl_prefer_server_ciphers  on;
                    #    ssl_ciphers  HIGH:!aNULL:!MD5;
                    
    
    
#nl        显示行号
     
   *
        选项和参数
            
              -b ：指定行号指定的方式，主要有两种：
              -b a ：表示不论是否为空行，也同样列出行号(类似 cat -n)；
              -b t ：如果有空行，空的那一行不要列出行号(默认值)；
              -n ：列出行号表示的方法，主要有三种：
              -n ln ：行号在荧幕的最左方显示；
              -n rn ：行号在自己栏位的最右方显示，且不加 0 ；
              -n rz ：行号在自己栏位的最右方显示，且加 0 ；       
          
   
   *    例子  
   
           eg:  
            
             nl -bt /vagrant_data/nginx.conf.default
            
                 1  #user  nobody;
                 2  worker_processes  1;
            
                 3  #error_log  logs/error.log;
                 4  #error_log  logs/error.log  notice;
                 5  #error_log  logs/error.log  info;
            
                 6  #pid        logs/nginx.pid;
            
            
                 7  events {
                 8      worker_connections  1024;
                 9  }
            
           eg:
           
                $ nl -bt /vagrant_data/nginx.conf.default
           
                1  #user  nobody;
                2  worker_processes  1;
           
                3  #error_log  logs/error.log;
                4  #error_log  logs/error.log  notice;
                5  #error_log  logs/error.log  info;
           
                6  #pid        logs/nginx.pid;
           
           
                7  events {
                8      worker_connections  1024;
                9  }
            
            eg:
            
                 nl -n ln /vagrant_data/nginx.conf.default
                
                1       #user  nobody;
                2       worker_processes  1;
                
                3       #error_log  logs/error.log;
                4       #error_log  logs/error.log  notice;
                5       #error_log  logs/error.log  info;
                
                6       #pid        logs/nginx.pid;
                
                
                7       events {
                8           worker_connections  1024;
                9       }
            
            eg:
            
                nl -n rn /vagrant_data/nginx.conf.default
                
                     1  #user  nobody;
                     2  worker_processes  1;
                
                     3  #error_log  logs/error.log;
                     4  #error_log  logs/error.log  notice;
                     5  #error_log  logs/error.log  info;
                
                     6  #pid        logs/nginx.pid;
                
                
                     7  events {
                     8      worker_connections  1024;
                     9  }
                     
             
             eg:
                     nl -n rz /vagrant_data/nginx.conf.default
                    
                    000001  #user  nobody;
                    000002  worker_processes  1;
                    
                    000003  #error_log  logs/error.log;
                    000004  #error_log  logs/error.log  notice;
                    000005  #error_log  logs/error.log  info;
                    
                    000006  #pid        logs/nginx.pid;
                    
                    
                    000007  events {
                    000008      worker_connections  1024;
                    000009  }


#more      一页一页翻动   

   -    space  一页页翻动
   -    Enter   一行行翻动
    /关键字      代表再这个显示内容中，向下搜寻关键字
    :f           显示现在的文档名以及目前显示的行数
    q            离开离开more 不再显示该文件内容
    b或者ctrl+b  向上翻页 代表往回翻页，不过这动作只对文件有用，对管线无用。
    
    
#less       一页一页的翻动
    
   -    空白格     向下翻1页
   -    PageDown   向下翻1页
   -    PageUp     向上翻1页
   /关键字          向下搜索
   ?关键字          向上搜索 
   n               重复上一个搜索
   N               反向的重复上一个搜索
   q               离开less程序
   Home            返回顶部
   END             返回底部
   
   
#head           取出文件的前几行
    
    -n ：后面接数字，代表显示几行的意思
    
   
#tail       取出文件的后几行
    
    -n    后面接数字 表示几行的意思
    -f     表示持续侦测后面所接的档名，要等到按下[ctrl]-c才会结束tail的侦测
    
    
     
    
                  
        
            
            
                                                                                                        
        
        