

```sql
select * from order where status = 1 order by create_time asc;
```
需要给`status`和`create_time`建立组合索引。
如果只给`status`单独建立索引，会发生文件排序，也就是SQL执行计划中，Extra列会出现`Using filesort`。



建一个商品表：
```sql
CREATE TABLE `product` (
    `id` int(11) NOT NULL,
    `product_no` varchar(20) DEFAULT NULL,
    `name` varchar(255) DEFAULT NULL,
    `price` decimal(10, 2) DEFAULT NULL,
    PRIMARY KEY (`id`) USING BTREE
) CHARACTER SET = UTF8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;

```


B+Tree相比于B树和二叉树来说，最大的优势在于查询效率。

B树非叶子节点也要存数据，所以单个节点的数据量更小，在相同的磁盘I/O次数下，就能查询到更多的节点。



`explain` 执行计划中需要重点关注Type字段。
- ALL
- index
- range(索引范围扫描)
- ref（非唯一索引扫描）
- eq_ref (唯一索引扫描)
- const（结果只有一条的主键或唯一索引扫描）




- 通过非主键索引（辅助索引）查询数据

会先通过辅助索引查询到主键索引的值，再通过主键索引查询对应的叶子节点，然后获取整行数据。这个过程叫回表。


## 常用优化索引的方法

- 前缀优化索引

如只对商品名的前五个字符建立索引，可以减小索引字段的大小，让一个索引页中可以存放更多索引值，有效提高查询速度。

但`order by`无法使用前缀索引，无法把前缀索引用作覆盖索引。


- 覆盖索引优化

是指


- 联合索引