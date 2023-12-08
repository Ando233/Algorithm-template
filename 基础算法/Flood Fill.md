```c++
#include <bits/stdc++.h>
using namespace std;

#define x first
#define y second

typedef pair<int, int> PII;

const int N = 1005, M = N * N;

int n, m;
char g[N][N];
PII q[M];
bool vis[N][N];

void bfs(int x, int y){
	int hh = 0, tt = 0;
	q[0] = {x, y};
	vis[x][y] = true;
	while(hh <= tt){
		PII t = q[hh++];
		for(int i = t.x - 1; i <= t.x + 1; i++){
			for(int j = t.y - 1; j <= t.y + 1; j++){
				if(i == t.x && j == t.y) continue;
				if(i < 0 || i >= n || j < 0 || j >= m) continue;
				if(g[i][j] == '.' || vis[i][j]) continue;
				q[++tt] = {i, j};
				vis[i][j] = true;
			}
		} 
	}
}

int main(){
	scanf("%d%d", &n, &m);
	for(int i = 0; i < n; i++){
		scanf("%s", g[i]);
	}
	
	int cnt = 0;
	for(int i = 0; i < n; i++){
		for(int j = 0; j < m; i++){
			if(g[i][j] == 'W' && !vis[i][j]){
				bfs(i, j);
				cnt++;
			}
		}
	}
	cout << cnt << '\n';
	return 0;
}
```

