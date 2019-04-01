# Protokoll-6
## Thema: Modbus/Temperatursensor
**Professor:** SX  
**Übungsdatum:** 18.12.2018  
**Author, KNr.:** Winter Matthias, 17  
**Anwesend:** Sarah Vezonik, Alois Vollmaier, Patrick Wegl, Mercedes Wesonig, Winter Matthias, Winter Thomas  

---

## Themenübersicht 
### 1. Modbus
### 2. Temperatursensor am µC
### 3. ADC
### 4. Programm


--- 

## 1. Modbus 
Das Kommunikationsprotokoll ist ein einfaches zustandsloses Protokoll basierend auf einem Request/Response Prinzip. Grundsätzlich unterscheidet man zwischen **drei** Varianten:   
  
  
* **Modbus ASCII** Rein textuelle byteweise Übertragung von Daten.  
* **Modbus RTU** Binäre byteweise Übertragung von Daten.  
* **Modbus TCP** Übertragung der Daten in TCP Paketen.   

 ![alt text](https://github.com/winmam14/Protokoll-5/blob/master/modbus_general_modbus_frame_png.png)  
 Quelle: LMS Skript  
   
   Wir haben für unsere Anwendung Modbus-ASCII verwendet, da es einfacher zu verstehen und zu verwenden ist.

### 1.1 Modbus ASCII
Im ASCII Transmission Mode werden die Frame-Bytes als ASCII-Text versendet. Für die Konfiguration der seriellen Schnittstelle werden standardmäßig nur 7 Daten-Bits verwendet! Geräte dürfen im Bedarfsfall aber auch eine davon abweichende Festlegung haben.   

Jeder Modbus **Serial Line ASCII Frame** hat folgenden Aufbau:  
 ![alt text](https://github.com/winmam14/Protokoll-5/blob/master/modbus_serial_ascii_frame_png.png)  
 Quelle: LMS Skript
 
 #### Unterrichts Beispiel
 
 Die im Unterricht als Beispiel gebrachte ADU ist die Request um einen Sensor auszlesen:  
 ``` 
 :010400000001BA<CR><LF>
 ```  
Die PDU für dieses Beispiel sieht wie folgt aus:  
 ``` 
 0400000001
 ```     

## 2. Temperatursensor am µC
  
  Im Unterricht verwenden wir den Arduino Nano welcher mit einem ATmega328p ausgestattet ist. Dieser besitzt einen eingebauten Temperatursensor. Diesen haben wir versucht über Modbus-ASCII auszulesen.

## 3. ADC
Ein Analog-Digital-Umsetzer ist ein elektronisches Gerät, Bauelement oder Teil eines Bauelements zur Umsetzung analoger Eingangssignale in einen digitalen Datenstrom, der dann weiterverarbeitet oder gespeichert werden kann. Weitere Namen und Abkürzungen sind ADU, Analog-Digital-Wandler oder A/D-Wandler.  
  
  Analog-Digital-Umsetzer sind elementare Bestandteile fast aller Geräte der modernen Kommunikations- und Unterhaltungselektronik wie z. B. Mobiltelefonen, Digitalkameras, oder Camcordern. Zudem werden sie, wie in unserer Anwendung, zur Messwerterfassung verwendet.  

![alt text](https://github.com/winmam14/Protokoll-6/blob/master/ADC.PNG?raw=true)   
Quelle: ATmega328p Datenblatt

### 3.2 Sukzessive Approximation
Sukzessive Approximation, bedeutet so viel wie schrittweise Annäherung. So heißt das Verfahren wie unser ADC das Analoge Signal in ein Digitales umwandelt.    

 Das Messsignal Uin wird in n Schritten digitalisiert, wobei die Genauigkeit bei jedem Schritt um 1 Bit steigt. Bei jedem Schritt wird die Eingangsspannung mit einer Referenzspannung Uref verglichen, die durch einen DA-Wandler erzeugt wird. Je nachdem, ob Uin größer oder kleiner als die Spannung des DA-Wandlers ist, wird die Referenzspannung im nächsten Schritt um die halbe Schrittweite des letzten Schritts nach oben oder nach unten verändert. Dadurch nähert sich die Spannung des DA-Wandlers immer mehr der Eingangsspannung an. Zum Schluss, wenn das letzte Bit des DA-Wandlers gesetzt ist, entspricht der Wert des DACs der Eingangsspannung.  
 ![alt text](https://github.com/winmam14/Protokoll-6/blob/master/adcsukap.png?raw=true)       
Quelle:[Hier](http://www.vias.org/mikroelektronik/adc_succapprox.html) klicken um zu Quelle zu gelangen!   
## 4. Programm


