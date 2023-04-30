---
layout: post
title: Komponenten für ein professionelles Heimnetzwerk auswählen
description: Ich stelle meine Komponentenauswahl zur installation eines professionellen Netzwerks vor, das bedeutend mehr Funktionen als eine gewöhnliche FRITZ!Box bietet und gleichzeitig die empfohlene Sicherheit als Vorbereitung für Smart Home mitbringt.
image:
categories: [Smart Home]
tags: [Netzwerk,Unifi,FritzBox,VLAN,Router,Gateway,Switch,Access Point, Smart Home]
date: 2023-04-20 22:20 +0200
---
## Motivation
In den letzten Jahren sind einige Smart Devices in meinem zu Hause eingezogen. Sie sind leider dafür bekannt, dass sie nicht besonders sicher sind. Dieser Umstand und mein Bruder, der mir ins Gewissen geredet hat, haben mich dazu bewegt, mein Netzwerk sicherer gegen Angriffe von außen zu machen. Schnell war klar, die AVM Fritzbox, die wohl bei den meisten im Einsatz ist, erfüllt nicht die notwendigen Anforderungen. Also musste etwas anderes her...

## Anforderungen
Im Internet findet man viele hilfreiche Seiten, die einem Tipps geben, wie man sein Netzwerk gegen Angreifer absichert. Das Bundesministerium für Sicherheit in der Informationstechnik (BSI) hat in meinen Augen einen sehr guten [Artikel](https://www.bsi.bund.de/DE/Themen/Verbraucherinnen-und-Verbraucher/Informationen-und-Empfehlungen/Internet-der-Dinge-Smart-leben/Smart-Home/smart-home_node.html) dazu verfasst. Einige weitere nützliche [Quellen](#quellen) sind am Ende des Beitrags gelistet.

Folgende **Kriterien für die Komponentenauswahl** sind mir wichtig gewesen:
1. **Firewall:** Regeln für den Netzwerkverkehr einrichten
2. **VLAN:** Separierung der Netzwerke
   1. Heimnetz für eigene, vertrauenswürdige Geräte
   2. Gästenetz für Gäste- und Arbeitsgeräte
   3. IoT-Netz für Smart Home Devices
3. **Modularität:** Separate Komponenten für die verschiedenen Funktionen
   1. Modem: Aufbau der Internetverbindung mit dem Internet Service Provider (ISP)
   2. Gateway/Router: Vergabe der IP Adressen und Routing der Verbindungen/Anfragen
   3. Switch: Verbindung von Netzwerk-Clients via LAN
   4. WLAN Access Point: Verbindung von Netzwerk-Clients via WLAN

Eine Firewall und die Möglichkeit diese nach eigenem Belieben zu konfigurieren, ist ein wichtiges Element, um den Netzwerkverkehr in seinem Heimnetzwerk zu regeln. Somit kann man sehr zielgenau Steuern, welche Kommunikation man zulassen will und welche blockiert werden soll. Die Beregelung kann beispielsweise auf IP-, Port-, oder Netzwerkebene erfolgen.

Virtuelle LANs (VLANs) dienen zur Einrichtung und Trennung verschiedener Netzwerke, die sich die gleiche physische Hardware teilen. Um dies zu erreichen, ist besondere Hardware notwendig, die VLAN-fähig ist. Die Netzwerktrennung dient ebenfalls dazu, dass Komponenten nach ihrer Vertrauenswürdigkeit gruppiert und deren Kommunikation unkompliziert gemanaged werden kann.

Die Modularität der Netzwerkkomponenten ermöglicht es, dass man später einzelne Komponenten mit ihrer spezifischen Funktion upgraden kann, ohne dass direkt das ganze System ersetzt werden muss. Dadurch können Kosten ggü. einer All-In-One Lösung gespart werden.

## Entscheidungsprozess
Wie bereits erwähnt hat meine AVM FRITZ!Box 7590 die Anforderungen an ein sicheres Netzwerk für Smart Home nicht erfüllen können. Da ich kein professioneller Netzwerkadministrator bin, sollte es etwas sein, dass auch durch technikaffine Laien konfigurierbar und wartbar ist. Mir haben die Beiträge im Forum [Administrator.de](https://administrator.de) sehr geholfen. Hersteller, die immer wieder genannt werden, sind beispielsweise:
* Cisco
* Mikrotik
* NetGear
* Ubiquiti
* Zyxel

Die Meinungen zur Hardware gehen stark auseinander. Letztlich habe ich mich für die Ubiquiti UniFi Serie entschieden. Die Komponenten sind bezahlbar und die Bedienung leichter als bei professioneller Hardware. Die Unifi Serie gilt als Prosumer Hardware. Hier finde ich mich wieder! Die eingeschränkteren Konfigurationsmöglichkeiten sind der Grund warum zum Teil von UniFi abgeraten wird.

## Komponenten
Ich war initial sehr überrascht, wie viele Rollen/Funktionen die FritzBox inne hat. Letztlich habe ich die FritzBox gegen 4 andere Komponenten ersetzt. Dabei habe ich mich für die Komponentenauswahl sehr an einem [Artikel von The Smart Home Journey](https://thesmarthomejourney.com/2021/06/14/smart-home-network-unifi/) orientiert. Entsprechend sieht die **Auswahl der Komponenten für mein professionelles Heimnetzwerk** wie folgt aus:

| #   | Funktion|     Komponente      |  Link          | Gebrauchtpreis |
| --- | --- | -------------       | :-----------:  | ----------:     |
| 1   | Modem | DrayTek Vigor166 | [Geizhals](https://geizhals.de/draytek-vigor166-v166-a-a2272803.html) | ~100€ |
| 2   | Router | Ubiquiti UniFi Security Gateway (USG) | [Geizhals](https://geizhals.de/ubiquiti-unifi-security-gateway-usg-a1213487.html) | ~75€ |
| 3   | Switch | Ubiquiti UniFi Switch (US-8-60) | [Geizhals](https://geizhals.de/ubiquiti-unifiswitch-8-desktop-gigabit-managed-switch-us-8-60w-a1554823.html) | ~100€ |
| 4   | Access Point | Ubiquiti UniFi Access Point AC Lite | [Geizhals](https://geizhals.de/ubiquiti-unifi-ap-ac-lite-uap-ac-lite-a1325765.html) | ~75€ |

Ich habe alle Komponenten für insgesamt 350€ über eBay Kleinanzeigen im Januar 2023 gebraucht gekauft. Die AVM FritzBox 7590 habe ich über den gleichen Weg für ~140€ verkauft.

### Modem 
Ursprünglich wollte ich die FritzBox als reines Modem umkonfigurieren und weiter nutzen. Somit hätte ich sie auch als Backup gehabt, falls in meinem neuen Setup mal ein Problem auftritt. Leider lässt AVM den sogenannten Bridge-Mode nicht zu. 

Deswegen habe ich mich für ein separates Modem und den Hersteller [DrayTek](https://www.draytek.de/modem-router.html) entschieden. Dieser wird oftmals genannt, wenn es um gute Hardware für die reine Modem-Funktionalität geht. In älteren Artikeln ist oft vom Modell Vigor 130 die Rede. Die aktuellen Modelle sind der Vigor 166 und 167. Welches Modell man wählt, hängt vom eigenen Internetanschluss ab. In meinem Fall ist es ein Telekom VDSL Anschluss mit 100 MBit. Dafür funktionieren beide Geräte. Ich hab mich für den **DrayTek Vigor 166** entschieden, da dieser zusätzlich G-FAST unterstützt, wobei dieses wahrscheinlich in Deutschland nicht zum Einsatz kommen wird.

Die FritzBox selbst nutzt ein TAE-F auf RJ-45 Kabel. Ich musste mir zusätzlich noch ein separates Kabel bestellen, damit ich den Vigor (RJ-11 Buchse) mit meiner Telefonbuchse (TAE-F) verbinden konnte. Dieses [TAE-F auf RJ-11 Kabel](https://www.amazon.de/dp/B0BN8MXN6P?psc=1&ref=ppx_yo2ov_dt_b_product_details) lag bei meinem gebrauchten Gerät nicht bei, sollte aber eigentlich im Lieferumfang enthalten sein.

### Gateway/Router
Das Ubiquiti UniFi Security Gateway (USG) übernimmt die Funktion des Routers und der Firewall. 

Das USG wird nicht mehr hergestellt. Deshalb greifen Leute mittlerweile zum [UniFi Dream Maschine](https://geizhals.de/ubiquiti-unifi-dream-machine-udm-eu-a2176664.html) / [Pro](https://geizhals.de/ubiquiti-unifi-dream-machine-pro-rackmount-gigabit-managed-nvr-switch-udm-pro-a2227937.html). Diese beiden Modelle stellen wiederum eine All-in-One Lösung dar. Ich würde mich heute eher für eine [pfSense](https://www.pfsense.org) entscheiden und mir dafür einen Mini-PC mit Dual-NIC (2 Netzwerkanschlüsse) zulegen. Gibt's ab 200€. Hier mal ein [Thread dazu auf Reddit](https://www.reddit.com/r/homelab/comments/ycxk4a/best_mini_pc_for_pfsense/). Eigentlich will ich auch noch auf pfSense umsteigen. Gerade läuft mein System aber stabil und ich hab keine Muse. Früher oder später muss ich hier aber nochmal ran.

### Switch
Der Ubiquiti UniFi Switch 8-Port mit 60 Watt Power over Ehternet (US-8-60) verbindet meine kabelgebundenen Geräte im Netzwerk mit dem USG. 8 Ports erschienen mir eine solide Anschlusszahl zu sein, da ich aktuell 4 **Geräte über LAN angebunden** habe und somit noch Platz für weitere Geräte vorhanden ist:
1. Router
2. Home Server
3. TV
4. NAS

Ich habe mich für die PoE Variante entschieden, weil ich es charmant finde, dass ich somit keinen zusätzlichen Netzstecker für den WLAN Access Point benötige, der ebenfalls PoE unterstützt.

Das charmante an UniFi ist, dass man alle Geräte zentral über die UniFi Controller Software verwalten kann. Zudem rechne ich mit höherer Kompatibilität und weniger Fehlern durch die Wahl eines einzigen Herstellers. Ist dir dies nicht so wichtig, kannst du auch für deutlich weniger Geld beispielsweise den [Netgear ProSAFE Plus GS100](https://geizhals.de/netgear-prosafe-plus-gs100-desktop-gigabit-smart-switch-gs108e-300-a1168564.html) kaufen. Dieser ist ebenfalls VLAN-fähig.

### WLAN Access Point
Die Ubiquite WLAN Access Points sind für ihre sehr gute Leistung bekannt und werden häufig empfohlen. Das Modell AP AC Lite unterstützt, wie der Name bereits verrät, die WLAN Funkstandards 802.11a/​b/​g/​n/​ac/​h (Wi-Fi 5). Zukünftig würde ich eher den [Ubiquiti UniFi 6 Lite](https://geizhals.de/?fs=unifi+6+lite&hloc=at&hloc=de) aufgrund der Zukunftsfähigkeit mit Wi-Fi 6 kaufen. Ich habe allerdings nach wie vor keine Geräte, die Wi-Fi 6 unterstützen, und auf eBay Kleinanzeigen war der UniFi 6 Lite schlichtweg im Vergleich deutlich teurer. 

Ein Vorteil des modularen Netzwerkaufbaus ist ja, dass ich den WLAN Access Point später einfach austauschen oder das Netzwerk um einen 2. AP erweitern kann.

## Ausblick
Die Komponenten für das professionelle Heimnetzwerk sind jetzt zusammengestellt. Nun geht es ans Eingemachte, nämlich die Konfiguration des Netzwerks. Diese folgt im nächsten Beitrag.

## Quellen
### Artikel
1. [BSI: Smarthome sicher einrichten](https://www.bsi.bund.de/DE/Themen/Verbraucherinnen-und-Verbraucher/Informationen-und-Empfehlungen/Internet-der-Dinge-Smart-leben/Smart-Home/smart-home_node.html)
2. [Heimnetzen: Grundlagen Heimvernetzung](https://heimnetzen.de/grundlagen-heimvernetzung/)
3. [ComputerWeekly: Heim-VLANs zur Segmentierung des Netzwerkverkehrs nutzen](https://www.computerweekly.com/de/tipp/Heim-VLANs-zur-Segmentierung-des-Netzwerkverkehrs-nutzen)
4. [The Smart Home Journey: Hardware for a professional smart home network - Next level network with Unifi equipment » The smarthome journey](https://thesmarthomejourney.com/2021/06/14/smart-home-network-unifi/)

### Videos
1. [Home Automation Guy: Building a smart home network](https://www.youtube.com/watch?v=x4hUt45ChAI)
2. [The Hook Up: Part 1 - Ultimate Home Network 2021 - WiFi 6 and UniFi Dream Machine Pro](https://www.youtube.com/watch?v=ufJ3dPAgFiM)
