- **课程名称：基础技能训练-01**
- **实验名称：Arduino控制DHT温湿度传感器和超声波测距仪器**
- **实验教室：主楼803**
- **实验日期：2024年7月9日**
- **班级：2023数字媒体技术2班**
- **学生姓名：侯理想 202311023018**
- **任课教师：田佳音**
## 实验目的
利用Arduino主板、DHT温湿度传感器和超声波测距仪等硬件完成相关操作并输出数据。
实现数据和用户的交互
## 实验内容
搭建硬件电路，在IDE中编写代码，完成调试
## 软件环境
Windows11环境下的Arduino IDE 2.3.2
## 实验原理
利用不同传感器获取环境数据
## 实验代码
```cpp linenums = '1'
#include "DHT.h"
#define DHTPIN 2     // 定义连接DHT传感器的引脚
#define DHTTYPE DHT11   // DHT11 或 DHT22

DHT dht(DHTPIN, DHTTYPE);
const int trigPin = 11; // Trig引脚

const int echoPin = 12; // Echo引脚

const int LED = 13;

long duration;

int distance;

  
  

void setup() {

  Serial.begin(9600); // 初始化串口通信

  pinMode(trigPin, OUTPUT); // 设置Trig引脚为输出

  pinMode(echoPin, INPUT);  // 设置Echo引脚为输入

  pinMode(LED , OUTPUT);

  dht.begin();

}

  

void loop() {

  float humidity = dht.readHumidity();

  float temperatureC = dht.readTemperature();

  float temperatureF = dht.readTemperature(true);

  

  // if (isnan(humidity) || isnan(temperatureC) || isnan(temperatureF)) {

  //   Serial.println("读取DHT传感器失败");

  //   return;

  // }

  
  
  

  // 触发超声波脉冲

  digitalWrite(trigPin, LOW);

  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);

  delayMicroseconds(10);

  digitalWrite(trigPin, LOW);

  

  // 读取Echo引脚的脉冲宽度

  duration = pulseIn(echoPin, HIGH);

  

  // 计算距离（单位：厘米）

  distance = duration * 0.034 / 2;

  

  // 输出距离到串口监视器

  Serial.print("距离: ");

  Serial.print(distance);

  Serial.println(" cm");

  if(distance < 20){

    digitalWrite(LED ,HIGH);

  }

  else digitalWrite(LED ,LOW);

  Serial.print("湿度: ");

  Serial.print(humidity);

  Serial.print("%  温度: ");

  Serial.print(temperatureC);

  Serial.print("°C ");

  Serial.print(temperatureF);

  Serial.println("°F");

  Serial.println();

  delay(100); // 延迟1秒

}
```
## 实验过程
### 1.构建仿真电路图
![[9a21ae04067326010894ef8b743bda4.png]]
### 2.搭建实体电路
![[997811146bb072a68b3a0ac98dee308.jpg]]
### 3.编写程序并拷贝到主板
![[Pasted image 20240709163058.png]]
## 实验结果分析
![[1463c580f29268957e68ac5c1e96b68.png]]
实验基本达到了预期效果。可以通过超声波测距仪测量距离，可以通过温湿度传感器获取周围环境的温度和湿度并进行输出；可以根据所得距离的远近控制一个发光二极管的点亮。
## 收获感想
我们可以利用Arduino主板完成多种创意，模拟身边的基本电气设备。在条件允许的情况下，我们可以发挥想象力创造出新颖的有用的装置。