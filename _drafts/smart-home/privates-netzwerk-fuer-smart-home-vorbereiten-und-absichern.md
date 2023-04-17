---
layout: post
title: Privates Netzwerk für Smart Home vorbereiten und absichern
description:
image:
categories: [Smart Home]
tags: [Netzwerk,Unifi,VLAN,Router,Gateway,Firewall,Switch,Access Point]
---
## Motivation
In den letzten Jahren haben einige Smart Devices in meinem zu Hause eingezogen. Sie sind leider dafür bekannt, dass sie nicht besonders sicher sind. Dieser Umstand und mein Bruder, der mir ins Gewissen geredet hat, haben mich dazu bewegt, mein Netzwerk sicherer gegen Angriffe von außen zu machen. Schnell war klar, die AVM Fritzbox, die wohl bei den meisten im Einsatz ist, erfüllt nicht die notwendigen Anforderungen. Also musste etwas anderes her...

## Anforderungen
Im Internet findet man viele hilfreiche Seiten, die einem Tipps geben, wie man sein Netzwerk gegen Angreifer absichert. Das Bundesministerium für Sicherheit in der Informationstechnik (BSI) hat in meinen Augen einen sehr guten [Artikel](https://www.bsi.bund.de/DE/Themen/Verbraucherinnen-und-Verbraucher/Informationen-und-Empfehlungen/Internet-der-Dinge-Smart-leben/Smart-Home/smart-home_node.html) dazu verfasst. Einige weitere nützliche [Quellen](#quellen) sind am Ende des Beitrags gelistet.

Folgende Themen sind mir bei der Auswahl der Komponenten wichtig gewesen:
1. Firewall
2. Separierung der Netzwerke (VLAN)
   1. Heimnetz
   2. Gästenetz
   3. IoT-Netz
3. Separate Komponenten für die verschiedenen Funktionen
   1. Modem: Aufbau der Internetverbindung mit dem Internet Service Provider (ISP)
   2. Gateway/Router: Vergabe der IP Adressen und Routing der Verbindungen/Anfragen
   3. Switch: Verbindung von Netzwerk-Clients via LAN
   4. WLAN Access Point: Verbindung von Netzwerk-Clients via WLAN
## Entscheidungsprozess

Wie bereits erwähnt hat die Fritzbox die Anforderungen an ein sicheres Netzwerk für Smart Home nicht erfüllen können. Da ich kein professioneller Netzwerkadministrator bin, sollte es etwas sein, dass auch durch technikaffine Laien konfigurierbar und wartbar ist. Mir haben die Beiträge im Forum [Administrator.de](www.administrator.de) sehr geholfen. Hersteller, die immer wieder genannt werden, sind beispielsweise:
* Cisco
* Mikrotik
* NetGear
* Ubiquiti
* Zyxel

Die Meinungen zur Hardware gehen stark auseinander. Letztlich habe ich mich für die Ubiquiti Unifi Serie entschieden. Die Komponenten sind bezahlbar und die Bedienung leichter als bei professioneller Hardware. Die eingeschränkteren Konfigurationsmöglichkeiten sind der Grund warum zum Teil von Unifi abgeraten wird. Die Unifi Serie gilt als Prosumer Hardware. Hier finde ich mich wieder!

## Komponenten

Ich war initial sehr überrascht, wie viele Rollen/Funktionen die FritzBox inne hat. Letztlich habe ich die FritzBox gegen 4 andere Komponenten ersetzt. Dabei habe ich mich für die Komponentenauswahl sehr an einem [Artikel von The Smart Home Journey](https://thesmarthomejourney.com/2021/06/14/smart-home-network-unifi/) orientiert. Entsprechend sieht meine Auswahl wie folgt aus:

| #   |     Komponente      |  Link          | Gebrauchtpreis |
| --- | -------------       | :-----------:  | ----------:     |
| 1   | DrayTek Vigor166 | [Geizhals](https://geizhals.de/draytek-vigor166-v166-a-a2272803.html) | ~100€ |
| 2   | Ubiquiti UniFi Security Gateway (USG) | [Geizhals](https://geizhals.de/ubiquiti-unifi-security-gateway-usg-a1213487.html) | ~75€ |
| 3   | Ubiquiti UniFi Switch (US-8-60) | [Geizhals](https://geizhals.de/ubiquiti-unifiswitch-8-desktop-gigabit-managed-switch-us-8-60w-a1554823.html) | ~100€ |
| 4   | Ubiquiti UniFi Access Point AC Lite | [Geizhals](https://geizhals.de/ubiquiti-unifi-ap-ac-lite-uap-ac-lite-a1325765.html) | ~75€ |

Ich habe alle Komponenten für insgesamt 350€ über eBay Kleinanzeigen gebraucht gekauft. Die AVM FritzBox 7590 habe ich über den gleichen Weg für ~140€ verkauft.

### Modem 
Ursprünglich wollte ich die Fritzbox als reines Modem umkonfigurieren und weiter nutzen. Somit hätte ich es auch als Backup gehabt, falls in meinem neuen Setup mal ein Problem vorliegt. Leider lässt dies AVM nicht zu. 

Deswegen habe ich mich beim Modem für den Hersteller [DrayTek](https://www.draytek.de/modem-router.html) entschieden. Dieser wird oftmals genannt, wenn es um gute Hardware für die reine Modem-Funktionalität handelt. In älteren Artikeln ist oft vom Modell Vigor 130 die Rede. Die aktuellen Modelle sind der Vigor 166 und 167. Welches Modell man wählt, hängt vom eigenen Internetanschluss ab. In meinem Fall ist es ein Telekom VDSL Anschluss mit 100 MBit. Dafür funktionieren beide Geräte. Ich hab mich für den **DrayTek Vigor 166** entschieden, da dieser zusätzlich G-FAST unterstützt, wobei dieses wahrscheinlich in Deutschland nicht zum Einsatz kommen wird.

Die FritzBox selbst nutzt ein TAE-F auf RJ-45 Kabel. Ich musste mir zusätzlich noch ein separates Kabel bestellen, damit ich den Vigor (RJ-11 Buchse) mit meiner Telefonbuchse (TAE-F) verbinden konnte. Dieses [TAE-F auf RJ-11 Kabel](https://www.amazon.de/dp/B0BN8MXN6P?psc=1&ref=ppx_yo2ov_dt_b_product_details) lag bei meinem gebrauchten Gerät nicht bei, sollte aber eigentlich im Lieferumfang enthalten sein.

### Gateway/Router
Das Ubiquiti UniFi Security Gateway (USG) übernimmt die Funktion des Routers und der Firewall. 

Das USG wird nicht mehr hergestellt. Deshalb greifen Leute mittlerweile zum [UniFi Dream Maschine](https://geizhals.de/ubiquiti-unifi-dream-machine-udm-eu-a2176664.html) / [Pro](https://geizhals.de/ubiquiti-unifi-dream-machine-pro-rackmount-gigabit-managed-nvr-switch-udm-pro-a2227937.html). Diese beiden Modelle stellen wiederum eine All-in-One Lösung dar. Ich würde mich heute eher für eine [pfSense](https://www.pfsense.org) entscheiden und mir dafür einen Mini-PC mit Dual-NIC (2 Netzwerkanschlüsse) zulegen. Gibt's ab 200€. Hier mal ein [Thread dazu auf Reddit](https://www.reddit.com/r/homelab/comments/ycxk4a/best_mini_pc_for_pfsense/). Eigentlich will ich auch noch auf pfSense umsteigen. Gerade läuft mein System aber stabil und ich hab keine Muse. Früher oder später muss ich hier aber nochmal ran.

### Switch
Der Ubiquiti UniFi Switch 8-Port 60 Watt Power over Ehternet (US-8-60) verbindet meine kabelgebundenen Geräte im Netzwerk mit dem USG. 8 Ports erschienen mir eine solide Anschlusszahl zu sein, da ich aktuell 4 Geräte über LAN anbinde und somit noch Platz für weitere Geräte vorhanden ist:
1. Router
2. Home Server
3. TV
4. NAS

Ich habe mich für die PoE Variante entschieden, weil ich es charmant finde, dass ich somit keinen zusätzlichen Netzstecker für den WLAN Access Point benötige, der ebenfalls PoE unterstützt.

### WLAN Access Point
Der Ubiquiti Access Point AC Lite (AP AC Lite) unterstützt, wie der Name bereits verrät, die WLAN Funkstandards 802.11a/​b/​g/​n/​ac/​h (Wi-Fi 5). Heute würde ich eher den [Ubiquiti UniFi 6 Lite](https://geizhals.de/?fs=unifi+6+lite&hloc=at&hloc=de) aufgrund der Zukunftsfähigkeit mit Wi-Fi 6 kaufen. Ich habe allerdings nach wie vor keine Geräte, die Wi-Fi 6 unterstützen, und auf eBay Kleinanzeigen war der UniFi 6 Lite schlichtweg im Vergleich deutlich teurer. Der Vorteil des modularen Netzwerkaufbaus ist ja, dass ich den WLAN Access Point einfach austauschen oder um einen 2. AP erweitern kann.

<!-- 
## TODO: Netzwerktopologie
Diagramm der Netzwerktopologie 
-->
## Einrichtung

Die UniFi Software läuft auf einem [Intel NUC7i3DNKE](https://ark.intel.com/content/www/de/de/ark/products/122495/intel-nuc-kit-nuc7i3dnke.html). Diesen haben ich für 160€ auf eBay Kleinanzeigen im Dezember 2022 erstanden.

Am DrayTek Vigor Modem die Firmware flashen

## Quellen
### Artikel
1. [BSI: Smarthome sicher einrichten](https://www.bsi.bund.de/DE/Themen/Verbraucherinnen-und-Verbraucher/Informationen-und-Empfehlungen/Internet-der-Dinge-Smart-leben/Smart-Home/smart-home_node.html)
2. [Heimnetzen: Grundlagen Heimvernetzung](https://heimnetzen.de/grundlagen-heimvernetzung/)
3. [ComputerWeekly: Heim-VLANs zur Segmentierung des Netzwerkverkehrs nutzen](https://www.computerweekly.com/de/tipp/Heim-VLANs-zur-Segmentierung-des-Netzwerkverkehrs-nutzen)
4. [Administator.de: VLAN Installation und Routing mit pfSense, Mikrotik, DD-WRT oder Cisco RV Routern](https://administrator.de/tutorial/vlan-installation-und-routing-mit-pfsense-mikrotik-dd-wrt-oder-cisco-rv-routern-110259.html)
5. [The Smart Home Journey: Hardware for a professional smart home network - Next level network with Unifi equipment » The smarthome journey](https://thesmarthomejourney.com/2021/06/14/smart-home-network-unifi/)
6. [The Smart Home Journey: Securing your smarthome devices – using VLANs to secure your home network](https://thesmarthomejourney.com/2021/07/19/vlan-secure-smarthome-network/)

### Videos
1. [Home Automation Guy: Building a smart home network](https://www.youtube.com/watch?v=x4hUt45ChAI)
2. [Home Automation Guy: Advanced Smart Home Security - VLANs and Firewalls](https://youtu.be/eqr-vTC7EVk)
3. [The Hook Up: Part 2 - Ultimate Home Network 2021 - VLANs, Firewall Rules, and WiFi Networks for IoT UniFi 6.0](https://www.youtube.com/watch?v=vz3u6E3Fxi8)
4. [iDomix: DrayTek Vigor 130 als VDSL Modem einrichten Tutorial](https://www.google.de/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwipirDMi7D-AhWlxAIHHarHBxwQwqsBegQIChAF&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D6Whbg_KnumM&usg=AOvVaw2i9ud4gpOCyqnOsX4JDAHW)
5. [iDomix: Supervectoring, Vigor 165 als Modem konfigurieren](https://www.google.de/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwipirDMi7D-AhWlxAIHHarHBxwQwqsBegQICBAF&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DhMWVMd8-SYE&usg=AOvVaw2KqMCVQZOQ3FlMg4iSZZNq)
6. [iDomiX: UniFi Firewall einstellen (VLAN Isolation, Security Gateway)](https://www.youtube.com/watch?v=7zCwntwpDOw)
