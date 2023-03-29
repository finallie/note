# mybatis

```text
SqlSessionFactory （mybatis全局配置  mapper映射配置）
SqlSession (执行器类型 自动提交) (非线程安全)
Executor (缓存)
StatementHandler
ParameterHandler
ResultSetHandler
TypeHandler

日志 代理模式(connection statement resultset等对象的代理) 适配器模式(适配底层日志框架)
事务 jdbc managed

mapper动态代理
缓存 装饰器模式 12级代理 数据一致性问题

spring整合
SqlSessionFactoryBean
SqlSessionTemplate 线程安全 无法执行事务相关操作 一个查询一个session 一个事务一个session
动态代理

批处理操作 BatchExecutor
```
