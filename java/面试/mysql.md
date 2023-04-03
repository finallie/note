# mysql

## buffer pool

缓存索引和数据 占内存的60%-80% 默认大小128M
缓存页+控制块
lru算法 young(热数据)+old(冷数据)+冷数据必须呆上一段时间(默认1s)才能移入表头 防治预读失效(预读 减少io次数)和bufferpool污染(全表扫描) 提高缓存命中率
free page + dirty page + clean page
free list + flush list + lru list
依照cpu核数设置实例数目 每个实例内存大于1G

## innodb与myisam区别

innodb 支持数据缓存 支持行级锁 mvcc 外键 事务 聚蔟索引

##
