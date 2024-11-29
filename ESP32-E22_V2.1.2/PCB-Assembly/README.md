# Bestückungshinweise PCB V2.1.2

Bestückungsreihenfolge, Varianten und Inbetriebnahme des PCB V2.1.2  

## 1) Minimalbestückung
* Die folgenden BT sind das absolute Minimum für die grundsätzliche Funktion.
* Über die USB-mikro Buchse am ESP32 kann auch das E22-Modul versorgt werden, wenn ein passendes USB-Netzgerät verwendet wird, welches mind. 2A bereitstellen kann.

### 1.1 Key-Components
* **PCB V2.1.2**
* **U1 = ESP32-DevKitC-V4**
* **U2 = OLED 0,96"**
* **U3 = E22-400M30S** (30dBm) od. **E22-400M33S** (33dBm) od. **E22-900M30S** (30dBm!)


### 1.2 Einbau-Varianten für U3 = E22-fffM3xS
> [!NOTE]
> **Dieses BT sollte als Erstes bestückt werden, um gut an die Lötstellen zu kommen.**

**a)** Das **E22-Modul** ist für **SMD-Direktlötung** vorgesehen. Der NT ist, dass es bei einem Defekt schwieriger abzulöten ist.  
<img src="..\picass\1-1_E22-direkt.jpg" alt="E22-direkt" width="400">  

**b)** **E22-Modul auf Sockel (Variante für PCB V2.1.2)**  
Obwohl der Pin-Abstand des E22-Moduls 2,50mm beträgt, ist es trotzdem möglich, Stifte und Buchsen im RM 2,54 zu verwenden.  
Bei dieser Art der Bestückung wird sozusagen ein Stecksockel aus einfachen, günstigen und handelsüblichen Teilen hergestellt.  
In einer späteren Version wird es eine Sockeladapterplatine geben und eine modifizierte PCB.

<ins>**Schritt 1:**</ins> Durchkontaktierte Lochrasterplatte 35x27mm (13x10 Löcher) mit **2x 8pol** + **2x 3pol Pfosten-Buchsen** bestücken und mit Stiftleisten stabilisieren.  
<img src="..\picass\1-2_E22_sockelPCB.jpg" alt="E22_sockelPCB" width="300"><img src="..\picass\1-2_E22_SocBu.jpg" alt="E22_SocBu" width="300">  

<ins>**Schritt 2:**</ins> verlöten und Lötstellen plan feilen, damit das E22-Modul plan aufliegen kann und gut verlötbar ist.  
<img src="..\picass\1-2_E22_Soctop.jpg" alt="E22_Soctop" width="300"><img src="..\picass\1-2_E22_Socbot.jpg" alt="E22_Socbot" width="300">  

<ins>**Schritt 3:**</ins> **2x 8pol** + **2x 3pol Pfostenstecker gewinkelt** zur Stabilisierung in die Pfosten-Buchsen stecken und das kürzere Ende noch weiter kürzen.  
<img src="..\picass\1-2_E22_SMD90.jpg" alt="E22_SMD90" width="300"><img src="..\picass\1-2_E22_SMDa.jpg" alt="E22_SMDa" width="300">  

<ins>**Schritt 4:**</ins> auf die PCB wie ein SMD-BT auflöten.  
<img src="..\picass\1-2_E22_SMDb.jpg" alt="E22_SMDb" width="300">  

<ins>**Schritt 5:**</ins> **C3** (220..470µF, liegender Einbau) & **C4** (100nF) bestücken.


### 1.3 Einbau-Varianten für U1 = ESP32-DevKitC V4
Die **V4** ist die derzeit neueste Version. Es können aber grundsätzlich auch die **V1**- od. **V4**-Module verwendet werden.  
> [!NOTE]
> Die Unterschiede werden an anderer Stelle detailiert dargestellt. [!TODO]

* **a)** Normalerweise verwendet man eine Pfosten-Steckverbindung, wobei die Buchsenleisten in das PCB eingelötet sind und die Pfostenstecker sich am ESP32-Modul befinden, **je 2x 19-pol**:  
<img src="..\picass\ESP32_BuLeiste.jpg" alt="ESP32_BuLeiste" width="300">  

* **b)** Es können aber auch IC-Sockelstifte & Sockelbuchsen verwendet werden. Dies hat den Vorteil, dass das ESP32-Modul problemlos auf ein Steckbrett eingesteckt werden kann.  
<img src="..\picass\ESP32_IC-Sockel.jpg" alt="ESP32_IC-Sockel" width="300">  


