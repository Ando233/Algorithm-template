# BSGS

```c++
#include <bits/stdc++.h>
using namespace std;

typedef pair<int, int> PII;
typedef long long ll;

int bsgs(int a, int b, int p){
    if(1 % p == b % p) return 0;
    int k = sqrt(p) + 1;
    unordered_map<int, int> hash;
    for(int i = 0, j = b % p; i < k; i++){
        hash[j] = i;
        j = (ll)j * a % p;
    }
    int ak = 1;
    for(int i = 0; i < k; i++) ak = (ll)ak * a % p;
    for(int i = 1, j = ak; i <= k; i++){
        if(hash.count(j)) return (ll)i * k - hash[j];
        j = (ll)j * ak % p;
    }
    return -1;
}

int main(){
	int a, b, p;
    cin >> a >> b >> p;
    int res = bsgs(a, b, p);
    if(res == -1) cout << "no solution";
    else cout << res;
	return 0;
}
```

