- **课程名称：基础技能训练-01**
- **实验名称：Arduino驱动蜂鸣器和数字显示屏**
- **实验教室：主楼803**
- **实验日期：2024年7月10日**
- **班级：2023数字媒体技术2班**
- **学生姓名：侯理想 202311023018**
- **任课教师：田佳音**
## 实验目的
利用Arduino主板实现对蜂鸣器和数字显示屏的驱动。实现蜂鸣器发出不同音调的声音、数字显示屏显示不同字符。
实现Processing和Arduino的串口交互。
## 实验内容
搭建硬件电路，在IDE中编写代码，完成调试。
## 软件环境
Windows11环境下的Arduino IDE 2.3.2
## 实验原理
蜂鸣器振动发出声音。
通过电位器调整电阻控制显示器亮度。
## 实验代码
### 蜂鸣器Demo
```cpp
const int buzzerPin = 10; // 蜂鸣器连接到引脚10

void setup() {
  pinMode(buzzerPin, OUTPUT); // 设置引脚为输出模式
}
void loop() {
  tone(buzzerPin, 1000); // 发出1000Hz的声音
  delay(500); // 持续500毫秒
  noTone(buzzerPin); // 停止发声
  delay(500); // 等待500毫秒
}

```
### 显示器Demo
```cpp
#include <LiquidCrystal.h>

  

// initialize the library by associating any needed LCD interface pin

// with the arduino pin number it is connected to

const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;

LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
void setup() {

  // set up the LCD's number of columns and rows:

  lcd.begin(16, 2);

  // Print a message to the LCD.

  lcd.print("hello, world!");

}

void loop() {

  // set the cursor to column 0, line 1

  // (note: line 1 is the second row, since counting begins with 0):

  lcd.setCursor(0, 1);

  // print the number of seconds since reset:

  lcd.print(millis() / 1000);

}
```
### Processing 和Arduino的交互设计
Processing代码示例
```cpp
import processing.serial.*;
Serial port;
void setup(){
 port = new Serial(this,"COM3",9600);
 size(300,300);
}
void draw(){
 rect(100,100,50,50);
}
void mouseClicked(){
 if((mouseX>=100) & (mouseX<=150) & (mouseY>=100) & (mouseY<=150)){
 println("LED turn ON");
 port.write("a");
 }
 else{
 println("LED turn OFF");
 port.write("b");
 }
}
```
Arduino代码示例
```cpp
int c=0;
void setup() {
 Serial.begin(9600);
 pinMode(LED_BUILTIN,OUTPUT);
}
void loop() {
 if(Serial.available()){
 c=Serial.read();
 if(c==97)
 digitalWrite(LED_BUILTIN,HIGH);
 else if(c==98)
 digitalWrite(LED_BUILTIN,LOW);
 }
}
```
### 实验过程
### 1.构建仿真电路图
![[25c3793f8b1d644ac3cfc2e13277269.png]]
![[b7202fb10420ac5369353cec480000c.png]]
### 2.搭建实体电路
![[1f511575653e1ab596e49dceaa5b98e.jpg]]
### 3.编写程序并拷贝到主板
## 实验结果分析
实验基本达到了预期效果。可以利用蜂鸣器演奏《小星星》《星球大战》等乐曲；可以点亮发光显示屏并通过电位器调整亮度；可以完成Processing和Arduino的串口通信，实现人机交互。
## 收获感想
我们可以利用Arduino主板完成多种创意，模拟身边的基本电气设备。在条件允许的情况下，我们可以发挥想象力创造出新颖的有用的装置。