---
id: doc3
title: Start
---

## 1 Hardware- und Softwarevoraussetzungen
Hardwarevoraussetzungen:

-  Rasperry Pi 4 mit mindestens 4 GB RAM 
-  ein passendes Gehäuse mit Lüfter für den Raspberry Pi
-  Offizielles Raspberry Pi Netzteil
-  Eine 2,5 Zoll USB-Festplatte (ab 250 GB oder mehr) - - > Wichtig: achtet darauf, das die USB-SSD   
   Festplatte eine externe Spannungsversorgung, also ein Netzteil mitgeliefert wird. 
-  USB - Kartenlesegerät für microSD Karten
-  Monitor mit HDMI Anschluss
-  Einen Micro-HDMI auf HDMI Adapter
-  Eine externe USB-Tastatur + kabelgebundene USB - Maus
-  Netzwerk bzw. Ethernet-LAN-Kabel mit einem RJ 45 Stecker (CAT-6)
-  Optional: Sunfounder 7 Zoll Touchscreen Display 
-  Optional: 1 microSD Karte mit 64 GB oder mehr. (Falls Ihr keine SSD verwenden wollt, würde ich aus
    Performancegründen für einen dauerhaften Nodebetrieb jedoch nicht empfehlen. Für Testzwecke ist das jedoch völlig ausreichend)

Softwarevoraussetzungen:

-  Raspberry Pi OS (64 bit)-beta
-  BalenaEtcher – Flash Tool um Rasperry Pi OS (64-bit) auf die USB-SSD-Festplatte zu flashen

Entpackt die heruntergeladene zip-Datei (2020-05-27-raspios-buster-arm64) am besten gleich in Eurem Download Verzeichnis. 

Damit hätten wir das Handwerkszeug zusammen und wir können uns nun der weiteren Einrichtung zuwenden. 


## 2 Download und Einrichtung von Raspberry Pi OS (64 bit)-beta

Ladet Euch nun das bekannte Flash Tool BalenaEtcher herunter:

