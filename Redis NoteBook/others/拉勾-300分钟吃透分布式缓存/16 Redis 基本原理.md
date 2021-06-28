## Redis 简介

Redis （Remote Server），远程字典服务。一个Redis实例可以有多个存储数据的字典，客户端可以通过select来选择字典即DB进行数据存储。



## Redis 特性

Memcached 只支持二进制字节块这一种数据类型。

线上Redis一般会同时使用两种持久化方式，通过开启appendonly及关联配置项将命令及时追加到AOF文件，同时在每天流量最低峰的时候，通过bgsave保存当时所有内存数据快照。

通过读写分离，把所有读操作落到Redis的master，所有读操作落到Redis的多个slave中，从而大幅提升Redis的读写能力。

Redis还支持事务，在multi指令后，指定多个操作，然后通过exec指令一次性执行，中途如果出现异常，则不执行所有命令操作，否则，按顺序一次性执行所有操作，执行过程中不会执行任何其它命令。

Redis 还支持Cluster特性，可以通过手动或自动的方式。将所有key按哈希分散到不同的节点，在容量不足时还可以通过Redis的迁移指令，把其中一部分key迁移到其它节点。



Redis的所有内存数据结构都存在全局的dict字典中，dict类似Memcached的hashtable。
Redis的dict也有 2 个哈希表，插入新的key时，一般用 0 号哈希表，随着key的插入和删除，
当0号哈希表的keys数大于哈希表桶数，
或keys数小于哈希桶的1/10时，
就对hash表进行扩缩。dict中，哈希表解决冲突的方式，与Memcached相同，也是通过桶内单链表，来指向多个hash相同的key/value数据。



## Redis 高性能

Redis一般被
Redis基于Epoll事件模型开发，可以进行非阻塞网络IO，
同时由于单线程命令处理，整个处理过程不存在竞争，不需要加锁，没有上下文切换开销，
所有数据操作都是在内存中操作，
所以Redis的性能很高，单个实例即可达到10W级QPS。核心线程除了负责网络IO及命令处理，还负责写数据到缓存，已方便将最新写操作同步到AOF、slave。

处理了子进程



## Redis 持久化




Redis

此时可以通过bgrewriteaof指令，对AOF进行重写，只保留数据的最后内容，来大大缩减AOF的内容。




## Redis 集群管理

Redis的集群管理有三种方式。
