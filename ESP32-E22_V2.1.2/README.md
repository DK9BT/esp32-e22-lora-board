# ESP32-E22-LoRa-board V2.1.1 - beta
Carrier Board for Lora Tranceiver like E22-400M33S and ESP32 MCU  
Variante einseitig bestückt / Variant equipped on one side  
Querformat für Outdoor / Landscape for Outdoor

### additional special components
Enclosure (transparent)  
https://www.reichelt.de/de/de/shop/produkt/industriegehaeuse_120_x_80_x_60_2mm_ip65_lichtgrau-340524

Enclosure (non-transparent)  
https://www.reichelt.de/de/de/shop/produkt/industriegehaeuse_120_x_80_x_60_2mm_ip65_lichtgrau-340515

Gehäuse Maßzeichnung:
https://cdn-reichelt.de/documents/datenblatt/C700/6U07120806437_6U-120806_DB.pdf

### Erläuterung zur Schutzbeschaltung
• Die Transient Voltage Suppressor Diode schützt vor ESD mit einer VBR = 5,6V min. @ I=1mA  
• Die 2 Schottky-Dioden entkoppeln die Versorgungseingänge.

Wenn das E22-Modul über das ESP32-Board versorgt wird, dann ist auch eine Schottky-Diode im Spannungspfad, aber es können u.U. über den USB-µ Stecker nicht die zusätzlich zum ESP32-Board erforderlichen 650mA für den E22 beim Senden geliefert werden.

Bei Versorgung über externe USB-C ist ebenso eine Schottky-Diode zur Entkopplung, bringt aber den Vorteil der höheren Stromverfügbarkeit und robusteren USB-C Verbinder. (nom. 5V/3A)

Bei Versorgung über ein externes Netzgerät über Schraubklemmen ist zwar auch eine Schottky-Diode erforderlich, aber bei Verwendung des **DC/DC-Wandler-Boards HW-613** kann mit bis zu 6-24V DC versorgt werden. Zusätzlich ist eine Feinsicherung und eine Schutzdiode gegen Verpolung eingebaut worden.

Für genauere Infos siehe die entsprechenden Datenblätter der Bauteile.

### Erläuterungen zum Gehäuseeinbau:
• Das Gehäuse verfügt über 4 Stk. Sacklöcher Ø3,2x4.  
• Darin können M2x4x3,5 Einpressmutter eingeschmolzen werden, wenn **keine** Schraubklemme+DC/DC-Wandler verwendet werden.  
• Bei Verwendung der Schraubklemme + DC/DC-Wandler, der auf der Rückseite der PCB platziert ist, muss ein größerer Abstand der PCB vom Gehäuseboden durch Verwendung von M2x**6**x3,5 Einpressmuttern eingehalten werden. Alternativ können auch Abstandsröhrchen L≥1,5mm verwendet werden (z.B. Ms-Rohr Ø3) und M2x8 Schrauben.  
• Bei anderem Bedarf können aber auch die Befestigungsbohrungen auf der PCB aufgebohrt werden.  
![Einpressbuchse_M2x4x3,5](https://github.com/user-attachments/assets/9b76f58b-3f03-4ac9-bbe7-2f518731cc2d)

Für das wasserdichte Gehäuse ist eine Druckausgleichsmembran zu empfehlen, damit das Wasser auch wieder herausdiffundieren kann. Sonst steht irgendwann die Leiterplatte unter Wasser.  
z.B. https://shop.bb-sensors.com/Druck/Drucksensoren/Druckausgleich-Membran-VPE-12-Stueck.html  
oder https://www.reichelt.at/at/de/shop/produkt/druckausgleichselement_m12_schwarz_2_stueck-371154  
oder https://www.amazon.de/dp/B088QJG676

Je nach Aufstellungsort kann auch eine einfache ≈Ø2mm Bohrung zum Druckausgleich ausreichen.

### Erläuterung zur SMA-Antennen-Buchse:
Durch die stehende SMA-Buchse ist eine mechanische Entkopplung von Gehäuse-PCB-Montage-SMA-Buchse zu einer ev. am Gehäuse montierter Antennen-Buchse, über Koaxkabel, gegeben. Bei Verwendung ohne Gehäuse kann auch eine gewinkelte SMA-Buchse eingebaut werden.  
Als Gehäusedurchführung kann eine dichte **N-Buchse <> U.FL IPEX** verwendet werden  
https://www.amazon.de/dp/B0C8J131PD

Alternativ eine SMA-Bu <> SMA-Bu:  
https://www.conrad.at/de/p/bkl-electronic-0409093-0409093-sma-adapter-sma-buchse-sma-buchse-1-st-457659.html

Alternativ eine IPEX <> SMA-Einbaubuchse:  
...

Alternativ eine SMA-Bu <> N-Bu mit Flansch, aber ohne Dichtung (ev. Dichtfolie verwenden):  
https://www.reichelt.at/at/de/shop/produkt/hf_n_buchse_sma_flanschbuchse-141249

### Programmierkabel für ESP32:
könnte wegen der nur 20cm im Gehäuse verbleiben:  
https://www.reichelt.at/at/de/shop/produkt/dual_easy_usb_2_0_kabel_a_st_auf_micro_b_st_gew_0_2_m-287766  
oder einen Winkeladapter verwenden:  
https://www.amazon.de/dp/B0CRVH7JRD

### Erläuterung zur USB-C Buchse:
Das Breakout Board mit der stehenden USB-C Buchse ermöglicht ein leichtes Anstecken der externen Versorgung.  
Es reicht sicher, dies mit einem Spiegelband aufzukleben und dann mit Drahtstückchen zu verbinden.  
USB-C vertical breakout board https://de.aliexpress.com/item/1005007821332638.html

### Ergänzung zur Frage: "PD oder nicht?"
Für USB-C PD (Power Delivery) ist ein Kommunikations-IC an CC1 & CC2 erforderlich.  
Wenn dieser nicht vorhanden ist, dann kann nur 5V geliefert werden und über die Widerstände an CC1 & CC2 wird der Strom "eingestellt".  
**5k1 sind für 5V/3A**

**Für USB-C Versorgung gibt es verschiedene Lösungen, die in hier aufgelistet werden ...**  
**... stay tuned ...**

***OE3WAS - Wolfgang - 2.11.2024***
