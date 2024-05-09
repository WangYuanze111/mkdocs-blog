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
```
3
```
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

### 3.编写函数，求一组整数中大于平均值的个数，数组元素个数任意。例如：给定的一组数为1,3,6,9,4,23,35,67,12,88时，函数值为3
Input sample
```
1 3 6 9 4 23 35 67 12 88
```
Output sample
```
3
```
``` cpp linenums=1
#include<stdio.h>

int  aver(int a[],int n){
	int sum = 0;
	int i;
	int ans = 0;
	for(i = 0;i<n;i++) sum += a[i];
	float Aver = 1.0*sum/n;
	for(i = 0;i<n;i++)
		if(a[i] > Aver) ans ++;
	return ans;
}
int main(){
	int a[100];
	int i = 0;
	int num;
	while(scanf("%d",&num)!=EOF){
		a[i] = num;
		i++;
	}
	int ans = aver(a,i);
	printf("%d",ans);
	return 0;
}
```
### 4.用指针编写函数 insert(s1,s2,f)，其功能是在字符串s1中的指定位置f处插入字符串s2

``` cpp linenums=1
#include<stdio.h>

void insert(char s1[] , char s2[],int f){
	char temp[100];
	int i;
	for(i = 0;s1[i];i++){
		temp[i] = s1[i];
	}
	for(i = 0;i<f;i++){
		s1[i] = temp[i];
	}
	for(i = 0;s2[i];i++){
		s1[f+i] = s2[i];
	}
	for(i = f+i;temp[f];i++){
		s1[i] = temp[f];
		f++;
	}
	s1[i] = '\0';
}
int main(){
	char s1[100] , s2[100];
	int n;
	scanf("%s%s%d",s1,s2,&n);
	insert(s1,s2,n);
	printf("%s",s1);
	return 0;
}
```



