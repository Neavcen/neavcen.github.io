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
Der Ubiquiti Access Point AC Lite (AP AC Lite) unterstützt, wie der Name bereits verrät, die WLAN Funkstandards 802.11a/​b/​g/​n/​ac/​h (Wi-Fi 5). Heute würde ich eher den [Ubiquiti UniFi 6 Lite](https://geizhals.de/?fs=unifi+6+lite&hloc=at&hloc=de) aufgrund der Zukunftsfähigkeit mit Wi-Fi 6 kaufen. Ich habe allerdings nach wie vor keine Geräte, die Wi-Fi 6 unterstützen, und auf eBay Kleinanzeigen war der UniFi 6 Lite schlichtweg im Vergleich deutlich teurer. Der Vorteil des modularen Netzwerkaufbaus ist ja, dass ich den WLAN Access Point einfach austauschen oder das Netzwerk um einen 2. AP erweitern kann.

<!-- 
## TODO: Netzwerktopologie
Diagramm der Netzwerktopologie 
-->
## Einrichtung

Zu Beginn müssen die Netzwerk-Komponenten miteinander verbunden werden. Als Hilfestellung bzw. Übersicht kannst du die zuvor dargestellte Netzwerktopologie heranziehen. Das Modem wird mit dem Telefonanschluss verbunden. Vom Modem führt eine Ethernet-Kabel zum UniFi USG. Das UniFi USG wird mit dem Switch verbunden. Genauso wie der UniFi AP AC Lite. Anschließend muss noch der Home Server mit Home Assistant oder der UniFi Cloud Key verbunden werden. Die restlichen Netzwerkgeräte können direkt oder später angeschlossen werden, da sie nicht für die initiale Einrichtung benötigt werden.

### UniFi Controller

Zur Einrichtung der Ubiquiti UniFi Komponenten wird die UniFi Software "UniFi Controller" benötigt. Die UniFi Software läuft bei mir als Addon namens [UniFi Network Application](https://github.com/hassio-addons/addon-unifi/blob/main/unifi/DOCS.md) auf Home Assistant OS. 

![Addon: UniFi Network Application](/assets/2023-04-18_Home Assistant_Addon_UniFi-Network-Application.png){: w="192" h="108" } 
_UniFi Addon in Home Assistant_

Home Assistant OS habe ich auf einem [Intel NUC7i3DNKE](https://ark.intel.com/content/www/de/de/ark/products/122495/intel-nuc-kit-nuc7i3dnke.html) installiert, der meinen Home Server darstellt. Im Anschluss musst du dir einen Ubiquiti Account erstellen, um dich in der Software einloggen zu können. Am besten aktivierst du dort direkt unter _My Security_ die Multifaktor-Authentifizierung (MFA) für mehr Sicherheit. Bei dem Home Assistant Addon ist zu beachten, dass man der UniFi Web UI unter _Einstellungen > System > Advanced > Inform Host_ die IP-Adresse des Home Assistant hinterlegt. Ansonsten funktioniert die Kommunikation mit den UniFi Geräten nicht.

![UniFi WebUI: Inform Host](/assets/2023-04-18_UniFI_WebUI_-_Einstellungen_System_Inform-Host.png){: w="192" h="108" } 
_UniFi WebUI Einstellung: Inform Host_

Unter _System > Administration > Remote Access_ empfehle ich die Checkbox "Allow" nicht anzuwählen. Hier gab es in der Vergangenheit eine Sicherheitslücke seitens Ubiquiti. Die Checkbox "Sync local admin with Ubiquiti SSO" kann hingegen ausgewählt werden.

Alternativ zu Home Assistant kann man auch einen Ubiquiti UniFi Cloud Key kaufen, der die UniFi Controller Software betreibt. Dies sind aber zusätzliche Kosten, die ich mit meiner Self-hosted Lösung einfach umgehen konnte. Zu dem Thema Home Assistant werde ich einen separaten Beitrag verfassen.

### Modem
Das Draytek Modem via Netzwerkkabel mit deinem Computer verbinden. Gegebenenfalls musst du das Modem noch auf Werkseinstellungen zurücksetzen. Am DrayTek Vigor Modem die neueste [Firmware](https://draytek.com/download_de/Firmwares-Modem/) flashen. Hierbei musst du sicherstellen, dass du die Firmware mit dem richtigen Modem Code (DSL-Treiber) auswählst. Für die Konfiguration haben mir zwei Videos von iDomiX sehr geholfen [[1](https://www.youtube.com/watch?v=6Whbg_KnumM), [2](https://www.youtube.com/watch?v=hMWVMd8-SYE)]. Letztlich habe ich mich doch lange mit der Konfiguration herumgequält. Deshalb hänge hier mal meine Konfiguration des DrayTek Vigor166 für meinen Telekom VDSL 100 Anschluss an. Bei Telekom muss der VLAN Tag 7 entweder im Modem oder im Router gesetzt werden. Ich habe mich für das Modem entschieden.

**DrayTek Vigor166 Konfiguration**

| ![01. Operation Mode](/assets/2023-01-24 Draytek Vigor 166 - 01 - Operation Mode.png) _01 Operation Mode_ | ![02. General Setup](/assets/2023-01-24 Draytek Vigor 166 - 02 - Internet Access - General Setup.png){: w="192" h="108"} _02 General Setup_ | ![03. Internet Access](/assets/2023-01-24 Draytek Vigor 166 - 03 - Internet Access - MPoA.png) _03 Internet Access_| ![04. LAN](/assets/2023-01-24 Draytek Vigor 166 - 04 - LAN - General Setup.png) _04 LAN General Setup_ | ![05. Online Status](/assets/2023-01-24 Draytek Vigor 166 - 05 - Online Status - Physical Connection.png) _05 Online Status_ | ![06. DSL Status](/assets/2023-01-24 Draytek Vigor 166 - 06 - Diagnostics - DSL Status.png) _06 DSL Status_ |

### Gateway/Router
Das Ubiquiti USG muss zu Beginn im UniFi Controller im Reiter _UniFi Devices_ initialisiert werden. Im Anschluss sollte es den Status "Online" haben. Gleiches kann man in diesem Zuge mit dem Switch und Access Point tun. Als nächstes solltest du die Firmware aktualisieren und automatische Updates. Veraltete Firmware kann ansonsten ein Sicherheitsrisiko darstellen.

#### Internetverbindung

Unter _Einstellungen > Internet > Primary (WAN1)_ muss nun der Port ausgewählt werden, über den das USG mit dem Modem verbunden ist. In der Regel ist das Port 1. Da die Internetverbindung mit dem Internet Service Provider mittels UniFi USG eingerichtet wird (deshalb ist das Modem mit PPPoE konfiguriert), müssen wir jetzt die Internetverbindung einrichten. Dies geht ebenfalls unter _Einstellungen > Internet_. Dort solltest du keine VLAN ID hinterlegen, wenn du dies bereits im Modem getan hast. Unter IPv4 Connection wählst du _PPPoE_ und hinterlegst _Username_ und Passwort, das dir dein ISP für die Einwahl ins Internet beim Abschluss deines DSL-Vertrags bereitgestellt hat. Ich habe unter _DNS Server > Primary Server_ die IP-Adresse des Home Assistant hinterlegt, da ich AdGuard zentral als DNS Werbeblocker in meinem Netzwerk verwende. Bei dir steht dort höchstwahrscheinlich 8.8.8.8 und das passt auch so.

![UniFi WebUI: Internetverbindung konfigurieren](/assets/2023-04-18_UniFI_WebUI_-_Einstellungne_Internet_Internetverbindung.png){: w="192" h="108" } 
_UniFi WebUI Einstellung: Internetverbindung konfigurieren_

Sind die Einstellungen korrekt, solltest du nach etwas Zeit im Reiter _Dashboard_ eine _WAN (IP)_ Adresse angezeigt bekommen. D.h. die Kommunikation mit dem ISP war erfolgreich. 

> Anmerkung: Deine öffentliche IP-Addresse solltest du aus Sicherheitsgründen niemals anderen mitteilen.
{: .prompt-warning }

#### Firewall


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
4. [iDomix: DrayTek Vigor 130 als VDSL Modem einrichten Tutorial](https://www.youtube.com/watch?v=6Whbg_KnumM)
5. [iDomix: Supervectoring, Vigor 165 als Modem konfigurieren](https://www.youtube.com/watch?v=hMWVMd8-SYE)
6. [iDomiX: UniFi Firewall einstellen (VLAN Isolation, Security Gateway)](https://www.youtube.com/watch?v=7zCwntwpDOw)
