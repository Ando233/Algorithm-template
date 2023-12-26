# 最大流EK

复杂度O(nm^2)，但实际上通常可以处理点&边1e3-1e4的数据

```c++
#include <bits/stdc++.h>
using namespace std;

typedef long long ll;
const int N = 2e3 + 5, M = 2e5 + 10, INF = 0x3f3f3f3f;
int h[N], pre[N], tot = 1;
ll d[N];
bool vis[N];
struct Edge{
    int to, nxt;
    ll w;
}e[M];

int n, m, S, T;
void add(int u, int v, ll w){
    e[++tot].to = v, e[tot].nxt = h[u], e[tot].w = w;
    h[u] = tot;
}

bool bfs(){
    memset(vis, false, sizeof vis);
    queue<int> q;
    q.push(S), vis[S] = true, d[S] = INF;
    while(!q.empty()){
        int t = q.front();
        q.pop();
        for(int i = h[t]; i; i = e[i].nxt){
            int v = e[i].to;
            if(!vis[v] && e[i].w){
                vis[v] = true;
                d[v] = min(d[t], e[i].w);
                pre[v] = i;
                if(v == T) return true;
                q.push(v);
            }
        }
    }
    return false;
}

ll EK(){
    ll r = 0;
    while(bfs()){
        r += d[T];
        for(int i = T; i != S; i = e[pre[i] ^ 1].to){
            e[pre[i]].w -= d[T];
            e[pre[i] ^ 1].w += d[T];
        }
    }
    return r;
}

int main(){
    scanf("%d%d%d%d", &n, &m, &S, &T);
    while(m--){
        int u, v; ll w;
        scanf("%d%d%lld", &u, &v, &w);
        add(u, v, w); add(v, u, 0);
    }
    
    printf("%lld", EK());
    return 0;
}
```

