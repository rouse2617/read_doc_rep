 



## 基础命令（汇总）

>   记录常用的Linux命令

```shell
#统计全部文件行数
#c 统计字节数  l 统计行数   w 统计字数。
-c 统计字节数。
-l 统计行数。
-m 统计字符数。这个标志不能与 -c 标志一起使用。
-w 统计字数。一个字被定义为由空白、跳格或换行字符分隔的字符串。
-L 打印最长行的长度。
-help 显示帮助信息
--version 显示版本信息
wc -l *
```

```shell
 #Linux scp 命令用于 Linux 之间复制文件和目录。
 1： 强制scp命令使用协议ssh1
-2： 强制scp命令使用协议ssh2
-4： 强制scp命令只使用IPv4寻址
#scp /home/space/music/1.mp3 root@www.runoob.com:/home/root/others/music 
```



```shell
#查看 系统版本 
cat /proc/version	

g++编译器默认的c++版本

g++ -dM -E -x c++ /dev/null | grep -F __cplusplus

C++标准	__cplusplus值
C++ 11	201103L
C++ 14	201402L
C++ 17	201703L

```







```shell
#disk usage，用来展示磁盘使用量的统计信息，默认du关注文件夹所包含的大小
#计算当前文件夹的总磁盘占用量, -s选项表示计算总和, -h选项表示以恰当的K/M/G单位展示
# -s 计算总和 
# -h 数量转换  k -> M/G
# -c 展示每个文件的大小 	默认全部遍历（包括文件夹里面的文件，隐藏文件）   
# --max-depth  设定遍历深度
# -a 打印 文件夹和文件的信息    
[root@node31 home]# ls
obs-registry-ET-UOS7.3.1.15.tar.gz  upgrade
rpm                                 upgrade-ET-GDS7.2.1.8-ET-GDS7.3.1.13.tar.gz
[root@node31 home]# du -sh
6.3G	.

```



```bash
#查看 centos版本
[root@VM-20-11-centos etc]#  cat /etc/redhat-release 
CentOS Linux release 8.5.2111
```



```shell
#列举 启动失败的服务
systemctl list-units --state failed
# 寻找 服务 
systemctl | grep [serviceName]
#查看服务信息配置
systemctl cat [serviceName]
#启动服务背后执行了那些命令？
#可以 再 /usr/lib/systemd/system 下找到相关脚本

```



```shell
#快速生成 大文件
dd if
fallocate -l 1g file.out
```





```bash
# 浏览大文件是内容时  可以用less，less 不会像 vi一样一下子全部打开，先打开一部分，速度快，方便浏览 
cat filename | less
```



```bash
#查看进程开了那些线程
ps -T -p <pid>

```

```bash
#tar 打包目录
tar -czf {打包的名字} {目录名}
```



```bash
#卸载 rpm 包
 rpm -e --nodeps {包名}
```



```shell
#看 服务的日志
	journalctl -u ceph-48bfd3ff-ff24-444b-8d0f-44f91c5a933a@osd.7.service
```





```shell
#shlle 中map 用法		


#1)遍历，根据key找到对应的value
for key in ${!myMap[*]};do
  echo $key
  echo ${myMap[$key]}
done
#2)遍历所有的key
for key in ${!myMap[@]};do
  echo $key
  echo ${myMap[$key]}
done
#3)遍历所有的value
for val in ${myMap[@]};do
  echo $val
done



[root@cdh-143 shell-test]# more map-test.sh
#!/bin/sh

echo "一、定义Map:declare -A myMap=([\"myMap00\"]=\"00\" [\"myMap01\"]=\"01\")"
declare -A myMap=(["my00"]="00" ["my01"]="01")
myMap["my02"]="02"
myMap["my03"]="03"

echo "二、输出所有的key:"
echo ${!myMap[@]}

echo "三、输出所有value:"
echo ${myMap[@]}

echo "四、输出map的长度:"
echo ${#myMap[@]}

echo "五、遍历，根据key找到对应的value:"
for key in ${!myMap[*]};do
  echo "key:"$key
  echo "value:"${myMap[$key]}
done

echo "六、遍历所有的key:"
for key in ${!myMap[@]};do
  echo "key:"$key
  echo "value:"${myMap[$key]}
done

echo "七、遍历所有value:"
for val in ${myMap[@]};do
  echo "value:"$val
done
```