### 1.4 OLED 0,96"
Für das OLED sind 2 Positionen 0°=Hochformat & 90°=Querformat (J11) vorgesehen, die mit **2x 4-pol Bu-Streifen** bestückt werden.  
Die OLED gibt es in grundsätzlich 2 verschiedenen Pin-Anordnungen. Die angegebene (**VCC-GND-SCL-SDA**) ist bereits auf der PCB verdrahtet. Falls man VCC <> GND umdrehen möchte, dann sind auf der Rückseiten 2 Leiterbahnen zu unterbrechen und 2 Drahtbrücken herzustellen (JP1 & JP2).  
Bei manchen OLEDs (rechts im Bild) kann man noch die **I²C**-Adresse von **`0x78`** auf **`0x7A`** ändern.  
Mit einem I²C-Scanner werden **`0x78` >> `0x3C`** und **`0x7A` >> `0x3D`** erkannt (7-Bit Format).  
Zusätzlich können auf manchen Modulen direkt die **VCC<>GND** durch die **J1/J2/J3/J4** im Foto rechts vertauscht werden.  
Das linke OLED verwendet einen **SH1106**-Driver (132x64 pixel), das rechte einen **SSD1306**-Driver (128x64 pixel).
<img src="..\picass\OLED_SH1106-SSD1306.jpg" alt="OLED_SH1106-SSD1306" width="600">  
Das OLED-Board kann über eine Abstandshülse Ø4x11 mit M2 Gewindebohrung beidseits mit M2x5 Schrauben auf dem PCB mechanisch fixiert werden.  
<img src="..\picass\U1+U2+C3+C4.jpg" alt="U1+U2+C3+C4" width="500"><img src="..\picass\1-4_OLEDfix.jpg" alt="OLEDfix" width="300">


### 1.5 User Button
Ein Taster **SW1** ist an **GPIO12** angeschlossen. Parallel dazu kann über **J10** ein Taster extern, zB. am Gehäuse, verbunden werden.  
Für **MeshCom** muss er erstmalig mit **`--button on`** aktiviert werden.  
<img src="..\picass\Button.jpg" alt="Button" width="400">


### 1.6 Testlauf #1
Beim Online-Flash Tool https://oe1kfr.com/esptool/ ist **E22** auszuwählen. (Hat auch eine Console. Chromium Browsers only!)  
Und läuft grundsätzlich, mit Minimalbestückung und auch ohne HF (E22).  
<img src="..\picass\Testlauf_1.jpg" alt="Testlauf1" width="500">


### 1.7 Varianten Antenne
* Das E22-Modul hat einen IPEX-Stecker. Hier kann eine Antenne angeschlossen werden über
  * ein **IPEX-SMA-Buchse Adapterkabel** oder
  * als Gehäusedurchführung eine dichte **U.FL IPEX <> N-Buchse** https://www.amazon.de/dp/B0C8J131PD oder
  * Alternativ eine IPEX <> SMA-Einbaubuchse: ...
 
* Beim Einbau der **SMA-Buchse J8 + R8** (0Ω=Drahtbrücke auf der Rückseite) über
  * einen SMA-St <> N-Bu mit Flansch, aber ohne Dichtung (ev. Dichtfolie verwenden):
https://www.reichelt.at/at/de/shop/produkt/hf_n_buchse_sma_flanschbuchse-141249
  * eine SMA-Bu <> SMA-Bu:  
https://www.conrad.at/de/p/bkl-electronic-0409093-0409093-sma-adapter-sma-buchse-sma-buchse-1-st-457659.html

Bei allen Varianten ist eine mechanische Entkopplung zwischen Antenne<>Gehäuse<>PCB gegeben.  


## 2) Spannungsversorgung
Für die Spannungsversorgung stehen mehrere Möglichkeiten zur Verfügung.  

### 2.1 USB-Micro via ESP32
Die Spannungsversorgung kann über die USB-Mikro-Buchse des ESP32-Moduls erfolgen, wenn ein geeignetes USB-Netzteil verwendet wird, welches bis zu 2A liefern kann. Solche Netzteile werden z.B. auch für die Versorgung von RapberryPi u.a. verwendet.  

