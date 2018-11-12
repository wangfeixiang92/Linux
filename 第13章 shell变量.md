#shell 变量

定义shell变量，需要加$

           myName=wfx
           
           
           变量名和等号之间不能有空格，这可能和你熟悉的所有编程语言都不一样。
           
           同时，变量名的命名须遵循如下规则：
           
           命名只能使用英文字母，数字和下划线，首个字符不能以数字开头。
           
           中间不能有空格，可以使用下划线（_）。
           
           不能使用标点符号。
           
           不能使用bash里的关键字（可用help命令查看保留关键字）。
           
#使用变量
        
            使用变量
            使用一个定义过的变量，只要在变量名前面加美元符号即可，如：
            
            your_name="qinjx"
            echo $your_name
            echo ${your_name}
            
            变量名外面的花括号是可选的，加不加都行，加花括号是为了帮助解释器识别变量的边界，比如下面这种情况：
            
            for skill in Ada Coffe Action Java; do
                echo "I am good at ${skill}Script"
            done
            如果不给skill变量加花括号，写成echo "I am good at $skillScript"，解释器就会把$skillScript当成一个变量（其值为空），代码执行结果就不是我们期望的样子了。
            
            推荐给所有变量加上花括号，这是个好的编程习惯。
                
                eg：
                
                for name in lilei wfx smj wh; do
                    echo "myname is ${name}"
                done;       
                
                 ./a.sh
                myName is lilei
                myName is wfx
                myName is smj
                myName is wh   
                
                
                推荐给所有变量加上花括号，这是个好的编程习惯。
                
                已定义的变量，可以被重新定义，如：
                
                your_name="tom"
                echo $your_name
                your_name="alibaba"
                echo $your_name
                这样写是合法的，但注意，第二次赋值的时候不能写$your_name="alibaba"，使用变量的时候才加美元符（$）。
                
                
#只读变量
            
            
            使用readonly命令可以将变量定义为只读变量，只读变量的值不能被改变
            
            #!/bin/bash
            myurl="wwww.baidu.com"
            readonly myurl
            echo ${myurl}
            
            运行脚本，结果如下：
            
            /bin/sh: NAME: This variable is read only.
            
#删除变量
            
            使用 unset 命令可以删除变量。语法：
            
            unset myName
            
            变量被删除后不能再次使用。unset 命令不能删除只读变量。
            
            eg:
                
                ./a.sh
                ./a.sh: line 5: unset: myName: cannot unset: readonly variable
                wfx
                ./a.sh: line 8: myName: readonly variable
                wfx
                
             eg:
                
#变量类型
            
            运行shell时，会同时存在三种变量
            
   * 局部变量
            
            
             局部变量在脚本或命令中定义，仅在当前shell实例中生效，其他shell启动的程序不能访问局部变量
             
   * 环境变量
             
             所有的程序，包括shell启动的程序，都能访问环境变量，有些程序需要环境变量来保证其能正常运行。必要的时候shell脚本也可以定义环境变量
             
   *  shell变量
            
              shell变量是由shell程序设置的特殊变量。shell变量中有一部分是环境变量，有一部分是局部变量，这些变量保证了shell的正常运行。
              
              
#shell 字符串
        
        字符串是shell编程中最常用最有用的数据类型（除了数字和字符串，也没啥其它类型好用了），字符串可以用单引号，也可以用双引号，也可以不用引号。单双引号的区别跟PHP类似。
        
#单引号
        str='this is a string'
        单引号字符串的限制：
        
        单引号里的任何字符都会原样输出，单引号字符串中的变量是无效的；
        单引号字串中不能出现单独一个的单引号（对单引号使用转义符后也不行），但可成对出现，作为字符串拼接使用。

#双引号
        your_name='runoob'
        str="Hello, I know you are \"$your_name\"! \n"
        echo $str
        Hello, I know you are "runoob"! 
        输出结果为：
        
        双引号的优点：
        
        双引号里可以有变量
        双引号里可以出现转义字符  
        
#获取字符串长度
        
        string="abcd"
        echo ${#string}                                              
            
                                                                     