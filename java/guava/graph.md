#

- Graph\<N>
- ValueGraph\<N,E>
- Network\<N,E> 可有平行边

## Graphs图算法

- hasCycle 环
- Graph\<N> transitiveClosure(Graph\<N> graph) 连接图
- Set\<N> reachableNodes(Graph\<N> graph, N node) 可达节点
- Graph\<N> transpose(Graph\<N> graph) 反转
- MutableGraph\<N> inducedSubgraph(Graph\<N> graph, Iterable<? extends N> nodes) 子图
