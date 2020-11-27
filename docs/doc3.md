---
id: doc3
title: Start
---

## Hardware- und Softwarevoraussetzungen
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


## Download und Einrichtung von Raspberry Pi OS (64 bit)-beta

Ladet Euch nun das bekannte Flash Tool BalenaEtcher herunter:

- [ Download BalenaEtcher Flashtool](https://www.balena.io/etcher/)

Unter Windows: Navigiert zu Eurem Download Ordner und startet die Installation des Programms unter Windows mit einem Doppelklick. 

Unter Linux: Navigiert zu Eurem Download Ordner und führt einen Rechtsklick auf das heruntergeladene BalenaEtcher Flash-Tool aus. Öffnet die Eigenschaften und klickt auf den Reiter „Zugriffsrechte“ und setzt dort den Haken bei „der Datei erlauben, sie als Programm auszuführen“. Danach könnt Ihr die Datei mit einem Doppelklick ausführen. 

1. Klickt auf "Flash from file" und wählt das heruntergeladene und entpackte "2020-05-27-raspios-buster-arm64.img", aus Eurem Download Ordner auf Eurem Rechner aus. 

<img src="../images/etcher1.png">
## Kurzversion zur Einrichtung von Raspihive

Nulla facilisi. Maecenas sodales nec purus eget posuere. Sed sapien quam, pretium a risus in, porttitor dapibus erat. Sed sit amet fringilla ipsum, eget iaculis augue. Integer sollicitudin tortor quis ultricies aliquam. Suspendisse fringilla nunc in tellus cursus, at placerat tellus scelerisque. Sed tempus elit a sollicitudin rhoncus. Nulla facilisi. Morbi nec dolor dolor. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Cras et aliquet lectus. Pellentesque sit amet eros nisi. Quisque ac sapien in sapien congue accumsan. Nullam in posuere ante. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Proin lacinia leo a nibh fringilla pharetra.

## Langversion zur Einrichtung von Raspihive

Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Proin venenatis lectus dui, vel ultrices ante bibendum hendrerit. Aenean egestas feugiat dui id hendrerit. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Curabitur in tellus laoreet, eleifend nunc id, viverra leo. Proin vulputate non dolor vel vulputate. Curabitur pretium lobortis felis, sit amet finibus lorem suscipit ut. Sed non mollis risus. Duis sagittis, mi in euismod tincidunt, nunc mauris vestibulum urna, at euismod est elit quis erat. Phasellus accumsan vitae neque eu placerat. In elementum arcu nec tellus imperdiet, eget maximus nulla sodales. Curabitur eu sapien eget nisl sodales fermentum.

## 4.1 Grundlegende Konfiguration des Raspberry Pi‘s mit dem Einrichtungsassistent

Phasellus pulvinar ex id commodo imperdiet. Praesent odio nibh, sollicitudin sit amet faucibus id, placerat at metus. Donec vitae eros vitae tortor hendrerit finibus. Interdum et malesuada fames ac ante ipsum primis in faucibus. Quisque vitae purus dolor. Duis suscipit ac nulla et finibus. Phasellus ac sem sed dui dictum gravida. Phasellus eleifend vestibulum facilisis. Integer pharetra nec enim vitae mattis. Duis auctor, lectus quis condimentum bibendum, nunc dolor aliquam massa, id bibendum orci velit quis magna. Ut volutpat nulla nunc, sed interdum magna condimentum non. Sed urna metus, scelerisque vitae consectetur a, feugiat quis magna. Donec dignissim ornare nisl, eget tempor risus malesuada quis.

## 4.2 Einrichtung der Portfreigaben in der Fritz!Box (Router) 

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque elementum dignissim ultricies. Fusce rhoncus ipsum tempor eros aliquam consequat. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus elementum massa eget nulla aliquet sagittis. Proin odio tortor, vulputate ut odio in, ultrices ultricies augue. Cras ornare ultrices lorem malesuada iaculis. Etiam sit amet libero tempor, pulvinar mauris sed, sollicitudin sapien.

## 4.3 Klonen des Raspihive Repositorys von Github

```
Mauris vestibulum ullamcorper nibh, ut semper purus pulvinar ut. Donec volutpat orci sit amet mauris malesuada, non pulvinar augue aliquam. Vestibulum ultricies at urna ut suscipit. Morbi iaculis, erat at imperdiet semper, ipsum nulla sodales erat, eget tincidunt justo dui quis justo. Pellentesque dictum bibendum diam at aliquet. Sed pulvinar, dolor quis finibus ornare, eros odio facilisis erat, eu rhoncus nunc dui sed ex. Nunc gravida dui massa, sed ornare arcu tincidunt sit amet. Maecenas efficitur sapien neque, a laoreet libero feugiat ut.
```

## 4.4 Verknüpfung der mitgelieferten Raspihive-Startdatei erstellen und die Datei

Nulla facilisi. Maecenas sodales nec purus eget posuere. Sed sapien quam, pretium a risus in, porttitor dapibus erat. Sed sit amet fringilla ipsum, eget iaculis augue. Integer sollicitudin tortor quis ultricies aliquam. Suspendisse fringilla nunc in tellus cursus, at placerat tellus scelerisque. Sed tempus elit a sollicitudin rhoncus. Nulla facilisi. Morbi nec dolor dolor. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Cras et aliquet lectus. Pellentesque sit amet eros nisi. Quisque ac sapien in sapien congue accumsan. Nullam in posuere ante. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Proin lacinia leo a nibh fringilla pharetra.

## 4.5 Erster Start von Raspihive und Installation der Hornet Node

Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Proin venenatis lectus dui, vel ultrices ante bibendum hendrerit. Aenean egestas feugiat dui id hendrerit. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Curabitur in tellus laoreet, eleifend nunc id, viverra leo. Proin vulputate non dolor vel vulputate. Curabitur pretium lobortis felis, sit amet finibus lorem suscipit ut. Sed non mollis risus. Duis sagittis, mi in euismod tincidunt, nunc mauris vestibulum urna, at euismod est elit quis erat. Phasellus accumsan vitae neque eu placerat. In elementum arcu nec tellus imperdiet, eget maximus nulla sodales. Curabitur eu sapien eget nisl sodales fermentum.

## 4.6 Optional: Installation des Reverse Proxy‘s + Certbot + Prozess zum Erhalt eines 			 SSL-Zertifikats von Let‘s Encrypt

Phasellus pulvinar ex id commodo imperdiet. Praesent odio nibh, sollicitudin sit amet faucibus id, placerat at metus. Donec vitae eros vitae tortor hendrerit finibus. Interdum et malesuada fames ac ante ipsum primis in faucibus. Quisque vitae purus dolor. Duis suscipit ac nulla et finibus. Phasellus ac sem sed dui dictum gravida. Phasellus eleifend vestibulum facilisis. Integer pharetra nec enim vitae mattis. Duis auctor, lectus quis condimentum bibendum, nunc dolor aliquam massa, id bibendum orci velit quis magna. Ut volutpat nulla nunc, sed interdum magna condimentum non. Sed urna metus, scelerisque vitae consectetur a, feugiat quis magna. Donec dignissim ornare nisl, eget tempor risus malesuada quis.

## 5. Weitere Funktionen von Raspihive

Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Proin venenatis lectus dui, vel ultrices ante bibendum hendrerit. Aenean egestas feugiat dui id hendrerit. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Curabitur in tellus laoreet, eleifend nunc id, viverra leo. Proin vulputate non dolor vel vulputate. Curabitur pretium lobortis felis, sit amet finibus lorem suscipit ut. Sed non mollis risus. Duis sagittis, mi in euismod tincidunt, nunc mauris vestibulum urna, at euismod est elit quis erat. Phasellus accumsan vitae neque eu placerat. In elementum arcu nec tellus imperdiet, eget maximus nulla sodales. Curabitur eu sapien eget nisl sodales fermentum.

## 6. Ausblick und weitere Entwicklung von Raspihive

Phasellus pulvinar ex id commodo imperdiet. Praesent odio nibh, sollicitudin sit amet faucibus id, placerat at metus. Donec vitae eros vitae tortor hendrerit finibus. Interdum et malesuada fames ac ante ipsum primis in faucibus. Quisque vitae purus dolor. Duis suscipit ac nulla et finibus. Phasellus ac sem sed dui dictum gravida. Phasellus eleifend vestibulum facilisis. Integer pharetra nec enim vitae mattis. Duis auctor, lectus quis condimentum bibendum, nunc dolor aliquam massa, id bibendum orci velit quis magna. Ut volutpat nulla nunc, sed interdum magna condimentum non. Sed urna metus, scelerisque vitae consectetur a, feugiat quis magna. Donec dignissim ornare nisl, eget tempor risus malesuada quis.