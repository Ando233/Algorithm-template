# 最小表示法

```c++
int get_min_pos(){
    int k = 0, i = 0, j = 1;
    while(k < n && i < n && j < n){
        if(a[(i + k) % n] == a[(j + k) % n]) k++;
        else{
            if(a[(i + k) % n] > a[(j + k) % n]) i += k + 1;
            else j += k + 1;
            if(i == j) j++;
            k = 0;
        }
    }
    return min(i, j);
}
```

# Lyndon分解

```c++
// duval_algorithm
vector<string> duval(string const& s) {
  int n = s.size(), i = 0;
  vector<string> factorization;
  while (i < n) {
    int j = i + 1, k = i;
    while (j < n && s[k] <= s[j]) {
      if (s[k] < s[j])
        k = i;
      else
        k++;
      j++;
    }
    while (i <= k) {
      factorization.push_back(s.substr(i, j - k));
      i += j - k;
    }
  }
  return factorization;
}
```

