

我们在Java程序中访问数据库的时候，有两种提交SQL语句的方式，
一种是通过Statement直接提交SQL:
```java
statement.executeUpdate("UPDATE Users SET status = 2 WHERE userID = 333");
```

另一种是先通过PrepareStatement预编译SQL，然后设置可变参数再提交执行:
```java

```

