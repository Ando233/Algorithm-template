# Hash

子串Hash

```c++
ll h[N];
int mod, p[N], p2[N], P;

string s;
void init_hash(){
    mod = 1e9 + 7, P = 23; p[0] = 1;
    for(int i = 0; i < s.size(); i++) p[i + 1] = 1LL * p[i] * P % mod; 
    for(int i = 0; i < s.size(); i++){
        h[i + 1] = (h[i] * P + (s[i] - 'a' + 1)) % mod;
    }
}

int get(int l, int r){
    return (h[r] - h[l - 1] * p[r - l + 1] % mod + mod) % mod;
}
```