- [ Download BalenaEtcher Flashtool](https://www.balena.io/etcher/)

Unter Windows: Navigiert zu Eurem Download Ordner und startet die Installation des Programms unter Windows mit einem Doppelklick. 

Unter Linux: Navigiert zu Eurem Download Ordner und führt einen Rechtsklick auf das heruntergeladene BalenaEtcher Flash-Tool aus. Öffnet die Eigenschaften und klickt auf den Reiter „Zugriffsrechte“ und setzt dort den Haken bei „der Datei erlauben, sie als Programm auszuführen“. Danach könnt Ihr die Datei mit einem Doppelklick ausführen. 

1. Klickt auf "Flash from file" und wählt das heruntergeladene und entpackte "2020-05-27-raspios-buster-arm64.img", aus Eurem Download Ordner auf Eurem Rechner aus. 

<img src="../images/etcher1.png">

2. Wählt nun unter "Select target" das Zielmedium, also die angeschlossene USB-SSD-Festplatte aus. 

<img src="../images/etcher2.png">

Die angeschlossene USB-SSD-Festplatte wird in der Regel automatisch von BalenaEtcher erkannt.

<img src="../images/etcher3.png">

Hinweis: Falls Ihr die Meldung "... your SSD drive is unusally large for an SD card or USB stick" könnt Ihr diese vernachlässigen. Klickt auf Continue und danach auf Flash! 

3. "Flash" startet den Einrichtungsvorgang, nach Abschluss des Flashvorgangs findet noch ein Validierungsvorgang statt und anschließend habt Ihr ein startfähiges USB-SSD-Medium mit dem Betriebssystem Raspberry Pi OS (64 bit) - beta erstellt.

<img src="../images/etcher4.png">

## 3 Kurzversion zur Einrichtung von Raspihive

Nachfolgend beschreibe ich stichpunktartig die erforderlichen Schritte zur Einrichtung von Raspihive. 
Nach dem Ihr das Raspbian OS (64 bit) beta Betriebssystem auf Eure USB-SSD Festplatte geflasht habt, könnt Ihr Euren Raspberry Pi mit Eurer Peripherie verkabeln und starten. Die weiteren Schritte sind: 
1. Grundlegende Konfiguration des Raspberry Pi‘s mit dem Einrichtungsassistent.
2. Fritz!Box (Router) Portfreigaben für die folgenden Ports erstellen : 80, 443, 15600 alle TCP und Port: 14626 UDP.
3. Klonen des Raspihive-Repositorys:
sudo git clone https://github.com/Raspihive/raspihive.git
4. Im Verzeichnis „pi“ die Textdatei „Raspihive“ auf den Desktop kopieren und mit ```sudo chmod +x Raspihive``` ausführbar machen.
5. Beim ersten Start von Raspihive:  Führt einen Doppelklick auf die erstellte Startdatei aus und wählt „im Terminal ausführen“ aus. Anschließend könnt Ihr im „Install Menu“ Hornet installieren.
Wenn Ihr eine eigene Domain besitzt, und DynDNS in der Fritzbox eingetragen oder bspw. den No-IP-Client installiert habt, könnt Ihr nach der Installation des Reverse Proxy‘s + Certbot Eure Domain aus dem Internet unter „Eure-Domain.xx“ aufrufen. Während der Installation im Terminal werdet Ihr dazu aufgefordert, ein Passwort zu vergeben. Dies ist das Passwort für den gesicherten Dashboard Zugriff. 
Der Benutzername lautet standardmäßig „Raspihive“ (ohne die „“).
6. Nach der Installation könnt Ihr dann im Terminal den Certbot Wizard mit dem Befehl 
sudo certbot –nginx
starten und für Eure Domain ein SSL-Zertifikat erhalten. 



## 4 Langversion zur Einrichtung von Raspihive

Nachfolgend beschreibe ich alle Schritte zur Einrichtung von Raspihive inklusive einiger Zusatzerklärungen. 

### 4.1 Grundlegende Konfiguration des Raspberry Pi‘s mit dem Einrichtungsassistent

Nach dem Flash-Vorgang Eurer USB-SSD-Festplatte mit BalenaEtcher könnt Ihr diese nun mit dem USB Port Eures Raspberry Pi‘s verbinden. Schließt darüber hinaus die USB-Maus und Tastatur an, verbindet das microHDMI Kabel mit einem der beiden microHDMI Ports des Raspberry‘s und das andere Ende des Monitorkabels in den HDMI Port Eures Hauptmonitors. Hierbei wird in der Regel ein HDMI auf microHDMI Adapter benötigt.  Optional jedoch empfehlenswert: Verbindet Euren Raspberry Pi vom Router- oder vom Switch ausgehend, per Netzwerkkabel mit der RJ 45 Buchse des Pi‘s. Schließt als letztes die Spannungsversorgung an den Pi mit dem originalen Rasberry Pi Netzteil an die USB-C-Schnittstelle an. 
Der erste Bootvorgang kann durchaus 5 – 10 Minuten dauern. 
In der Testphase hat sich herausgestellt, dass der USB-Bootvorgang bei manchen USB-SSD Festplatten, welche am USB 3.0 Port  (blaue Ports) am Raspberry Pi 4 angeschlossen sind, manchmal nicht ordnungsgemäß funktioniert. Falls dies bei Euch der Fall sein sollte, müsst Ihr für den erstmaligen Bootvorgang den USB 2.0 Port verwenden. In der Raspihive-App habe ich einen Fix dafür eingebaut, sodass nach Durchführung des SSD-Fixes Eure Festplatte danach auch von dem USB 3.0 Port starten sollte. 

Stellt an Eurem Hauptmonitor den richtigen HDMI-Port ein und Ihr werdet nach ungefähr 5 Minuten mit dem Anmeldebildschirm bzw. dem Ersteinrichtungsassistent begrüßt. 

Notiert Euch bitte die lokale IP-Adresse des Raspberry Pi‘s und klickt auf „Next“…

<img src="../images/etcher4.png">

und nehmt die entsprechenden Länder-, Sprach- und Zeitzonen Einstellungen vor und klickt wiederum auf „Next“...

<img src="../images/etcher4.png">

Vergebt nun ein sicheres Passwort für den standardmäßig gesetzten Benutzer Pi und klickt auf „Next“...

<img src="../images/etcher4.png">

Wenn Ihr einen schwarzen Rand zwischen der aktuellen Anzeige und Eurem Monitor seht, dann setzt den Haken bei „This screen shows a black border around the desktop“ und klickt auf „Next“...

<img src="../images/etcher4.png">

Bei diesem Schritt könnt Ihr auswählen ob Ihr Euren Raspberry Pi per WLAN mit Eurem Netzwerk verbinden möchtet. Dieser Schritt entfällt, wenn Ihr ein Netzwerkkabel in die RJ 45 Buchse des Pi‘s eingesteckt habt. Falls das bei Euch der Fall sein sollte, könnt Ihr einfach auf „Skip“ klicken...falls nicht, wählt Euren Accesspoint aus und klickt auf „Next“, anschließend müsst Ihr Euer WLAN-Zugangspasswort eingeben und der Raspberry Pi ist per WLAN mit Eurem Netzwerk verbunden. 

<img src="../images/etcher4.png">

Der nächste Schritt ist sehr wichtig. Achtet generell stets darauf, das Ihr Euer Betriebssystem aktuell haltet und regelmäßig mit Updates versorgt. Dies verbessert generell die Stabilität, Leistungsfähigkeit und Sicherheit Eures Systems. Klickt auf „Next“ um den Aktualisierungsvorgang zu starten... 

<img src="../images/etcher4.png">

welcher durchaus ein wenig Zeit beansprucht, da die verfügbaren Updates zunächst heruntergeladen...

<img src="../images/etcher4.png">

und anschließend installiert werden...

<img src="../images/etcher4.png">

Nach der erfolgreichen Aktualisierung des Systems, solltet Ihr Euren Raspberry Pi einmal neu starten, damit die Änderungen auch wirksam werden. 

<img src="../images/etcher4.png">

Klickt dazu einmal auf „Restart“ und wartet bis Ihr wieder den Desktop seht. Der Neustart kann wieder ein paar Minuten dauern, also habt etwas Geduld an dieser Stelle ;) Der nächste Neustart geht danach sehr schnell vonstatten. 

