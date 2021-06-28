
Redis不同于Memcached将value视为黑盒，Redis的value本身具有结构化的特点，对于value提供了丰富的操作。
基于内存存储的特点使得Redis与传统的关系型数据库相比，拥有极高的吞吐量和相应性能。


## 1 数据结构

Redis没有传统关系型数据库的table模型。scheme所对应的db仅以编号区分，同一个db内，可以作为顶层模型，其值是扁平化，即db本身就是可以值的命名空间。
实际使用中，通常以“：”号作为分隔符，将命名空间值和业务key连接，作为Redis中当前db下的key值，如“article：12345”作为key值，表示article这个命名空间下的元素的key，类似于关系型数据库中的article表主键为123456的行。


### 1.1 value对象的通用结构

```
typedef struct redisObject {
    
}
```


### 1.2 String

redis的string和其它很多编程语言中的语义类似，它能表达三种值的类型：
- 字符串
- 整数
- 浮点数

三种类型间根据具体场景由redis完成相互间自动转型，并且根据需要选取底层的承载方式。


### 1.3 List


### 1.4 Map

Map 型的value在Redis中又叫Hash,顾名思义，它的最初实现是一个哈希表。

Redis本身就是key-value结构，它的value可以是map类型，此类型的value内部又是一个subkey-subvalue。
但，map内部的key和value不能再嵌套map了，它只能是String型所能表达的内容：整形、浮点型、字符串。


1 基本操作


2 内存数据结构


3 hashtable实现



### 1.6 Sorted-Set

Sorted-Set 是Redis特有的数据类型，类似Map




## 2 客户端与服务器的交互



## 3 单机处理逻辑





### 3.1 多路复用




## 4 持久化