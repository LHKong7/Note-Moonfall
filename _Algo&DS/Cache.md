为了提高数据的访问性能，我们选择将数据放置在内存中

存放数据的内存我们称为缓存



一个是存放 put （key，value）

一个是 get 根据key拿取value



FIFO （First In First Out）： 淘汰最先放入缓存的数据

LRU （Least Recently Used）淘汰最久未使用的数据

LFU（Least Frequently Used）淘汰最不频繁使用的数据





