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
  
  Im Unterricht verwenden wir den Arduino Nano welcher mit einem ATmega328p ausgestattet ist. Dieser besitzt einen eingebauten Temperatursensor welcher das Modbus Protokoll unterstützt.

## 3. ADC


![alt text](https://github.com/winmam14/Protokoll-6/blob/master/ADC.PNG?raw=true) 
Quelle: ATmega328p Datenblatt
