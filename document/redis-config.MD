# Redis AppendOnly 方式配置存档





>1.save:
     在save的过程中，Redis的链接会关闭，因此会有一段时间程序无法链接Redis
     以下来源于官方文档:
      #
      # Save the DB on disk:
      #
      #   save <seconds> <changes>
      #
      #   Will save the DB if both the given number of seconds and the given
      #   number of write operations against the DB occurred.
      #
      #   In the example below the behaviour will be to save:
      #   after 900 sec (15 min) if at least 1 key changed
      #   after 300 sec (5 min) if at least 10 keys changed
      #   after 60 sec if at least 10000 keys changed
      #
      #   Note: you can disable saving completely by commenting out all "save" lines.
      #
      #   It is also possible to remove all the previously configured save
      #   points by adding a save directive with a single empty string argument
      #   like in the following example:
      #
      #   save ""
      #   save 900 1
      #   save 300 10
      #   save 60 10000
      #   save 10 1

 **port <端口号>**
 
 tcp-backlog 511
 timeout 0
 tcp-keepalive 0
 loglevel notice
 

 logfile ""
 
 
 databases 16
 

 
 **save ""**
 
 stop-writes-on-bgsave-error yes
 
 rdbcompression yes
 
 rdbchecksum yes
 
 dbfilename dump.rdb
 
 dir ./
 
 slave-serve-stale-data yes
 
 slave-read-only yes
 

 repl-diskless-sync no
 
 repl-diskless-sync-delay 5
 
 repl-disable-tcp-nodelay no
 
 slave-priority 100
 
 **requirepass <密码>**
 
 **maxheap 1.5GB**
 
 heapdir /
 
 **maxmemory 1GB**
 
 **appendonly yes**
 
 **appendfilename "appendonly.aof"**
 
 **appendfsync everysec**
 
 no-appendfsync-on-rewrite no
 
 auto-aof-rewrite-percentage 100
 
 auto-aof-rewrite-min-size 64mb
 
 aof-load-truncated yes
 
 lua-time-limit 5000
 
 slowlog-log-slower-than 10000
 
 slowlog-max-len 128
 
 latency-monitor-threshold 0
 
 notify-keyspace-events ""
 
 hash-max-ziplist-entries 512
 hash-max-ziplist-value 64
 
 list-max-ziplist-entries 512
 list-max-ziplist-value 64
 
 set-max-intset-entries 512
 
 zset-max-ziplist-entries 128
 zset-max-ziplist-value 64
 
 hll-sparse-max-bytes 3000
 
 activerehashing yes
 
 client-output-buffer-limit normal 0 0 0
 client-output-buffer-limit slave 256mb 64mb 60
 client-output-buffer-limit pubsub 32mb 8mb 60
 
 hz 10
 
 **aof-rewrite-incremental-fsync yes**
 

