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
Die OLED gibt es in grundsätzlich 2 verschiedenen Pin-Anordnungen. Die angegebene (**VCC-GND-SCL-SDA**) ist bereits auf der PCB verdrahtet. Falls man VCC <> GND umdrehen möchte, dann sind auf der Rückseiten 2 Leiterbahnen zu unterbrechen und 2 Drahtbrücken herzustellen (JP1 & JP2).  
Bei manchen OLEDs (rechts im Bild) kann man noch die **I²C**-Adresse von **0x78** auf **0x7A** ändern und zusätzlich auch noch auf dem OLED selber die **VCC<>GND** durch die **J1/J2/J3/J4** im Foto vertauschen.  
Das linke OLED verwendet einen **SH1106**-Driver (132x64 pixel), das rechte einen **SSD1306**-Driver (128x64 pixel).
<img src="..\picass\OLED_SH1106-SSD1306.jpg" alt="OLED_SH1106-SSD1306" width="600">

### 1.5 Kleinteile
* **Buchsenleisten** für U1: **2x 19-pol** & U2: **2x 4-pol** & **C3** (220..470µF, liegender Einbau) & **C4** (100nF)  
<img src="..\picass\U1+U2+C3+C4.jpg" alt="U1+U2+C3+C4" width="500">

### 1.6 User Button
Ein Taster **SW1** ist an **GPIO12** angeschlossen. Parallel dazu kann über **J10** ein Taster extern, zB. am Gehäuse, verbunden werden.  
<img src="..\picass\Button.jpg" alt="Button" width="400">

### 1.7 Varianten Antenne
* Das E22-Modul hat einen IPEX-Stecker. Hier kann eine Antenne angeschlossen werden über
  * ein **IPEX-SMA-Buchse Adapterkabel** oder
  * als Gehäusedurchführung eine dichte **U.FL IPEX <> N-Buchse** https://www.amazon.de/dp/B0C8J131PD oder
  * Alternativ eine IPEX <> SMA-Einbaubuchse: ...
 
* Beim Einbau der **SMA-Buchse J8 + R8** (0Ω=Drahtbrücke auf der Rückseite) über
  * einen SMA-St <> N-Bu mit Flansch, aber ohne Dichtung (ev. Dichtfolie verwenden): https://www.reichelt.at/at/de/shop/produkt/hf_n_buchse_sma_flanschbuchse-141249
  * eine SMA-Bu <> SMA-Bu:  
https://www.conrad.at/de/p/bkl-electronic-0409093-0409093-sma-adapter-sma-buchse-sma-buchse-1-st-457659.html

Bei allen Varianten ist eine mechanische Entkopplung zwischen Antenne<>Gehäuse<>PCB gegeben.  
[img]  


### 1.x Testlauf #1
Beim Online-Flash Tool https://oe1kfr.com/esptool/ ist **E22** auszuwählen. (Hat auch eine Console. Chromium Browsers only!)  
Und läuft grundsätzlich, mit Minimalbestückung und noch ohne HF (E22).  
<img src="..\picass\Testlauf_1.jpg" alt="Testlauf1" width="500">

Für weitere Details siehe auch [README](../README.md)  
___
***15.11.2024 by OE3WAS***
