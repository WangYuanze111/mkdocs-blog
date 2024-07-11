# Day 1 实验报告
- **课程名称：基础技能训练-01**
- **实验名称：Arduino模拟交通信号灯**
- **实验教室：主楼803**
- **实验日期：2024年7月8日**
- **班级：2023数字媒体技术2班**
- **学生姓名：侯理想 202311023018**
- **任课教师：田佳音**
## 实验目的
利用Arduino主板等硬件材料实现模拟交通信号灯。
## 实验内容
搭建硬件电路，在IDE中编写代码，完成调试。
## 软件环境
Windows11环境下的Arduino IDE 2.3.2
## 实验原理
控制不同引脚的高低电平变化来点亮发光二极管
## 实验代码
```cpp
void setup() {
	pinMode(11, OUTPUT);
	pinMode(12, OUTPUT);
	pinMode(13, OUTPUT);
}
void loop() {
  int RED = 12;
  int GREEN = 11;
  int YELLOW = 13;
  digitalWrite(RED,HIGH);
  digitalWrite(GREEN,LOW);
  digitalWrite(YELLOW,LOW);  
  delay(1000);
  
  digitalWrite(RED, LOW);
  digitalWrite(GREEN, HIGH);
  digitalWrite(YELLOW, LOW);                      
  delay(1000);  
  
  digitalWrite(RED, LOW);
  digitalWrite(GREEN, LOW);
  digitalWrite(YELLOW, HIGH);  
  delay(1000);      
}

```
## 实验过程
### 1.构建仿真电路图
![[Pasted image 20240708160422.png]]
### 2.搭建实体电路
![[f4dbe79434df84dfe8903bf5bb16170.jpg]]
### 3.编写程序并拷贝到主板
![[Pasted image 20240708160628.png]]
## 实验结果分析
实验基本达到了预期效果，完成了对一个交通信号灯的基础功能模拟。
## 收获感想
我们可以利用Arduino主板完成多种创意，模拟身边的基本电气设备。在条件允许的情况下，我们可以发挥想象力创造出新颖的有用的装置。
