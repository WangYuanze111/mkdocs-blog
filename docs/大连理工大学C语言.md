# 大连理工大学C语言作业
## Week 9
### 1.e的近似
编写函数，求e=1+1/1!+1/2!+1/3!+……+1/n!的值。

Input sample
```
10
```
Output sample
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
### 2.统计数字字符
编写函数，求给定字符串中数字字符的个数，在主函数中输入字符串及输出统计的个数。

Input sample
```
abc123fg
```
Output sample
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

### 3.大于平均数的个数
编写函数，求一组整数中大于平均值的个数，数组元素个数任意。例如：给定的一组数为1,3,6,9,4,23,35,67,12,88时，函数值为3

Input sample
```
1 3 6 9 4 23 35 67 12 88
```
Output sample
```
3
```
``` cpp linenums="1"
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
### 4.3*3二维数组排序
编写函数用冒泡排序法将二维数组a[3][3]中的9个整数分别按照所属各行进行由大到小的排序。

``` c linenums="1"
#include<stdio.h>
void Sort(int (*a)[3]){
	int i;
	for(i = 0;i<3;i++){
		int j;
		for(j = 1;j<=2;j++){
			int k;
			for(k = 0;k<2;k++){
				if(a[i][k]>a[i][k+1]){
					int t = a[i][k];
					a[i][k]	= a[i][k+1];
					a[i][k+1] = t;	
	 			}	
			}
		}
	}
}
int main(){
	int a[3][3];
	for(int i = 0;i<3;i++){
		for(int j = 0;j<3;j++)
			scanf("%d",&a[i][j]);
	}
	Sort(a);
	for(int i = 0;i<3;i++){
		for(int j = 0;j<3;j++)
			printf("%d",a[i][j]);
		printf("\n");
	}
	return 0;
}
```
### 5.x的n次方
编写递归函数求x的n次方, 并调用此函数求2的5次方

``` c linenums="1"
#include<stdio.h>
int Pow(int x , int n){
	if(n==0) return 1;
	return x*Pow(x,n-1);
}
int main(){
	int a = Pow(2,5);
	printf("%d",a);
	return 0;
}
```
### 6.字符串插入
用指针编写函数 insert(s1,s2,f)，其功能是在字符串s1中的指定位置f处插入字符串s2

``` cpp linenums="1"
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
## Week 10
### 1.x的n次方
编写求x的n次方的递归函数，在主函数调用并输出。(x为double型，n为整型，函数类型为double型）

Input Sample
```
4 3
```
Output Sample
```
64.000000
```

``` c linenums="1"
#include<stdio.h>

double Pow(double x , int n){
	if(n==0) return 1;
	return x*Pow(x , n-1);
}
int main(){
	double a ;
	int b;
	scanf("%lf%d" , &a,&b);
	printf("%lf" , Pow(a , b));
	return 0;
}
```
### 2.输出最大最小数
编写函数，通过键盘输入10个整数，找出其中最大的数和最小的数，在主调函数中输入数据和结果。

Input Sample
```
2 3 4 1 7 6 8 9 26 35
```
Output Sample
```
max=35,min=1
```

``` c linenums="1"
#include<stdio.h>
int Max(int p[]){
	int ans = p[0];
	for(int i = 1;i<10;i++)
		if(ans<p[i]) ans = p[i];
	return ans;
}
int Min(int p[]){
	int ans = p[0];
	for(int i = 1;i<10;i++)
		if(ans>p[i]) ans = p[i];
	return ans;
}
int main(){
	int a[10];
	for(int i = 0;i<10;i++){
		scanf("%d" , &a[i]);
	}
	printf("max=%d,min=%d" , Max(a) , Min(a));
	return 0;
}
```
### 3.任意整数转换为千分位分隔的字符形式。
编写函数，对于任意输入的一个整数，转换为千分位分隔的字符形式，在主函数中调用并输出。

Input Sample
```
123456
```
Output Sample
```
123,456
```
``` c linenums="1"
#include<stdio.h>
void f(int n){
	char s[50];
	int len = 0;
	int cnt = 0;
	while(n){
		int t = n%10;
		if(len && (len-cnt)%3==0){
			s[len] = ',';
			len++;
			cnt++;
		}
		s[len] = t+'0';
		len++;
		n/=10;
	}
	for(int i = len-1;i>=0;i--)
		putchar(s[i]);
}
int main(){
	int x;
	scanf("%d",&x);
	f(x);
	return 0;
}
```
### 4.找数
编写函数，输入N个整数，将它们存入数组a中，再输入一个整数x，然后在数组中
查找x，如果找到，输出相应的下标，否则，输出"Not Found"。要求在主函数中输入10个整数及查找结果。

Input Sample 1
```
1 2 3 4 5 6 7 8 9 10
5
```
Output Sample 1
```
5
```
Input Sample 2
```
1 2 3 4 5 6 7 8 9 10
11
```
Output Sample 2
```
Not Found
```
``` c linenums="1"
#include<stdio.h>
void Find(int num[] , int x){
	for(int i = 0;i<10;i++){
		if(num[i] == x){
			printf("%d",i+1);
			return ;
		}
	}
	printf("Not Found");
	return ;
}
int main(){
	int a[10];
	for(int i = 0;i<10;i++){
		scanf("%d" , &a[i]);
	}
	int n;
	scanf("%d" , &n);
	Find(a,n);
	return 0;
}
```




