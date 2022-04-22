#

## 输入输出

```c++
//cout与printf不再公用缓存区  cout不再线程安全
ios::sync_with_stdio(0);
//cin操作前cout不再flush
cin.tie(0);
```

## 复杂度

|input size |required time complexity
|---|---
|n ≤ 10| O(n!)
|n ≤ 20 |O(2^n^)
|n ≤ 500 |O(n^3^)
|n ≤ 5000 |O(n^2^)
|n ≤ 10^6^ |O(nlogn) or O(n)
|n is large |O(1) or O(logn)

## 线段树

```c++
int sum(int a, int b) {
    a += n; b += n;
    int s = 0;
    while (a <= b) {
        if (a%2 == 1) s += tree[a++];
        if (b%2 == 0) s += tree[b--];
        a /= 2; b /= 2;
    }
    return s;
}

void add(int k, int x) {
    k += n;
    tree[k] += x;
    for (k /= 2; k >= 1; k /= 2) {
        tree[k] = tree[2*k]+tree[2*k+1];
    }
}
```

## Range updates

difference array

## bit manipulation

- __builtin_clz(x): the number of zeros at the beginning of the number
- __builtin_ctz(x): the number of zeros at the end of the number
- __builtin_popcount(x): the number of ones in the number
- __builtin_parity(x): the parity (even or odd) of the number of ones

```c++
//遍历x的子集
int b = 0;
do {
// process subset b
} while (b=(b-x)&x);
```

## 最短路径

- Bellman–Ford 边的权重可以为负数 检测负环 O(VE)

```c++
for (int i = 1; i <= n; i++) distance[i] = INF;
distance[x] = 0;
for (int i = 1; i <= n-1; i++) {
    for (auto e : edges) {
        int a, b, w;
        tie(a, b, w) = e;
        distance[b] = min(distance[b], distance[a]+w);
    }
}
```

- Shortest Path Faster Algorithm  Bellman–Ford升级版 只遍历更新的点 用quene实现

- Dijkstra’s algorithm 不能有负边 O(V+ ElogE)

- Floyd–Warshall O(n^3^) 所有最短路径

```c++
for (int k = 1; k <= n; k++) {
    //加强Floyd–Warshall 求最小环 edge[i][i]需设置为INF而不是0
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= n; j++) {
            mn = min(mn, distance[i][j]+edge[i][k]+edge[k][j])
        }
    }

    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= n; j++) {
            distance[i][j] = min(distance[i][j],
            distance[i][k]+distance[k][j]);
        }
    }
}
```

## Tree

- traversal

```c++
void dfs(int s, int e) {
    // process node s
    for (auto u : adj[s]) {
        if (u != e) dfs(u, s);
    }
}
```

- Diameter

## Spanning trees

- Kruskal’s algorithm（并查集）
- Prim’s algorithm
