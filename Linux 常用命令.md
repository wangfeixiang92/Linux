#shutdown

* NAME 介绍
       
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
