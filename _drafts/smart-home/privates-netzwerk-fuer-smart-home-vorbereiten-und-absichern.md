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
   1. Modem
   2. Router
   3. Switch
   4. WLAN Access Point
## Entscheidungsprozess

Da ich kein professioneller Netzwerkadministrator bin, sollte es etwas sein, dass auch durch technikaffine Laien konfigurierbar und wartbar ist. Mir haben die Beiträge im [Administrator.de-Forum](www.administrator.de) sehr geholfen. Hersteller, die immer wieder genannt werden, sind beispielsweise:
* Cisco
* Mikrotik
* NetGear
* Ubiquiti
* Zyxel

Die Meinungen zur Hardware gehen stark auseinander. Letztlich habe ich mich für die Ubiquiti Unifi Serie entschieden. Die Komponenten sind bezahlbar und die Bedienung leichter als bei professioneller Hardware. Die eingeschränkteren Konfigurationsmöglichkeiten sind der Grund warum zum Teil von Unifi abgeraten wird. Die Unifi Serie gilt als Prosumer Hardware. Hier finde ich mich wieder!

## Komponenten

Wie bereits erwähnt hat die Fritzbox die Anforderungen an ein sicheres Netzwerk für Smart Home nicht erfüllen können.

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
