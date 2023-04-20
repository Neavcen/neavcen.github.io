---
layout: post
title: Professionelles Heimnetzwerk mit Smart Home einrichten
description:
image:
categories: [Smart Home]
tags: [Netzwerk,Unifi,VLAN,Router,Gateway,Firewall,Switch,Access Point]
---
## Motivation
In den letzten Jahren haben einige Smart Devices in meinem zu Hause eingezogen. Sie sind leider dafür bekannt, dass sie nicht besonders sicher sind. Dieser Umstand und mein Bruder, der mir ins Gewissen geredet hat, haben mich dazu bewegt, mein Netzwerk sicherer gegen Angriffe von außen zu machen. Schnell war klar, die AVM Fritzbox, die wohl bei den meisten im Einsatz ist, erfüllt nicht die notwendigen Anforderungen. Also musste etwas anderes her...

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
