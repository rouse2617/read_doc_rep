C/C++语法方面
==============================


ftruncate
~~~~~
.. highlight:: sh
::
   
   int ftruncate(int fd, off_t  length)
   改函数可以用于扩展文件大小，但并没有向磁盘写数据，是用 0来填充

   int fd = open("test.txt", O_CREAT | O_WRONLY | O_TRUNC, 0666);
   ftruncate(fd, 1000)    //扩容1000个字节


memchr
~~~~~
.. highlight:: sh
::

   在字符串中找第一个匹配的字符，并且返回该字符所在对的地址
   str -- 指向要执行搜索的内存块。
   c   -- 以 int 形式传递的值，但是函数在每次字节搜索时是使用该值的无符号字符形式。
   n   -- 要被分析的字节数
   void *memchr(const void *str, int c, size_t n)

.. highlight:: c
::
   
   const char str[] = "qwertasdfg";
   const char ch = 't';
   char *p;
   p = (char*)memchr(str, ch, strlen(str));
   printf("%s",p);

   