### 2.2 Versorgung über USB-C
Das **USB-C BreakOut-Board** mit der stehenden USB-C Buchse ermöglicht ein leichtes Anstecken der externen Versorgung, speziell bei Einbau in ein Gehäuse. https://de.aliexpress.com/item/1005007821332638.html  

<ins>**Funktion:**</ins>  
Für USB-C PD (Power Delivery) ist ein Kommunikations-IC an CC1 & CC2 erforderlich.
Wenn dieser nicht vorhanden ist, dann kann nur 5V geliefert werden und über die Widerstände an CC1 & CC2 wird der Strom "eingestellt". Die Widerstände **R3** & **R4** mit jeweils **5k1** signalisieren dem USB-Netzteils, dass es **5V/3A** liefern darf. Die Schottky-Diode **D1** verhindert eine Rückspeisung, falls mehrere Spannungsquellen angeschlossen sind.  

<ins>**Schritt 1:**</ins> Die Widerstände **R3** & **R4** (je 5k1) auf der Rückseite bestücken und auf der Oberseite Lötpins auf ein Minimum kürzen.  
<img src="..\picass\2-1_R3-R4.jpg" alt="R3-R4" width="400">  

<ins>**Schritt 2:**</ins> Die Diode **D1** und eine längere **4-pol** Stiftleiste **J2** mit Gesamtlänge **15mm** auf der Oberseite bestücken.  
Dann 2-3 Lagen Doppelklebepads zur Unterstützung des USB-C Adapter Boards aufbringen ...  
<img src="..\picass\2-2_J2-D1.jpg" alt="J2-D1" width="400">  

<ins>**Schritt 3:**</ins> das USB-C Adapter Board aufkleben und verlöten. An die überstehende Stiftleiste kann eine USB-C Einbaubuchse mit Kabel angesteckt werden.  
<img src="..\picass\2-3_USB-C-Bu.jpg" alt="USB-Bu" width="400">  

Die Versorgung über die USB-C-Buchse funktioniert.  
<img src="..\picass\2-4_USB-C_ok.jpg" alt="USB-C_ok" width="400">  


### 2.3 Versorgung über DC/DC HW-613
> [!NOTE]
> Funktionsbeschreibung [!TODO]
Bei Versorgung über ein externes Netzgerät über Schraubklemmen ist zwar auch eine Schottky-Diode erforderlich, aber bei Verwendung des **DC/DC-Wandler-Boards HW-613** (bis 1,5A) kann mit bis zu 6-24V DC versorgt werden und die Ausgangsspannung kann eingestellt werden, bzw. fix durch Lötbrücken.  

**D5** 1N4007 o.ä. & **C5** 100nF bestücken  
<img src="..\picass\2-6_D5-C5.jpg" alt="D5C5" width="400">  

Eine 4-pol Stiftleiste auf den DC/DC-Wandler **U4 HW-613** löten.  
<img src="..\picass\2-5_DC-DC.jpg" alt="DCDC" width="400">  
> [!IMPORTANT]
> Auf einem Steckbrett den DC/DC-Wandler mit dem Poti auf **5,3V** Ausgangsspannung einstellen.

> [!CAUTION]
> Es ist nicht zu empfehlen, die ADJ-Leiterbahn zu unterbrechen und den 5V-Jumper zu löten, ausser man hat ein sehr gute Lupe (Mikroskop) und entsprechendes Schneidwerkzeug. Siehe https://protosupplies.com/product/mp2315-mini-adjustable-dc-dc-step-down-module/  
> <img src="..\picass\MP2315-Mini-Adjustable-DC-DC-Step-Down-Module-Jumpers.jpg" alt="DCDCjmp" width="150">  

[img U4 eingelötet] & D2 auf Oberseite & J3  

Weitere BT: C6, D4  
Weitere BT: F1, D4  
• Zusätzlich ist eine **2A** Feinsicherung **F1** und eine Schutzdiode **D5** (1N4004..1N007) gegen Verpolung eingebaut.  
• Die Transient Voltage Suppressor Diode **D4** (alternativ **D3**) schützt vor ESD mit einer VBR = 5,6V min. @ I=1mA

