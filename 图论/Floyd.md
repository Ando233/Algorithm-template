# Floyd

```c++
#include <bits/stdc++.h>
using namespace std;

const int N = 505;
typedef long long ll;
ll d[N][N];
int n, m;

void floyd(){
	for(int k = 1; k <= n; k++){
		for(int i = 1; i <= n; i++){
			for(int j = 1; j <= n; j++){
				d[i][j] = min(d[i][j], d[i][k] + d[k][j]);
				d[j][i] = d[i][j];
			}
		}
	}
}
 
int main(){
	scanf("%d%d", &n, &m);
	memset(d, 0x3f, sizeof(d));
	for(int i = 1; i <= n; i++){
		d[i][i] = 0;
	}
	
	for(int i = 0; i < m; i++){
		ll u, v, w;
		scanf("%lld%lld%lld", &u, &v, &w);
		d[u][v] = min(d[u][v], w);
		d[v][u] = min(d[v][u], w);
	}
	
	floyd();
	
	for(int i = 1; i <= n; i++){
		for(int j = 1; j <= n; j++){
			printf("%lld ", d[i][j]);
		}
		printf("\n");
	}
	return 0;
}
```

