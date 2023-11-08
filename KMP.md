# KMP

```c++
#include <bits/stdc++.h>
using namespace std;

const int N = 1e6 + 5;
char s[N], t[N];
int nxt[N];
int main(){
	cin >> s + 1 >> t + 1;
	
	int n = strlen(s + 1), m = strlen(t + 1);
	nxt[1] = 0;
	for(int i = 2, j = 0; i <= m; i++){
		while(j && t[i] != t[j + 1]) j = nxt[j];
		if(t[i] == t[j + 1]) j++;
		nxt[i] = j;
	}
	
	for(int i = 1, j = 0; i <= n; i++){
		while(j && s[i] != t[j + 1]) j = nxt[j];
		if(s[i] == t[j + 1]) j++;
		if(j == m){
			cout << i - m + 1 << '\n';
			j = nxt[j];
		}
	}
	
	for(int i = 1; i <= m; i++){
		cout << nxt[i] << " ";
	}
	return 0;
}
```

