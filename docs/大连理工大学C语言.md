# 大连理工大学C语言作业
## 第九周
### 1.编写函数，求e=1+1/1!+1/2!+1/3!+……+1/n!的值。
input sample
```
10
```
output sample
```
e=2.7183
```

``` c linenums="1"
#include<stdio.h>

float f(int x) {
	int t = 1;
	float ans = 1;
	int i;
	for (i = 1; i <= x; i++) {
		t *= i;
		ans += 1.0 / t;
	}
	return ans;
}

int main() {
	float e;
	int n;
	scanf_s("%d", &n);
	e = f(n);
	printf("e=%.4f", e);
	return 0;
}
```
### 2.编写函数，求给定字符串中数字字符的个数，在主函数中输入字符串及输出统计的个数。
input sample
```
abc123fg
```
output sample
3
``` c linenums="1"
#include<stdio.h>

int f(char s[]) {
	int cnt = 0;
	int i = 0;
	for (i = 0;; i++) {
		if (s[i] == '\0') break;
		if (s[i] > '0' && s[i] < '9') cnt++;
	}
	return cnt;
}

int main() {
	char s[1000];
	scanf("%s", s);
	int ans = f(s);
	printf("%d", ans);
	return 0;
}
```