### 2.4 Versorgung über DC/DC R-78B5.0-2.0
Statt dem günstigen DC/DC in [2.3](https://github.com/DK9BT/esp32-e22-lora-board/blob/main/ESP32-E22_V2.1.2/PCB-Assembly/README.md#23-versorgung-%C3%BCber-dcdc-hw-613) kann auch ein handeslsüblicher, aber auch teurerer Schaltregler z.B. der **RECOM R-78B5.0-2.0** verwendet werden.  
https://at.rs-online.com/web/p/schaltregler/1392959  
https://www.conrad.at/de/p/recom-r-78k5-0-2-0-dc-dc-wandler-5-v-2-a-10-w-inhalt-1-st-2887420.html  
[img 3D]

### 2.5 Versorgung über USB-C Einbaubuchse
An die überstehende Stiftleiste **J2** kann eine USB-C Einbaubuchse mit Kabel angesteckt werden.  
[Foto !TODO]

### 2.6 Einbau in ein Gehäuse
Enclosure (transparent) https://www.reichelt.de/de/de/shop/produkt/industriegehaeuse_120_x_80_x_60_2mm_ip65_lichtgrau-340524  
Enclosure (non-transparent) https://www.reichelt.de/de/de/shop/produkt/industriegehaeuse_120_x_80_x_60_2mm_ip65_lichtgrau-340515  
Gehäuse Maßzeichnung: https://cdn-reichelt.de/documents/datenblatt/C700/6U07120806437_6U-120806_DB.pdf  

* Das Gehäuse verfügt über 8 Stk. Sacklöcher Ø3,2x4. Die in den Ecken sind für die Befestigung der PCB vorgesehen. Die Sacklöcher auf den Seiten können für die Befestigung eines 3D-Druck Einbauteils verwendet werden.
* Darin können **M2x4x3,5 Einpressmutter** eingeschmolzen werden, wenn keine Schraubklemme+DC/DC-Wandler verwendet werden.
* Bei Verwendung der Schraubklemme + DC/DC-Wandler, der auf der Rückseite der PCB platziert ist, muss ein größerer Abstand der PCB vom Gehäuseboden durch Verwendung von **M2x6x3,5 Einpressmuttern** eingehalten werden.
* Alternativ können auch Abstandsröhrchen L≥1,5mm verwendet werden (z.B. Ms-Rohr Ø3) und M2x8 Schrauben.
* !!! für den erhöhten Einbau der PCB ins Gehäuse wird es ein 3D-Druck-Teil geben!
* Bei anderem Bedarf können aber auch die Befestigungsbohrungen auf der PCB aufgebohrt werden.  
![Einpressbuchse_M2x4x3,5](https://github.com/user-attachments/assets/9b76f58b-3f03-4ac9-bbe7-2f518731cc2d)  

Für das wasserdichte Gehäuse ist eine Druckausgleichsmembran zu empfehlen, damit das Wasser auch wieder herausdiffundieren kann. Sonst steht irgendwann die Leiterplatte unter Wasser.  
z.B. https://shop.bb-sensors.com/Druck/Drucksensoren/Druckausgleich-Membran-VPE-12-Stueck.html  
oder https://www.reichelt.at/at/de/shop/produkt/druckausgleichselement_m12_schwarz_2_stueck-371154  
oder https://www.amazon.de/dp/B088QJG676

Je nach Aufstellungsort kann auch eine einfache ≈Ø2mm Bohrung zum Druckausgleich ausreichen.  

### 2.7 Programmierkabel für ESP32
Dieses könnte wegen der nur 20cm im Gehäuse verbleiben:  
https://www.reichelt.at/at/de/shop/produkt/dual_easy_usb_2_0_kabel_a_st_auf_micro_b_st_gew_0_2_m-287766  
oder es kann ein Winkeladapter verwenden werden: https://www.amazon.de/dp/B0CRVH7JRD  


## 98) weitere Hinweise
* **C2** ist bei Verwendung des **ESP32-DevKitC-V4** nicht erforderlich. Die Anschlüsse können für einen externen Reset-Taster verwendet werden.

___
# 99) Allgemeine Hinweise
* Die Schaltung ist nach den gängigen Regeln der Technik konzipiert und hergestellt. Es wurde jedoch nicht geprüft ob allfällige Normen eingehalten werden.
* Die hier angegebenen Hinweise sind lediglich eine Beschreibung einer Möglichkeit des Zusammenbaus.
* Die Inbetriebnahme erfolgt eigenverantwortlich.
* Ich weise auf die gesetzlichen Bestimmungen bez. Elektrogeräten, Funkanlagen u.ä. hin, die von jedem Anwender selber einzuhalten sind.

___
***:copyright: 23.11.2024 10:10 by OE3WAS - Wolfgang***
