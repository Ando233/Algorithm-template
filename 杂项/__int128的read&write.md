# __int128的read&write

```c++
inline void read(__int128 &x){
	bool f = 0;
	char ch;
	if ((ch = getchar()) == EOF) exit(0);
	while(ch < '0' || ch > '9'){
		f |= ch == '-', ch = getchar();
	}
	x = 0;
	while(ch >= '0' && ch <= '9'){
		x = (x << 3) + (x << 1) + ch - '0', ch = getchar();
	}
	if(f) x = -x;
}

void write(__int128 &x){
	int a[50],w = 0, i;
	bool f = 0;
	if(x < 0) f = 1, x = -x;
	while(x){
		a[++w] = x % 10;
		x /= 10;
	}
	if(f) putchar('-');
	for(i = w; i >= 1; i--) putchar(a[i] + '0');
	if(w == 0) putchar('0');
	putchar('\n');
}
```

