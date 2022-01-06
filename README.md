### Redis 5.0

### 中文注释

##### AOF
######开启
1. aof功能开启时会执行一次重写流程(创建一个temp.aof)，将redis现存的key value转化为命令写入temp.aof,,aof_state会设为AOF_WAIT_REWRITE
2. 等到重写完了后会在backgroundRewriteDoneHandler函数里面将重写期间产生的差异命令(aof_rewrite_buf_blocks)写入temp.aof,然后设置aof_state为AOF_ON
3. 后面的客户端命令就会写入aof_buf

