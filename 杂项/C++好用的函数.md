# C++好用的函数

## upper/lower_bound

upper_bound（第一个大于/小于x）, lower_bound（第一个大于等于/小于等于x）

以lower_bound举例：

```
//	a为vector
int idx = lower_bound(a.begin(), a.end(), x) - a.begin();
//	a为数组
int idx = lower_bound(a, a + n, x) - a;
//	第一个小于等于x的
int idx = lower_bound(a.begin(), a.end(), x, greater<int>()) 
```

## bitset

```
bitset<N> s;
count() 返回有多少个1
any() 判断是否至少有一个1
none() 判断是否全为0
set() 所有位置成1
set(k, v) 第k位置成v
reset() 所有位置成0
flip() 取反
flip(k) 第k位
```