```shell
#定期执行某个命令，并且这个事会原地刷新，不是那种追加式的
[root@node126 ~]# watch

Usage:
 watch [options] command

Options:
  -b, --beep             beep if command has a non-zero exit
  -c, --color            interpret ANSI color and style sequences
  -d, --differences[=<permanent>]
                         highlight changes between updates
  -e, --errexit          exit if command has a non-zero exit
  -g, --chgexit          exit when output from command changes
  -n, --interval <secs>  seconds to wait between updates
  -p, --precise          attempt run command in precise intervals
  -t, --no-title         turn off header
  -x, --exec             pass command to exec instead of "sh -c"

 -h, --help     display this help and exit
 -v, --version  output version information and exit

For more details see watch(1).
You have new mail in /var/spool/mail/root
[root@node126 ~]# 

#例子 每隔4s 执行一个命令
[root@node126 ~]# watch -n 4  "free -h"

Every 4.0s: free -h                                             Sat Mar  4 17:20:27 2023
              total        used        free	 shared  buff/cache   available
Mem:           3.7G        2.0G        251M        249M        1.4G        1.1G
Swap:            0B          0B          0B
```





```shell
#去除指定 字符
-c, --complement：反选设定字符。也就是符合 SET1 的部份不做处理，不符合的剩余部份才进行转换
-d, --delete：删除指令字符
-s, --squeeze-repeats：缩减连续重复的字符成指定的单个字符
-t, --truncate-set1：削减 SET1 指定范围，使之与 SET2 设定长度相等
--help：显示程序用法信息
--version：显示程序本身的版本信息
[root@node61 ~]# echo "ssscccc" | tr -d "s"
cccc
[root@node61 ~]# 
```







```shell
开启 coredump
#设置 core 文件大小，默认为0
ulimit -c unlimited 
#开启后可设置 core文件生成的格式
sudo sysctl -w kernel.core_pattern=core.%p.%s.%c.%d.%P.%E


			
```







## 常用 shell 脚本

### 批量解压   压缩

```shell
for i in $(ls *.tar);do tar xvf $i;done	
```

### ls显示 路径

```shell
find $PWD | xargs ls -ld  |grep  	
```









## if else

#### 	基本用法

```shell
if command1
then 
 commands
elif command2
then 
 more commands
fi

# bash shell的if语句会运行if后面的那个命令。如果该命令的退出状态码是0（该命令成功运行），位于then部分的命令就会被执行。如果该命令的退出状态码是其他值
# comand 会看做一个命令，所以如果用 到什么符号需要注意是否要使用转义字符
#---------------------------------------------
#!/bin/bash
#查看用户是否存在
testuser=root
if grep $root /etc/passwd > /dev/null
then
    echo "This is my first command"
fi
#----------------------------------------------

testuser=root
function echo_line()
{
    echo "---------------------------"
}
#---------------------------------
# if grep $root /etc/passwd > /dev/null
#     echo "dd"
# then
#     echo "This is my first command"
# fi

#---------------------------
#-eq 等于(equal)
# if [ "$a" -eq "$b" ]
# #-ne不等于(no equal)
# if [ "$a" -ne "$b" ]
# #-gt大于(greater than)
# if [ "$a" -gt "$b" ]
# #-ge大于等于
# if [ "$a" -ge "$b" ]
# #-lt小于(less than)
# if [ "$a" -lt "$b" ]
# #-le小于等于
# if [ "$a" -le "$b" ]
# #<小于(在双括号中使用)
# (("$a" < "$b"))
# #<=小于等于(在双括号中使用)
# (("$a" <= "$b"))
# #>大于(在双括号中使用)
# (("$a" > "$b"))
# #>=大于等于(在双括号中使用)
# (("$a" >= "$b"))
#--------------------------
USER=root
if [ $USER = $testuser ] 
then 
 echo "This is not $testuser" 
else 
 echo "Welcome $testuser" 
fi

#------------------------
#比较字符
val1=baseball
val2=hocket
#注意 [后加个空格
#     此时 > 会当做重定向符号 
if [ $val1 > $val1 ]
then
    echo "$val is greater thee $val2"
else
    echo "$val is less then ${val2}"
fi
#添加转移符号 
if [ $val1 \> $val1 ]
then
    echo "$val is greater thee $val2"
else
    echo "$val is less then ${val2}"
fi
echo_line

#检测字符串数量s是否0判断是否为空字符
val="asfdasf"
if [ -n ${val} ]
then
    echo "string ${val} is not empty"
else
    echo "The string ${val} is empty"
fi
echo_line

```

#### 判断文件操作

> #判断是否为文件 或者 文件夹，以及文件属性
> -d file 检查file是否存在并是一个目录
> -e file 检查file是否存在
> -f file 检查file是否存在并是一个文件
> -r file 检查file是否存在并可读
> -s file 检查file是否存在并非空
> -w file 检查file是否存在并可写
> -x file 检查file是否存在并可执行
> -O file 检查file是否存在并属当前用户所有
> -G file 检查file是否存在并且默认组与当前用户相同
> file1 -nt file2 检查file1是否比file2新
> file1 -ot file2 检查file1是否比file2旧
>
> 参数很多，但还是很好记 的目录的单词是 director 就是 -d 以此类推jump_directory=/home/shell

