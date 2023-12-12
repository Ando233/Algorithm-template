# Trie树

```c++
#include <bits/stdc++.h>
using namespace std;

const int N = 1e5 + 5;
int son[N][26], cnt[N], tot;
void insert(char s[]){
	int p = 0;
	for(int i = 0; s[i]; i++){
		int u = s[i] - 'a';
		if(!son[p][u]) son[p][u] = ++tot;
		p = son[p][u];
	}
	cnt[p]++;
}

int query(char s[]){
	int p = 0;
	for(int i = 0; s[i]; i++){
		int u = s[i] - 'a';
		if(!son[p][u]) return 0;
		p = son[p][u];
	}
	return cnt[p];
}

char s[N];
int main(){
	int n;
	cin >> n;
	while(n--){
		int op;
		cin >> op >> s;
		if(op == 0) insert(s);
		else cout << query(s) << '\n';
	}
	return 0;
} 
```

