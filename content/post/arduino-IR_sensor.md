+++
title = "用Arduino製作一個家庭室外燈"
description = "Make a home outdoor light with Arduino"
date = 2021-02-17
tags = ["Arduino","HC-SR501"]
+++

最近在電視上看到有人在賣壁掛式的紅外線感應燈，且價格蠻高的，所以我心血來潮，運用手邊有的"HC-SR501"人體紅外線感測器和Arduino nano來製作一個。   

## 材料
1. Arduino nano 
2. HC-SR501人體紅外線感測器
3. LED燈板
4. 杜邦線
5. 電池盒
6. 麵包版

## 連接腳位

|        | Arduino nano |麵包版   |
|:----:  |:------------:|:------:|
|HC-SR501|      D4      |   +/-  |
|LED燈板 |      D13     |    -    |
|電池盒  |              |   +/-   |

## 程式碼
    void setup() {
        Serial.begin(9600);
        pinMode(4, INPUT);     
        pinMode(13, OUTPUT); 

        digitalWrite(13, LOW);       
    }

    void loop(){
        int p = digitalRead(4);
        if (p == HIGH) {     
            digitalWrite(13, HIGH); 
            Serial.println("Detected");
            delay(5000);
        } 
        else {
            digitalWrite(13, LOW); 
            Serial.println("No One");
        }
    
    } 

## 補充
如果覺得感測器太靈敏的話，可透過感測器上的二個旋鈕調整
- 調節距離電位器順時針旋轉，感應距離增大（約7公尺），反之，感應距離減小（約3公尺）。
- 調節延時電位器順時針旋轉，感應延時加長（約300秒），反之，感應延時減短（約5秒）。
![HC-SR501人體紅外線感測器](/arduino-IR/HC-SR501.png)
確定正常運作後可用杜邦線將nano板上的5V、GND接到麵包板上的正負極，就可以在需要的地方運作了。

