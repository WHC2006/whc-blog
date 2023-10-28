不会写DP，记忆化搜索凑活一下就得了

```cpp
#include <iostream>
#include <algorithm>
#include <cstring>
using namespace std;
//记忆化搜索
int b[1002][1002];//主数组
int a[1002][1002];//记忆化数组
int n,ans;

int max(int x, int y) {//自写max
	if (x > y) {
		return x;
	}
	else {
		return y;
	}
}
int solve(int z, int j) {
	if (a[z][j] > -1)
		return a[z][j];
	if (z == n ) {
		a[z][j] = b[z][j];
		
	}
	else{
		a[z][j] = max(solve(z + 1, j), solve(z + 1, j + 1)) + b[z][j];
	}
	return a[z][j];
}

int main()
{
	memset(a, -1, sizeof(a));
	cin >> n;
	for (int i = 1; i <= n ; i++)
		for(int j=1;j<=i;j++)
		cin >> b[i][j];
	cout<<solve(1, 1);

	return 0;
}

//whc
```
