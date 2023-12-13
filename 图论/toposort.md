# toposort

```c++
bool toposort(){
    queue<int> q;
    int cnt = 0;
    for (int i = 1; i <= n; i ++ ){
        if (!d[i]) q.push(i);
    }

    while (!q.empty()){
        int t = q.front();
        q.pop();
        cnt++;
        cout << t << ' ';

        for (int i = h[t]; i; i = e[i].nxt){
            int v = e[i].to;
            if (--d[v] == 0){
                q.push(v);
            }
        }
    }
    return cnt == n;
}
```

