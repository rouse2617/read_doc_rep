-   [x] std::pair 

-   返回多个参数

unique_lock   lock_guard

std::piecewise_construct_t

**scoped_ptr**

std::piecewise_construct 

std::map:equal_range  stl

std::optional

函数后面加 

std::in_place_type_t

std::is_nothrow_constructible_v 

函数后面 override = 0

std::forward()

 const override  用途 

std::function

std::move ？ 为什么效率好，原理， 弊端？ 使用创建？   

std::make_unique

boost::intrusive::list

std::tie

**柔性数组**

futex  什么做是？



---


# 有时间汇总

debuginfo 

gdb 原理

cache miss

![image-20230423174730014](C:/Users/h00165/AppData/Roaming/Typora/typora-user-images/image-20230423174730014.png)

### 代码编译流程--> 四个步骤 ，实现原理？elf？

### 编译连接怎么弄？？ 怎么用动态库？？ 

**kill -10**

 **memchr**

**prctl**


**flock**

**fcntl**

**ceph中的 自旋锁实现**

**socketpair**

**setsid**

**statfs**

 **fstatfs**

**readlink**

**O_CLOEXEC** 

**pipe2(pipefd, O_CLOEXEC);**

**noexcept**

**sockaddr_un**

**std::piecewise_construct,**

**ceph 加锁？？**

**std::function**

**typeid 打印出函数名字？**

**__thread 代表含义 （C++ 11后才支持）**

**__tls_get_addr??? TLS是啥**

>    **程序编译的流程？？？**
>
>    **LTO ??**
>
>    **软连接和硬链接**

**atomic**

**fsync()**

**posix_fadvise（）** 

 **std::mem_fn**

**什么 是管程？**

 **构造函数 =default**

**using 用法**

**make_unique**

---



## 网络

三层 四层 七层网络



TCP_NODELAY 合并小的TCP包为一个大的TCP包，避免过多的小的TCP的报文的TCP头部浪费网络带宽



互斥锁原理 

std::make_unique



fio 4M 和 fio 5M 为什么相差那么大





xatrr  和  omap 和  map_hander



网卡 irq 绑定？  中断 ？ 网卡收发包原理？  cpu 缓存？

eBPF 概念 了解

DPDK、SPDK、RDMA、NUMA

nvmeof

各种磁盘  IO 性能 ，一个IO 多长时间（SSD ，HDD ）？ （多种IO模型 对应 那些类型的）如何缓解？ 多读少写，少写多读对应的场景，加了ssdcache 有什么问题？ 

bond网卡？？？各种模式 ？

一些 类的实现 

![image-20230329110806447](http://img.rui.vin/202303291108543.png)

CHAP认证 ？ 加强吧版本的三次握手？









ceph osd perf

![image-20230531235202076](img.rui.vin/image-20230531235202076.png)













![image-20220909175628016](http://img.rui.vin/202209091756060.png

<img src="http://img.rui.vin/202209091742630.png"/>	











pthread_rwlock_init





![image-20220909174229533](http://img.rui.vin/202209091742630.png)	





无锁编程 __sync_fetch_and_add [多线程无锁编程--原子计数操作：__sync_fetch_and_add等12个操作](https://www.cnblogs.com/lyggqm/p/6208218.html)





# [带外(out of band)数据](https://www.cnblogs.com/lvdongjie/p/12915137.html)



1.     余江那边   有个 OEM的项目   yinw






















## boost 库

​	 asio 

​	 boost::intrusive

​	 

  



```
自旋锁？？？？

inline void spin_lock(std::atomic_flag& lock)

{

 while(lock.test_and_set(std::memory_order_acquire))

 ;

}
```













put 流程



测试

继续看 excu





















