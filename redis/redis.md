##redis 基础
### 参考资料
* [菜鸟教程](http://www.runoob.com/redis/redis-tutorial.html)
* [Redis 命令参考](http://doc.redisfans.com/)
* [15天玩转redis](http://www.cnblogs.com/huangxincheng/p/4966258.html)
### 关键字
* REmote DIctionary Server(Redis)
* key-value存储系统
* ANSI C语言编写、遵守BSD协议

###特点
* 数据持久化，内存中的数据--> 磁盘中
* string、list、hash、set、zset五种数据类型、HyperLogLog结构
* master-slave模式的数据备份

###基本命令
> 远程登录
> 
* redis-cli -h host -p port -a password
* PING  --> PONG

> 键命令
> 
* DEL 	 key
* EXISTS key
* MOVE key db
* RENAME key newkey
* RENAMENX key newkey : 仅当newkey不存在时重命名
* TYPE key
* 
* EXPIRE 	key second
* EXPIREAT 	key timestamp
* PEXPIRE 	key millisecond
* PEXPIREAT key millisecond-timestamp
* PERSIST key
* TTL key
* PTTL key
* 
* KEYS *
* KEYS pattern
* RANDOMKEY
* [SCAN](http://doc.redisfans.com/key/scan.html)
* 
* DUMP key: 序列化 内存 -> 硬盘
* RESTORE key: 反序列化
* 

> 字符串命令
> 
* SET key value
* SETNX key value
* SETEX key seconds value
* GETSET key value
* SETRANGE key offset value
* SETBIT key offset value
* 
* MSET key1 value1 key2 value2...
* MSETNX ...
* PSETEX key milliseconds value
* 
* GET key
* MGET key1 key2...
* GETRANGE key start end
* GETBIT key offset
*
* STRLEN key
* APPEND key value
* INCR key
* INCRBY key increment
* INCRBYFLOAT key increment
* DECR key
* DECRBY key decrement
*

> 哈希命令   
> field不能重复
>
* HLEN key
* HKEYS key
* HVALS key : 所有值
* HDEL key field1 field2...
* HEXISTS key field
* 
* HSET key field valye
* HMSET key f1 v1 f2 v2
* HSETNX key field value
* 
* HGET key field
* HMGET key f1 f2
* HGETALL key : key中的所有字段和值
*  
* HINCRBY key field increment
* HINCRBYFLOAT key field increment
* HSCAN key cursor [MATCH pattern] [COUNT count] 
*

> 列表命令
> 
* LLEN key 
* LINDEX key index
* LRANGE key start end
* 
* LPUSH key v1 v2 / RPUSH
* LPOP key / RPOP
* LPUSHX key value / RPUSHX
* RPOPLPUSH source destination
* 
* LSET key index value ： Index 小于0从右边开始, 比如-1
* LINSERT key BEFORE|AFTER pivot value
* LREM key count value : count可以小于0
* LTRIM key start end ： 只能从左到右操作
* 
* [BLPOP](http://doc.redisfans.com/list/blpop.html) 
* BRPOP
* BRPOPLPUSH

> 集合命令
>    
* SCARD key
* SMEMBERS key
* SISMEMBER key member
* SRANDMEMBER key count
* 
* SADD key m1 m2...
* SREM key m1 m2...
* SMOVE source destination member
* SPOP key 随机
* 
* SDIFF key1 key2 :返回其他key2中没有的key1的元素 
* SDIFFSTORE destination key1 key2 ： 减去其他集合的元素
* SINTER key1 key2 : 相交
* SINTERSTORE ...
* SUNION key1 key2
* SUNIONSTORE ... 
* 
* SSCAN key cursor [MATCH pattern] [COUNT count] : glob 风格
* 

> 有序集合命令   
> 按 score从小到大排序， 从0开始
> 
* ZCARD key
* ZCOUNT key minscore maxscore
* ZLEXCOUNT key - + : [m1 [m2
* 
* ZADD key score1 mem1...
* 
* ZINCRBY key increment member
* ZINTERSTORE destination keysnum key1 key2:分数相加
* ZUNIONSTORE destination keysnum key1 key2 :相同分数相加
* 
* ZRANGE key start stop[WITHSCORES]
* ZRANGEBYLEX key [c (g  : 字段必须用[
* ZRANGEBYSCORE key (1 5  :  1 < score <= 5  : 分数不能用[
* ZRANK key mem
* ZSCORE key mem
* ZREVRANGE key start stop
* ZREVRANGEBYSCORE key min max
* ZREVRANK key mem
* 
* ZREM key m1 m2
* ZREMRANGEBYLEX key min max
* ZREMRANGEBYRANK key start end
* ZREMRANGEBYSCORE key min max
* 
* ZSCAN key cursor [MATCH pattern] [COUNT count] 
*

> HyperLogLog  
> [redis数据结构HyperLogLog](https://www.cnblogs.com/ysuzhaixuefei/p/4052110.html)  
> [Hyperloglog基数统计](http://www.jianshu.com/p/0cf5f8bc1079)  
> 
* PFADD key element1 element2 ...
* PFCOUNT key1 key2 ...
* PFMERGE destkey key1 key2 ...




