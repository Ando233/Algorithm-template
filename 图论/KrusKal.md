# KrusKal

```c++
#include <bits/stdc++.h>
using namespace std;

const int N = 5005, M = 2e5 + 5, INF = 0x3f3f3f3f;
struct Edge{
	int u, v, w;
	bool operator< (const Edge& W)const{
		return w < W.w;
	}
}e[M];
int n, m;
int f[N];
int find(int x){
	return x == f[x] ? x : f[x] = find(f[x]);
}
int main(){
	scanf("%d%d", &n, &m);
	for(int i = 0; i < m; i++){
		int u, v, w;
		scanf("%d%d%d", &u, &v, &w); 
		e[i] = {u, v, w};
	}
	sort(e, e + m);
	for(int i = 1; i <= n; i++) f[i] = i;
	int ans = 0, cnt = 0;;
	for(int i = 0; i < m; i++){
		int fau = find(e[i].u), fav = find(e[i].v);
		if(fau != fav){
			f[fau] = fav;
			ans += e[i].w;
			cnt++;
		}
	}
	
	if(cnt < n - 1) printf("orz");
	else cout << ans;
	return 0;
}
```