```shell
#这是一些 实践
if [ -d ${jump_directory} ]
then
    echo "The $jump_directory directory exists"
    ls
else
    echo "not exist"
fi 

file_name=h.sh
if [ -e $file_name ]
then
    echo "ok the $file_name is exist"
else
    echo "$file_name if not exist"
fi

if [-x $file_name ]
then
    echo " $file_name is "
else
    echo "$file_name"
fi


echo " 复合条件测试   布尔运算  || && "

file_name=h.sh

echo "判断是文件是否满足 是可执行文件而且是可读的"
if [ -x ${file_name} ] && [ -r ${file_name} ]
then
    echo "都满足"
else
    echo "不满足"
fi

```

#### case 

> 当出现大量的 if else if esle 时 可以用  case   类比于 C语言的  switch case
>
> 

---



## 循环结构 for while

#### for

```shell
for var in *list* 
do 
 *commands* 
done 
#这里的 list 可以是个数组，命令....
```

- list是多串字符时,  list 使用空格划分这些字符串，如果字符有空格需要用双引号隔开来

    ```shell
    for test in abc def hih "afas sdaf"
    do 
    	echo $test
    done
    ```

- list 也可以是 个变量 （如字符数组）

    ```shell
    strs="my name is rui"
    for test in $strs
    do
    	echo $test
    done
    ```

- 从命令总读取值

    ```shell
    #遍历ls的每个输出
    for test in $(ls) 
    do  
        echo $test
    done
    # 这里输入默认遍历方式以空格隔开为主
    # 如果想以换行为分割符号的话
    # INS 内部字段分隔符（internal field separator） 
    #是一种 set 变量，当 shell 处理"命令替换"和"参数替换"时，shell 根据 IFS 的值，默认是 space, tab, newline 来拆解读入的变量，然后对特殊字符进行处理，最后重新组合赋值给该变量。
    IFS=$'\n\n'  
    for test in $(ls -la) 
    do  
        echo $test
    done
    ```

- 自动读取文件列表

    ```shell
    # list 也可以是个路径，遍历是会自动遍历文件夹下的内容
    
    for file in /home/shell/*
    do 
        if [ -f "$file" ]
        then
            echo "$file is a file" 
        elif [ -d "$file" ]
        then
            echo "$file is directory"
        fi
        
    done
    
    ```

- 按照C语言风格写 for

    这里要注意的是 符号的直接的空格，shell 对这个要求很好

    ```shell
    #for (( i=1; i <= 10; i++ ) ) 最后面读了个空格就不行了
    for (( i=1; i <= 10; i++ ))
    do
        printf "$i "
    done
    ```

-   随机书生成   

    {0..9} 指定范围 {begin..end}

    ```
    for i in {0..9};do echo $RANDOM;done
    
    ```

    


#### while

```shell
while test command 
do 
 other commands 
done
#和C语言的差不多，就是表达形式有不同
#这里test command可以由多条组成
```

```shell
#逐行读取
cat /etc/passwd | while read LINE 
do
      echo $LINE 
done
 
```

# docker 命令

-   主机关机后，docker 容器启动方法

    找到没启动的容器，记下  其ID

```shell
bash-4.2$ docker container ls -a
CONTAINER ID        IMAGE                                                  COMMAND                  CREATED             STATUS                      PORTS                     NAMES
41cb44ca7917        6a60c3ae21e8                                           "/bin/bash -c cat ..."   7 days ago          Exited (143) 5 days ago                               debug_ceph_core
a2b88e93a4d3        hub.expontech.com/obs-ceph/obs-ceph-utils:2023022020   "/bin/bash -c cat ..."   9 days ago          Exited (255) 20 years ago  
.....


docker update --restart=always  {容器id}

```

-   删除容器 rmi

```dockerfile
docker rmi {容器名字} 
```



# 网络工具

```shell
ss 
#ss 命令用来显示处于活动状态的套接字信息。ss 命令可以用来获取 socket 统计信息，它可以显示和 netstat 类似的内容。但ss的优势在于它能够显示更多更详细的有关 TCP 和连接状态的信息，而且比 netstat 更快速更高效。

#显示所有的tcp
ss -t -a
```



# 三剑客



## grep

```shell
   grep -r "待查找内容" ./
   
   #打印出 查找内容所在行上下几行
   # -A  ahead 
   # -B  Behide
   # -C  上下都打印
   #打印匹配行的前5行
    grep -A 5 "error" catalina.out
   #打印匹配行的后5行

    grep -B 5 "error" catalina.out

    #打印匹配行的前后5行
    shell> grep -C 5 "error" catalina.out
    
    #打印出 匹配到的内容 
    grep -o 
    
    
    
```



