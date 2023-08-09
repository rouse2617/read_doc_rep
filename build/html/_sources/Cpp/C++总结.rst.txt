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


.. code-block:: python
   :name: this-py

   print 'Explicit is better than implicit.'