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
|n ≤ 106 |O(nlogn) or O(n)
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
