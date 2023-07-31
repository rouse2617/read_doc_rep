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





