<img src="../images/etcher4.png">

### 4.2 Einrichtung der Portfreigaben in der Fritz!Box (Router) 

Bevor wir uns um die Einrichtung von Raspihive kümmern, müssen wir aktuell noch die folgenden Ports in unserem Router freigeben. 

Essentiell, Port: 14626, Protokoll UDP – Autopeering 
Essentiell, Port: 15600, Protokoll TCP – Gossip (neighbors) 
Optional, Port: 80 Protokoll TCP – Certbot
Optional, Port: 443 Protokoll TCP – Certbot

Da ich eine Fritz!Box verwende, zeige ich Euch die Einrichtung der Portfreigaben anhand der Fritzbox. 
1. Öffnet die Benutzeroberfläche der Fritz!Box indem Ihr in Euren Browser „fritz.box“ oder die lokale IP-Adresse: „192.168.178.1“ eintippt.
Das Login Passwort findet Ihr in der Regel auf dem Aufdruck, welcher an der Unterseite der Fritz!Box aufgebracht ist. Entnehmt das „Fritz!Box-Kennwort“ und gebt es auf dem Anmeldebildschirm bzw. auf der Login Seite der Fritz!Box Benutzeroberfläche ein und klickt auf „Anmelden“...

<img src="../images/etcher4.png">

Klickt danach auf: „Internet“ (1)...

<img src="../images/etcher4.png">

- - > „Freigaben“ (2)  - - > „Gerät für Freigaben hinzufügen“ (3)...

<img src="../images/etcher4.png">

Wählt nun unter dem Punkt „Gerät“ Euren Raspberry Pi aus. 

<img src="../images/etcher4.png">

Die am Anfang notierte lokale IP Adresse, welche uns im Einrichtungsassistent angezeigt wurde, muss mit dieser IP, bei Punkt 2 (roter Pfeil) übereinstimmen. Es kann ja durchaus sein, das Ihr mehr als einen Raspberry Pi verwendet und dann könnt Ihr diese anhand der unterschiedlichen lokalen IP Adresse unterscheiden. Klickt anschließend auf „Neue Freigabe“ (3)...

<img src="../images/etcher4.png">

### 4.3 Klonen des Raspihive Repositorys von Github

```
Mauris vestibulum ullamcorper nibh, ut semper purus pulvinar ut. Donec volutpat orci sit amet mauris malesuada, non pulvinar augue aliquam. Vestibulum ultricies at urna ut suscipit. Morbi iaculis, erat at imperdiet semper, ipsum nulla sodales erat, eget tincidunt justo dui quis justo. Pellentesque dictum bibendum diam at aliquet. Sed pulvinar, dolor quis finibus ornare, eros odio facilisis erat, eu rhoncus nunc dui sed ex. Nunc gravida dui massa, sed ornare arcu tincidunt sit amet. Maecenas efficitur sapien neque, a laoreet libero feugiat ut.
```

