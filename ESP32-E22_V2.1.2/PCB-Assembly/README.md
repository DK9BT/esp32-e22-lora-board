# Bestückungshinweise PCB V2.1.2

spezielle Details und Varianten bez. der Bestückung des PCB V2.1.2  

## 1) Minimalbestückung
* Die folgenden BT sind das absolute Minimum für die grundsätzliche Funktion.
* Über die USB-mikro Buchse am ESP32 wird auch das E22-Modul versorgt. Voraussetzung ist eine passenden USB-Netzgerät, welches mind. 2A bereitstellen kann.

### 1.1 Key-Components
* **PCB V2.1.2**
* **U1 = ESP32-DevKitC-V4**
* **U2 = OLED 0,96"**
* **U3 = EE22-400M30S** (30dBm) od. **E22-400M33S** (33dBm)


### 1.2 Einbau-Varianten für U1 = ESP32-DevKitC V4
* **a)** Normalerweise verwendet man eine Pfosten-Steckverbindung, wobei die Buchsenleisten in das PCB eingelötet sind und die Pfostenstecker sich am ESP32-Modul befinden:  
<img src="..\picass\ESP32_BuLeiste.jpg" alt="ESP32_BuLeiste" width="300">  

* **b)** Es können aber auch IC-Sockelstifte & Sockelbuchsen verwendet werden. Dies hat den Vorteil, dass das ESP32-Modul problemlos auf ein Steckbrett eingesteckt werden kann.  
<img src="..\picass\ESP32_IC-Sockel.jpg" alt="ESP32_IC-Sockel" width="300">  

### 1.3 Einbau-Varianten für E22
* **a)** Das E22-Modul ist für SMD-Direktlötung vorgesehen. Der NT ist, dass es bei einem Defekt schwieriger abzulöten ist.
* **b)** Obwohl der Pin-Abstand des E22-Moduls 2,50mm beträgt, ist es trotzdem möglich IC-Sockelstifte & IC-Sockel im Raster 2,54 zu verwenden.  
...  
[img]   

### 1.4 OLED 0,96"
Für das OLED sind 2 Positionen 0°=Hochformat & 90°=Querformat (J11) vorgesehen, die mit 4-pol Bu-Streifen bestückt werden.  

### 1.5 Kleinteile
* **Buchsenleisten** für U1: **2x 19-pol** & U2: **2x 4-pol** & **C3** (220..470µF, liegender Einbau) & **C4** (100nF)  
<img src="..\picass\U1+U2+C3+C4.jpg" alt="U1+U2+C3+C4" width="500">

### 1.6 Varianten Antenne
* über **IPEX-SMA-Buchse Adapterkabel** oder **SMA-Buchse J8 + R8** (0Ω=Drahtbrücke auf der Rückseite) oder andere Varianten siehe [README](../README.md)  
[img]  

___
***15.11.2024 by OE3WAS***
