# Smarthome

## Temperatursensor via One-Wire-Bus anschliessen

Verwendet wird der Temperatursonsor DS1820. Dieser hat drei Anschlüsse: Masse (GND, Pin 1), Daten (DQ, Pin 2) und Betriebsspannung (VDD, Pin3). Man kann VDD und GND verbinden und so den Sensor mit einer parasitäre Stromversorgung von 3 bis 5 Volt betreiben. Der Anschluss des Schaltkreises ist dadurch mit einer einfachen zweiadrigen verdrillten Leitung möglich. Jeder Sensor besitzt einen vom Hersteller vergebenen eindeutigen Code.

Bei dem verwendeten, wasserfesten Sensor haben die Kabelfarben folgende Bedeutung:

Rotes Kabel: +5V => 1
Schwarzes Kabel: Erdung => 2
Gelb Kabel: Daten => 3

### Voraussetzung 

Folgende Schritte sind notwendig, damit man die Temperatur auslesen kann:

- Raspberry Pi Booten und mit "raspi-config" unter Schnittstellen den One-Wire Bus aktivieren
- Reboot
- dann unter /boot/config.txt den Eintrag "dtoverlay=w1-gpio,gpiopin=4,pullup=off" bzw. "dtoverlay=w1-gpio,gpiopin=4,pullup=on"
- Reboot

### Anschluss mit Pullup-Widerstand

Den Datenanschluss DQ des DS1820 verbindet man direkt mit dem Anschluss GPIO4 der GPIO-Schnittstelle des Raspberry Pi. GND und VDD liegen am Masseanschluss GND. Die parasitäre Stromversorgung bewerkstelligt ein Pullup-Widerstand von 4,7 kΩ zwischen dem 3,3 Volt Anschluss 3V3 und GPIO4.

Das Schaltbild sieht wie folgt aus:

[[https://github.com/mabaumga/smarthome/blob/master/img/owb1.png]]


### Anschluss ohne Pullup-Widerstand

In dieser Variante werden alle drei Kabel verwendet. Auf der Platine sieht das dann wie folgt aus:

[[https://github.com/mabaumga/smarthome/blob/master/img/owb2.png]]

Mit dem Raspberry werden die Kabel wie folgt verbunden:

Rot: 3,3 V
Schwarz: Gnd
Gelb: GPIO4


## Anschluss des BME270

Hier verwendet man 



