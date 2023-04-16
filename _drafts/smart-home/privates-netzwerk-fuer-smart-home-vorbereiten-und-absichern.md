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
   2. Router: Vergabe der IP Adressen und Routing der Verbindungen/Anfragen
   3. Switch: Verbindung von Netzwerk-Clients via LAN
   4. WLAN Access Point: Verbindung von Netzwerk-Clients via WLAN
## Entscheidungsprozess

Wie bereits erwähnt hat die Fritzbox die Anforderungen an ein sicheres Netzwerk für Smart Home nicht erfüllen können. Da ich kein professioneller Netzwerkadministrator bin, sollte es etwas sein, dass auch durch technikaffine Laien konfigurierbar und wartbar ist. Mir haben die Beiträge im [Administrator.de-Forum](www.administrator.de) sehr geholfen. Hersteller, die immer wieder genannt werden, sind beispielsweise:
* Cisco
* Mikrotik
* NetGear
* Ubiquiti
* Zyxel

Die Meinungen zur Hardware gehen stark auseinander. Letztlich habe ich mich für die Ubiquiti Unifi Serie entschieden. Die Komponenten sind bezahlbar und die Bedienung leichter als bei professioneller Hardware. Die eingeschränkteren Konfigurationsmöglichkeiten sind der Grund warum zum Teil von Unifi abgeraten wird. Die Unifi Serie gilt als Prosumer Hardware. Hier finde ich mich wieder!

## Komponenten

Ich habe mich bei der Komponentenauswahl sehr an einem [Artikel von The Smart Home Journey](https://thesmarthomejourney.com/2021/06/14/smart-home-network-unifi/) orientiert. Entsprechend sieht meine Auswahl wie folgt aus:

* [Ubiquiti UniFi Security Gateway (USG)](https://geizhals.de/ubiquiti-unifi-security-gateway-usg-a1213487.html) => ~75€
* [Ubiquiti UniFi Switch (US-8-60)](https://geizhals.de/ubiquiti-unifiswitch-8-desktop-gigabit-managed-switch-us-8-60w-a1554823.html) => ~100€
* [Ubiquiti UniFi Access Point AC Lite](https://geizhals.de/ubiquiti-unifi-ap-ac-lite-uap-ac-lite-a1325765.html) => ~75€
* [DrayTek Vigor166](https://geizhals.de/draytek-vigor166-v166-a-a2272803.html) => ~100€

Ich habe alle Komponenten über eBay Kleinanzeigen gebraucht für insgesamt 350€ gekauft. Die FritzBox 7590 habe ich über den gleichen Weg für ~140€ verkauft.

**Anmerkung zum Router:**
Das UniFi USG wird mittlerweile nicht mehr hergestellt. Deshalb greifen Leute mittlerweile zum [UniFi Dream Maschine](https://geizhals.de/ubiquiti-unifi-dream-machine-udm-eu-a2176664.html) / [Pro](https://geizhals.de/ubiquiti-unifi-dream-machine-pro-rackmount-gigabit-managed-nvr-switch-udm-pro-a2227937.html). Diese stellen wiederum eine All-in-One Lösung dar. Ich würde mich heute allerdings eher für eine [pfSense](https://www.pfsense.org) entscheiden und mir dafür einen Mini-PC mit Dual-NIC (2 Netzwerkanschlüsse) zulegen. Gibt's ab 200€. Hier mal ein [Thread dazu auf Reddit](https://www.reddit.com/r/homelab/comments/ycxk4a/best_mini_pc_for_pfsense/). Eigentlich will ich auch noch auf pfSense umsteigen. Gerade läuft mein System aber gut und ich bin gerade nicht bereit nochmal Geld auszugeben und einen zweiten Mini-PC aufzusetzen.

**Anmerkung zum WLAN Access Point:**
Heute würde ich eher den [Ubiquiti UniFi 6 Lite](https://geizhals.de/?fs=unifi+6+lite&hloc=at&hloc=de) aufgrund der Zukunftsfähigkeit kaufen. Ich habe allerdings nach wie vor keine Wifi6-fähigen Geräte und auf eBay Kleinanzeigen gab es diese schlichtweg nicht als ich gesucht habe oder waren im Vergleich deutlich teurer.

## Einrichtung

Die UniFi Software läuft auf einem [Intel NUC7i3DNKE](https://ark.intel.com/content/www/de/de/ark/products/122495/intel-nuc-kit-nuc7i3dnke.html). Diesen haben ich für 160€ auf eBay Kleinanzeigen im Dezember 2022 erstanden.

## Quellen [#quellen]
### Artikel
1. [BSI: Smarthome sicher einrichten](https://www.bsi.bund.de/DE/Themen/Verbraucherinnen-und-Verbraucher/Informationen-und-Empfehlungen/Internet-der-Dinge-Smart-leben/Smart-Home/smart-home_node.html)
2. [Heimnetzen: Grundlagen Heimvernetzung](https://heimnetzen.de/grundlagen-heimvernetzung/)
3. [ComputerWeekly: Heim-VLANs zur Segmentierung des Netzwerkverkehrs nutzen](https://www.computerweekly.com/de/tipp/Heim-VLANs-zur-Segmentierung-des-Netzwerkverkehrs-nutzen)
4. [Administator.de: VLAN Installation und Routing mit pfSense, Mikrotik, DD-WRT oder Cisco RV Routern](https://administrator.de/tutorial/vlan-installation-und-routing-mit-pfsense-mikrotik-dd-wrt-oder-cisco-rv-routern-110259.html)
5. [The Smart Home Journey: Hardware for a professional smart home network - Next level network with Unifi equipment » The smarthome journey](https://thesmarthomejourney.com/2021/06/14/smart-home-network-unifi/)
6. [The Smart Home Journey: Securing your smarthome devices – using VLANs to secure your home network](https://thesmarthomejourney.com/2021/07/19/vlan-secure-smarthome-network/)

### Videos
1. [Home Automation Guy: Advanced Smart Home Security - VLANs and Firewalls](https://youtu.be/eqr-vTC7EVk)
2. [The Hook Up: Part 2 - Ultimate Home Network 2021 - VLANs, Firewall Rules, and WiFi Networks for IoT UniFi 6.0](https://www.youtube.com/watch?v=vz3u6E3Fxi8)
3. [iDomiX: UniFi Firewall einstellen (VLAN Isolation, Security Gateway)](https://www.youtube.com/watch?v=7zCwntwpDOw)
