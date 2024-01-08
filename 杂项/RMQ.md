# RMQ

```c++
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
typedef pair<int, int> PII;
const int inf = 0x3f3f3f3f;
const int N = 2e5 + 10;

int a[N], f[N][35];
int n, m;
void init(){
    for(int i = 1; i <= n; i++) f[i][0] = a[i];
    for(int j = 1; (1 << j) <= n; j++){
        for(int i = 1; i + (1 << j - 1) <= n; i++){
            f[i][j] = max(f[i][j - 1], f[i + (1 << j - 1)][j - 1]);
        }
    }
}

int query(int l, int r){
    int k = log2(r - l + 1);
    return max(f[l][k], f[r - (1 << k) + 1][k]);
}

int main() {
    ios::sync_with_stdio(false); 
    cin.tie(0); cout.tie(0);
    cin >> n >> m;
    for(int i = 1; i <= n; i++) cin >> a[i];
    init();
    while(m--){
        int l, r;
        cin >> l >> r;
        cout << query(l, r) << '\n';
    }
    return 0;
}
```

