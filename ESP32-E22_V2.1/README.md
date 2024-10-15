# esp32-e22-lora-board
Carrier Board for Lora Tranceiver like E22-400M33S and ESP32 MCU

V 2.1.x  Variante einseitig bestückt / Variant equipped on one side


### additional special components

Enclosure (transparent) https://www.reichelt.de/de/de/shop/produkt/industriegehaeuse_120_x_80_x_60_2mm_ip65_lichtgrau-340524

Enclosure (non-transparent) https://www.reichelt.de/de/de/shop/produkt/industriegehaeuse_120_x_80_x_60_2mm_ip65_lichtgrau-340515

Gehäuse Maßzeichnung:
https://cdn-reichelt.de/documents/datenblatt/C700/6U07120806437_6U-120806_DB.pdf

USB-C vertical breakout board https://de.aliexpress.com/item/1005007821332638.html  
USB-C Gehäusebuchse https://de.aliexpress.com/item/1005005388486563.html


### Erläuterung zur Schutzbeschaltung

• Die Transient Voltage Suppressor Diode schützt vor ESD mit einer VBR = 5,6V min. @ I=1mA  
• Die 2 Schottky-Dioden entkoppeln die Versorgungseingänge.

Wenn das E22-Modul über das ESP32-Board versorgt wird, dann ist auch eine Schottky-Diode im Spannungspfad, aber es können u.U. über den USB-µ Stecker nicht die zusätzlich zum ESP32-Board erforderlichen 650mA für den E22 beim Senden geliefert werden.

Bei Versorgung über externe USB-C ist ebenso eine Schottky-Diode zur Entkopplung, bringt aber den Vorteil der höheren Stromverfügbarkeit und robusteren USB-C Verbinder. (nom. 5V/3A)

Bei Versorgung über ein externes Netzgerät über Schraubklemmen ist zwar auch eine Schottky-Diode erforderlich, aber es könnte mit ≈5,5V versorgt werden, um den Spannungsabfall auszugleichen, um den E22 max. zu versorgen.

Für genauere Infos siehe die entsprechenden Datenblätter der Bauteile.


### Erläuterungen zum Gehäuseeinbau:

Das Gehäuse verfügt über 4 Stk. Sacklöcher Ø3,2x4. Darin können M2x4x3,5 Einpressmutter eingeschmolzen werden.
Bei anderem Bedarf können die Befestigungsbohrungen auf der PCB aufgebohrt werden.  
![Einpressbuchse_M2x4x3,5](https://github.com/user-attachments/assets/9b76f58b-3f03-4ac9-bbe7-2f518731cc2d)

Für das wasserdichte Gehäuse ist eine Druckausgleichsmembran zu empfehlen, damit das Wasser auch wieder herausdiffundieren kann. Sonst steht irgendwann die Leiterplatte unter Wasser.  
z.B. https://shop.bb-sensors.com/Druck/Drucksensoren/Druckausgleich-Membran-VPE-12-Stueck.html  
oder https://www.reichelt.at/at/de/shop/produkt/druckausgleichselement_m12_schwarz_2_stueck-371154  
Je nach Aufstellungsort kann auch eine einfache ≈Ø2mm Bohrung zum Druckausgleich ausreichen.

### Erläuterung zur SMA-Antennen-Buchse:

Durch die stehende SMA-Buchse ist eine mechanische Entkopplung von Gehäuse-PCB-Montage-SMA-Buchse zu einer ev. am Gehäuse montierter Antennen-Buchse, über Koaxkabel, gegeben. Bei Verwendung ohne Gehäuse kann auch eine gewinkelte SMA-Buchse eingebaut werden.  
Als Gehäusedurchführung kann eine dichte SMA-Bu <> SMA-Bu verwendet werden:  
https://www.conrad.at/de/p/bkl-electronic-0409093-0409093-sma-adapter-sma-buchse-sma-buchse-1-st-457659.html

### Erläuterung zur USB-C Buchse:

Das Breakout Board mit der stehenden USB-C Buchse ermöglicht ein leichtes Anstecken der externen Versorgung.  
Es reicht sicher, dies mit einem Spiegelband aufzukleben und dann mit Drahtstückchen zu verbinden.  
Optional kann da aber auch eine 4-pol Stiftleiste od. Buchsenleiste eingebaut werden und eine 4-pol USB-C Einbaubuchse mit Drähten verbunden werden.  
**Aliexpress** Link siehe Stückliste.  
https://www.amazon.de/RUNCCI-YUN-Typ-C-Buchse%EF%BC%8CUSB-C-Buchse-Panelmontage-3A-Schnelllade-Typ-C-Buchse-USB-C-Pigtail-Kabel/dp/B0CPLRH4W6/

### Ergänzung zur Frage: "PD oder nicht?"
Für USB-C PD (Power Delivery) ist ein Kommunikations-IC an CC1 & CC2 erforderlich.  
Wenn dieser nicht vorhanden ist, dann kann nur 5V geliefert werden und über die Widerstände an CC1 & CC2 der Strom "eingestellt" werden.  
**5k1 sind für 5V/3A**