## awk

>   逐行读入，默认有空格为分隔符，将每行切片，最后再进行各种分析处理
>
>   **gawk** *options program file*

-   $0代表整个文本行，$1代表第一个数据段



```bash
[root@node29 shell]# awk '{print $n}' boot.log 
Jul  4 15:27:22 node254 NET[897]: /etc/sysconfig/network-scripts/ifup-post : updated /etc/resolv.conf
Jul  8 09:30:51 node1 NET[866]: /etc/sysconfig/network-scripts/ifup-post : updated /etc/resolv.conf
Jul  8 12:27:43 node29 NET[814]: /etc/sysconfig/network-scripts/ifup-post : updated /etc/resolv.conf
Jul 12 15:44:38 node29 NET[846]: /etc/sysconfig/network-scripts/ifup-post : updated /etc/resolv.conf
Jul 13 13:25:33 node29 NET[849]: /etc/sysconfig/network-scripts/ifup-post : updated /etc/resolv.conf
Jul 14 10:43:07 node29 NET[842]: /etc/sysconfig/network-scripts/ifup-post : updated /etc/resolv.conf
Jul 14 12:00:22 node29 NET[843]: /etc/sysconfig/network-scripts/ifup-post : updated /etc/resolv.conf
Jul 14 21:11:11 node29 NET[846]: /etc/sysconfig/network-scripts/ifup-post : updated /etc/resolv.conf

[root@node29 shell]# awk '{print $1 "  "$2 }' boot.log 
Jul  4
Jul  8
Jul  8
Jul  12
Jul  13
Jul  14
Jul  14
Jul  14
[root@node29 shell]# 
```

-   awk 模糊匹配某一列

      需求:  用awk筛选出 包含 指定字符的行，并打印出改行的指定列
      思路：awk是一行一行读取的，读取一行时候 可以定位到哪一列，然后用内置函数 match去模糊匹配去判断是否满足要求，当然一开始也可以直接用 正则筛选，但经过一些筛选之后得出来的结果再用正则呢，这时就得用内部的match函数了

    >    **match(s, r [, a])**      
    >
    >   Return  the  position  in s where the regular expression r occurs, or 0 if r is not present, and set the values of RSTART and RLENGTH.  Note that the argument order is the same as for the ~ operator: str ~ re.  If  array  a  is  provided, a is cleared and then elements 1 through n are filled with the portions of s that match the corresponding parenthesized subexpression in r.  The 0'th element of a contains the  por‐tion of s matched by the entire regular expression r.  Subscripts a[n, "start"], and a[n, "length"] pro‐vide the starting index in the string and length respectively, of each matching substring.

```shell
#	对某一个列做正则匹配
[root@node29 shell]# echo "hrp qep" | awk ' { if(match($2,/hr./))  print "匹配成功"}'
[root@node29 shell]# echo "hrp qep" | awk ' { if(match($1,/hr./))  print "匹配成功"}'
匹配成功
[root@node29 shell]# 
```

-   awk有很多内部处理函数，遇到比较棘手的问题，可以看看有没有相应的内部函数可以处理







## sed

>   sed编辑器被称作流编辑器（stream editor）
>   (1) 一次从输入中读取一行数据。
>   (2) 根据所提供的编辑器命令匹配数据。
>   (3) 按照命令修改流中的数据。
>   (4) 将新的数据输出到STDOUT。(不会修改原来色数据)
>
>   **sed** *options script file*
>
>   <img src="C:\Users\h00165\AppData\Roaming\Typora\typora-user-images\image-20220718150023947.png" alt="image-20220718150023947" style="zoom:50%;" />	

-   替换文本

    ```shell
    # -s 
    # -s/待替换内容 /替换的内容/
    echo "This is a test\" | sed 's/test/big test/'
    ls -la | sed s'/root/特级用户/'
    #g
    ```

-   按行号去

-   尾部插入文本

    ```
    sed -i '$ a\content' filename
    ```

    

-   sed -n '1,3p' boot.log





---

常用命令（win）

```powershell
netsh wlan show profiles
netsh wlan show profiles {wifi名字} key=clear  #可以看到 wifi密码
28-CD-C4-18-D7-1F


知道端口号
netstat -ano | findstr [端口号]
C:\Users\h00165>netstat -ano | findstr 38020
  TCP    0.0.0.0:38020          0.0.0.0:0              LISTENING       28592
  TCP    [::]:38020             [::]:0                 LISTENING       28592
最后面是 pid，根据pid 任务管理器 kill 掉

```

/usr/bin/findmnt