### 4.4 Verknüpfung der mitgelieferten Raspihive-Startdatei erstellen und die Datei

Nulla facilisi. Maecenas sodales nec purus eget posuere. Sed sapien quam, pretium a risus in, porttitor dapibus erat. Sed sit amet fringilla ipsum, eget iaculis augue. Integer sollicitudin tortor quis ultricies aliquam. Suspendisse fringilla nunc in tellus cursus, at placerat tellus scelerisque. Sed tempus elit a sollicitudin rhoncus. Nulla facilisi. Morbi nec dolor dolor. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Cras et aliquet lectus. Pellentesque sit amet eros nisi. Quisque ac sapien in sapien congue accumsan. Nullam in posuere ante. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Proin lacinia leo a nibh fringilla pharetra.

### 4.5 Erster Start von Raspihive und Installation der Hornet Node

Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Proin venenatis lectus dui, vel ultrices ante bibendum hendrerit. Aenean egestas feugiat dui id hendrerit. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Curabitur in tellus laoreet, eleifend nunc id, viverra leo. Proin vulputate non dolor vel vulputate. Curabitur pretium lobortis felis, sit amet finibus lorem suscipit ut. Sed non mollis risus. Duis sagittis, mi in euismod tincidunt, nunc mauris vestibulum urna, at euismod est elit quis erat. Phasellus accumsan vitae neque eu placerat. In elementum arcu nec tellus imperdiet, eget maximus nulla sodales. Curabitur eu sapien eget nisl sodales fermentum.

### 4.6 Optional: Installation des Reverse Proxy‘s + Certbot + Prozess zum Erhalt eines 			 SSL-Zertifikats von Let‘s Encrypt

Phasellus pulvinar ex id commodo imperdiet. Praesent odio nibh, sollicitudin sit amet faucibus id, placerat at metus. Donec vitae eros vitae tortor hendrerit finibus. Interdum et malesuada fames ac ante ipsum primis in faucibus. Quisque vitae purus dolor. Duis suscipit ac nulla et finibus. Phasellus ac sem sed dui dictum gravida. Phasellus eleifend vestibulum facilisis. Integer pharetra nec enim vitae mattis. Duis auctor, lectus quis condimentum bibendum, nunc dolor aliquam massa, id bibendum orci velit quis magna. Ut volutpat nulla nunc, sed interdum magna condimentum non. Sed urna metus, scelerisque vitae consectetur a, feugiat quis magna. Donec dignissim ornare nisl, eget tempor risus malesuada quis.

## 5. Weitere Funktionen von Raspihive

Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Proin venenatis lectus dui, vel ultrices ante bibendum hendrerit. Aenean egestas feugiat dui id hendrerit. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Curabitur in tellus laoreet, eleifend nunc id, viverra leo. Proin vulputate non dolor vel vulputate. Curabitur pretium lobortis felis, sit amet finibus lorem suscipit ut. Sed non mollis risus. Duis sagittis, mi in euismod tincidunt, nunc mauris vestibulum urna, at euismod est elit quis erat. Phasellus accumsan vitae neque eu placerat. In elementum arcu nec tellus imperdiet, eget maximus nulla sodales. Curabitur eu sapien eget nisl sodales fermentum.

## 6. Ausblick und weitere Entwicklung von Raspihive

Phasellus pulvinar ex id commodo imperdiet. Praesent odio nibh, sollicitudin sit amet faucibus id, placerat at metus. Donec vitae eros vitae tortor hendrerit finibus. Interdum et malesuada fames ac ante ipsum primis in faucibus. Quisque vitae purus dolor. Duis suscipit ac nulla et finibus. Phasellus ac sem sed dui dictum gravida. Phasellus eleifend vestibulum facilisis. Integer pharetra nec enim vitae mattis. Duis auctor, lectus quis condimentum bibendum, nunc dolor aliquam massa, id bibendum orci velit quis magna. Ut volutpat nulla nunc, sed interdum magna condimentum non. Sed urna metus, scelerisque vitae consectetur a, feugiat quis magna. Donec dignissim ornare nisl, eget tempor risus malesuada quis.