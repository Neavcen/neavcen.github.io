---
layout: post
title: Komponenten für ein professionelles Heimnetzwerk in Betrieb nehmen
description: Ich führe dich Schritt für Schritt durch die Inbetriebnahme meines professionellen Netzwerks, das bedeutend mehr Funktionen als eine gewöhnliche FRITZ!Box bietet und gleichzeitig die empfohlene Sicherheit für Smart Home mitbringt.
image:
categories: [Smart Home]
tags: [Netzwerk,Unifi,VLAN,Router,Gateway,Firewall,Switch,Access Point,Smart Home]
date: 2023-04-29 00:43 +0200
---
## Motivation
Die Verwendung von Smart Home Geräten im eigenen Heimnetz stellt eine potenzielle Sicherheitslücke dar. Diese Geräte sind nicht unbedingt für ihre Sicherheit bekannt. Schnell war klar, die AVM Fritzbox, die wohl bei den meisten im Einsatz ist, erfüllt nicht die notwendigen Anforderungen. Also musste etwas anderes her... Die Komponentenauswahl habe ich bereits im Beitrag [Komponenten für ein professionelles Heimnetzwerk auswählen]({% post_url smart-home/2023-04-20-komponenten-fuer-ein-professionelles-heimnetzwerk-auswaehlen %}) näher erläutert. Hier folgt nun die Inbetriebnahme und Konfiguration eben dieser Hardware.

## Einrichtung
Bevor die einzelnen Komponenten konfiguriert werden können, müssen diese ans Netz genommen und eine Verbindung untereinander hergestellt werden. Nimm dir Zeit für die Einrichtung. Ich hab bestimmt 3 Trockenläufe gehabt, bevor ich mich wirklich entschlossen habe, alle Geräte auf das neue Netzwerk umzuziehen. 

Es macht absolut keinen Spaß unter Zeitdruck zu arbeiten, weil jemand anders auf die Internetverbindung angewiesen ist. Bevor du die Internetverbindung deines bestehenden Routers trennst, gehe sicher, dass alle Komponenten deines neuen Netzwerks richtig verkabelt und konfiguriert sind. Du wirst bestimmt zwischendurch etwas Googeln wollen. 

> Die DSL-Verbindung deines bestehenden System würde ich erst trennen, wenn Modem, Router, Switch und WLAN Access Point korrekt miteinander kommunizieren. Alternativ solltest du schnell in der Lage sein wieder eine Internetverbindung über dein Bestandssystem herzustellen. Baue dieses keinesfalls vorher ab. Ich habe die Einrichtung spät abends gemacht, als meine Partnerin bereits geschlafen und die fehlende Internetverbindung nicht bemerkt hat.
{: .prompt-tip }

Im nachfolgenden Abschnitt gehe ich zunächst auf die Netzwerktopologie ein. Diese gibt dir eine gute Übersicht, wie die einzelnen Komponenten miteinander verbunden werden.

### Netzwerktopologie
Das Modem wird mit dem DSL-Telefonanschluss verbunden. Vom Modem (DrayTek Vigor166) führt ein Ethernet-Kabel zum Router (UniFi USG). Der Router wird mit dem Switch (UniFi US-8-60) verbunden. Genauso wie der WLAN Access Point (UniFi AP AC Lite). Anschließend muss noch der Home Server mit Home Assistant oder der UniFi Cloud Key verbunden werden. Die restlichen Netzwerkgeräte können direkt oder später angeschlossen werden, da sie nicht für die initiale Einrichtung benötigt werden.

![Topologie meines Netzwerks](/assets/smart-home/Netzwerktopologie.drawio.svg){: w="300" } 
_Topologie meines Netzwerks_

### Modem
Um das Draytek Modem konfigurieren zu können, musst du dieses via Ethernetkabel mit deinem Computer verbinden. Du benötigst also ein Notebook oder ähnliches mit einem LAN-Anschluss. Gegebenenfalls musst du das Modem noch auf Werkseinstellungen zurücksetzen. 

Nachdem du dich erfolgreich mit dem DrayTek Vigor verbunden hast, solltest du zuerst einmal die neueste [Firmware](https://draytek.com/download_de/Firmwares-Modem/) flashen. Hierbei musst du sicherstellen, dass du die Firmware mit dem richtigen Modem Code (DSL-Treiber) auswählst. 

Für die Konfiguration haben mir zwei Videos von iDomiX sehr geholfen [[1](https://www.youtube.com/watch?v=6Whbg_KnumM), [2](https://www.youtube.com/watch?v=hMWVMd8-SYE)]. Letztlich habe ich mich doch lange mit der Konfiguration herumgequält. Deshalb hänge ich hier mal meine Konfiguration des DrayTek Vigor166 für meinen Telekom VDSL 100 Anschluss an. Bei Telekom muss der VLAN Tag 7 entweder im Modem oder im Router gesetzt werden. Ich habe mich für das Modem entschieden.

**DrayTek Vigor166 Konfiguration**

| ![01. Operation Mode](/assets/smart-home/2023-01-24 Draytek Vigor 166 - 01 - Operation Mode.png){: w="150" } _01 Operation Mode_ | ![02. General Setup](/assets/smart-home/2023-01-24 Draytek Vigor 166 - 02 - Internet Access - General Setup.png){: w="150" } _02 General Setup_ | ![03. Internet Access](/assets/smart-home/2023-01-24 Draytek Vigor 166 - 03 - Internet Access - MPoA.png){: w="150" } _03 Internet Access_| ![04. LAN](/assets/smart-home/2023-01-24 Draytek Vigor 166 - 04 - LAN - General Setup.png){: w="150" } _04 LAN General Setup_ | ![05. Online Status](/assets/smart-home/2023-01-24 Draytek Vigor 166 - 05 - Online Status - Physical Connection.png){: w="150" } _05 Online Status_ | ![06. DSL Status](/assets/smart-home/2023-01-24 Draytek Vigor 166 - 06 - Diagnostics - DSL Status.png){: w="150" } _06 DSL Status_ |

### UniFi Controller
Zur Einrichtung der Ubiquiti UniFi Komponenten wird die UniFi Software "UniFi Controller" benötigt. Die UniFi Software läuft bei mir als Addon namens [UniFi Network Application](https://github.com/hassio-addons/addon-unifi/blob/main/unifi/DOCS.md) auf Home Assistant OS. 

![Addon: UniFi Network Application](/assets/smart-home/2023-04-18_Home Assistant_-_Addon_UniFi-Network-Application.png){: w="300" } 
_UniFi Controller Addon in Home Assistant_

Home Assistant OS habe ich auf einem [Intel NUC7i3DNKE](https://ark.intel.com/content/www/de/de/ark/products/122495/intel-nuc-kit-nuc7i3dnke.html) installiert, der meinen Home Server darstellt. Im Anschluss musst du dir einen Ubiquiti Account erstellen, um dich in der Software einloggen zu können. Am besten aktivierst du dort direkt unter _My Security_ die Multifaktor-Authentifizierung (MFA) für mehr Sicherheit. Bei dem Home Assistant Addon ist zu beachten, dass man der UniFi Web UI unter _Einstellungen > System > Advanced > Inform Host_ die IP-Adresse des Home Assistant hinterlegt. Ansonsten funktioniert die Kommunikation mit den UniFi Geräten nicht.

![UniFi Controller: Inform Host](/assets/smart-home/2023-04-18_UniFI_Controller_-_Einstellungen_System_Inform-Host.png){: w="300" } 
_UniFi Controller: Inform Host_

Unter _System > Administration > Remote Access_ empfehle ich die Checkbox "Allow" nicht anzuwählen. Hier gab es in der Vergangenheit eine Sicherheitslücke seitens Ubiquiti. Die Checkbox "Sync local admin with Ubiquiti SSO" kann hingegen ausgewählt werden.

Alternativ zu Home Assistant kann man auch einen Ubiquiti UniFi Cloud Key kaufen, der die UniFi Controller Software betreibt. Dies sind aber zusätzliche Kosten, die ich mit meiner Self-hosted Lösung einfach umgehen konnte. Zu dem Thema Home Assistant werde ich einen separaten Beitrag verfassen.

### Gateway/Router
Das Ubiquiti USG Gateway muss zu Beginn im UniFi Controller im Reiter _UniFi Devices_ initialisiert werden. Im Anschluss sollte es den Status "Online" haben. Gleiches kann man in diesem Zuge mit dem Switch und Access Point tun. Als nächstes solltest du die Firmware aktualisieren und automatische Updates. Veraltete Firmware kann ansonsten ein Sicherheitsrisiko darstellen.

![UniFi Controller: UniFi Devices](/assets/smart-home/2023-04-28_UniFi_Controller_-_Devices.png){: w="300" } 
_UniFi Controller: Übersicht der angeschlossenen UniFi Geräte_

### Virtuelle Netzwerke (VLAN)
Nachdem die UniFi Geräte initialisiert wurden und miteinander kommunizieren können, sollten zuerst die verschiedenen virtuellen Netzwerke angelegt werden. Dafür wechsle auf den Reiter _Einstellungen > Networks_. Dort hinterlegst du einen Namen, wählst das USG als Router aus und kannst, bei Bedarf, eine eigene Subnetzmaske für die Nutzung eines dedizierten IP-Bereichs definieren.

Hier sind zwei Beispiele aus meiner VLAN-Konfiguration:

| ![VLAN: LAN](/assets/smart-home/2023-04-28_UniFi_Controller_-_Einstellungen_Netzwerk_VLAN-LAN.png){: w="300" } _VLAN: LAN_ | ![VLAN: Guest+Work](/assets/smart-home/2023-04-28_UniFi_Controller_-_Einstellungen_Netzwerk_VLAN-Guest.png){: w="300" } _VLAN: Guest+Work_ |

Insgesamt habe ich vier VLANs angelegt:
1. **WAN: Exklusiv für Router/Gateway** - Nur aufgrunddessen angelegt, dass ich jedes Mal die Verbindung  zwischen USG und UniFi Controller verloren habe, wenn ich das USG und den Home Assistant in den 10er Netzwerkadressbereich umziehen wollte.
2. **LAN: Eigene, vertrauenswürdige Geräte** - In erster Linie Notebooks, Tablets und Smartphones der Haushaltsangehörigen. 
3. **Guest+Work: Gäste- oder Arbeitsgeräte** - Nur externe Geräte untergebracht. Dieses ist explizit als Gastnetzwerk eingerichtet, wodurch die Geräte untereinander nicht kommunizieren dürfen.
4. **IoT: Smart Devices bzw. nicht vertrauenswürdige Geräte** - Sprich alle Smart Devices, wo nicht genau klar ist, ob diese evtl. gesammelte Daten an Ihren Hersteller senden oder deren Sicherheitsfeatures fraglich sind. Hierzu zählen bspw. Smart TVs, Lautsprecher, WLAN-Steckdosen, etc.

### Managed Switch
Beim Ubiquiti US-8-60 Switch müssen primär die Netzwerkprofile für die einzelnen Ethernet Ports definiert werden. Das Profil definiert, welcher Netzwerkverkehr an den Port weitergeleitet wird. Dafür gehst du in die Einstellungen des Switches über _UniFi Devices > Switch > Ports > Port Manager_ und wählst pro Port welches Netzwerkprofil angewandt werden soll. 

Für den Port, an dem das Gateway hängt, muss unbedingt das Profil "All" gewählt werden, damit dieses mit mehreren bzw. allen VLANs sowie deren Geräten kommunizieren kann. Gleiches gilt für den WLAN Access Point als auch den Home Server. Hingegen wird dem Port des Smart TVs das Profil "IoT" oder dem NAS das Profil "LAN" zugeordnet. Somit können diese nur mit Geräten aus ihrem Netz kommunizieren. Zumindest sofern eine Kommunikation der Netzwerkteilnehmer untereinander gestattet ist.

### WLAN Access Point
Der Ubiquiti AP AC Lite WLAN Access Point unterstützt die Ausstrahlung von bis zu 3 verschiedenen SSIDs. D.h. man kann WLAN-Konnektivität für drei verschiedene Netzwerke über einen WLAN Access Point herstellen. Dazu musst du lediglich den Namen des WLANs, ein Passwort und die Zuordnung eines VLANs festlegen. Hast du mehrere WLAN Access Points kannst du zudem auswählen, welche SSID von welchem AP bereitgestellt wird. 

Ich habe im Reiter _Einstellungen > WiFi_ die **SSIDs für folgende VLANs eingerichtet**:
* LAN
* Guest+Work
* IoT

Somit kann ich analog zu meinem managed Switch steuern, mit welchem VLAN sich die WLAN Geräte verbinden und später mit Hilfe der Firewall definieren, mit welchen anderen Netzwerkteilnehmern sie kommunizieren dürfen.

### Internetverbindung
Für die Herstellung der Internetverbindung muss unter _Einstellungen > Internet > Primary (WAN1)_ der Port ausgewählt werden, über den das USG mit dem Modem verbunden ist. In der Regel ist das Port 1. Da die Internetverbindung mit dem Internet Service Provider mittels UniFi USG eingerichtet wird (deshalb ist das Modem mit PPPoE konfiguriert), müssen wir dort die Internetverbindung einrichten. 

Dies geht ebenfalls unter _Einstellungen > Internet_. Dort solltest du keine VLAN ID hinterlegen, wenn du dies bereits im Modem getan hast. Unter IPv4 Connection wählst du _PPPoE_ und hinterlegst _Username_ und Passwort, das dir dein ISP für die Einwahl ins Internet beim Abschluss deines DSL-Vertrags bereitgestellt hat. 

Ich habe unter _DNS Server > Primary Server_ die IP-Adresse des Home Assistant hinterlegt, da ich AdGuard zentral als DNS Werbeblocker in meinem Netzwerk verwende. Bei dir steht dort höchstwahrscheinlich 8.8.8.8 und das passt auch so.

![UniFi Controller: Internetverbindung konfigurieren](/assets/smart-home/2023-04-18_UniFi_Controller_-_Einstellungen_Internet_Internetverbindung.png){: w="300" } 
_UniFi Controller: Internetverbindung konfigurieren_

Sind die Einstellungen korrekt, solltest du nach etwas Zeit im Reiter _Dashboard_ eine _WAN (IP)_ Adresse angezeigt bekommen. D.h. die Kommunikation mit dem ISP war erfolgreich. Wenn die Internetverbindung steht, ist das Essenziellste geschafft! Niemand will nämlich von seinem Partner oder seiner Partnerin angepöbelt werden, weil Netflix nicht erreichbar ist :sweat_smile:

> Anmerkung: Deine öffentliche IP-Addresse solltest du aus Sicherheitsgründen niemals anderen mitteilen.
{: .prompt-warning }

### Firewall und Firewall-Regeln
Die Firewall ist das Herzstück des neuen Netzwerkaufbaus. Hierüber wird gesteuert, welche Kommunikation innerhalb eines Netzwerks bzw. über mehrere Netzwerke hinweg erlaubt oder verboten ist. Werden bestimmte im Vorfeld definierte Sicherheitsregeln verletzt, filtert bzw. blockiert die Firewall die Kommunikationsdaten, die zwischen zwei Netzwerken hin und hergeschickt wurden. 

Generell arbeitet einen Firewall folgendermaßen: Die Regeln werden für jedes Paket der Reihe nach geprüft, und die erste zutreffende Regel wird angewendet. Die Reihenfolge der Regeln ist daher relevant. 

Die **Zusammensetzung einer Firewall-Regel** besteht meist aus sechs Komponenten:
1. Absender-IP-Adresse
2. Ziel-IP-Adresse
3. Netzwerkprotokoll (TCP, UDP, ICMP, …)
4. Port-Nummer (bei TCP und UDP)
5. Aktion (erlauben, verwerfen oder ablehnen)

Nachfolgend findest du ein Beispiel für eine Firewall-Regel, die die Initiierung der Kommunikation von IoT-Geräten zu Geräten im LAN-Netzwerk unterbindet.

![UniFi Controller: Firewall-Regel - Beispiel](/assets/smart-home/2023-04-28_UniFi_Controller_-_Einstellungen_Firewall_Regel_Beispiel.png){: w="300" } 
_UniFi Controller: Firewall-Regeln - Beispiel_

Ich habe mich bei der Definition der Firewall-Regeln an den Video-Tutorials von [Home Automation Guy](https://youtu.be/eqr-vTC7EVk), [The Hook Up](https://www.youtube.com/watch?v=vz3u6E3Fxi8) und [iDomiX](https://www.youtube.com/watch?v=7zCwntwpDOw) orientiert.

Grundsätzlich sollen folgende **Ziele mit den Firewall-Regeln** erreicht werden:
1. **Eigene, sichere Geräte (VLAN: LAN)**
   1. dürfen auf die IoT-Geräte zugegreifen bzw. die Kommunikation initiieren, aber nicht umgekehrt (z.B. Song auf Smart Speaker abspielen).
   2. haben Zugriff auf das Internet.
2. **Gast- und Arbeitsgeräte (VLAN: "Guest+Work")**
   1. können nicht mit den Geräten der anderen VLANs kommunizieren und auch nicht untereinander.
   2. haben Zugriff auf das Internet.
3. **IoT-Geräte (VLAN: "IoT")**
   1. dürfen bei einer bereits aufgebauten Verbindung durch sichere Geräte antworten.
   2. können eine Verbindung zum Home Server aufbauen.
   3. haben Zugriff auf das Internet (Smart TV, Smart Speaker). 
   Sofern man Smart Devices besitzt, die nicht zwingend Internetzugriff benötigen (z.B. WLAN Steckdosen), kann es sinnvoll sein, diese in ein eigenes VLAN zu verschieben und den Internetzugriff zu sperren.

Meine Liste der Firewall-Regeln für den Bereich "LAN In" sieht im UniFi Security Gateway wie folgt aus:

![UniFi Controller: Firewall-Regeln - LAN In](/assets/smart-home/2023-04-28_UniFi_Controller_-_Einstellungen_Firewall_Regel-LAN-Uebersicht.png){: w="300" }
_UniFi Controller: Firewall-Regeln - LAN In_

## Zusammenfassung und Fazit
Puh, endlich geschafft! Wie du höchstwahrscheinlich festgestellt hast, ist einiges an Aufwand nötig, um die vielen Netzwerkkomponenten miteinander zu verbinden und richtig einzurichten. Dagegen ist im Vergleich eine FritzBox wirklich schnell und einfach in Betrieb genommen.

Die großen Vorteil des neuen Setups sind die Möglichkeit zur Aufteilung der Netzwerkteilnehmer in verschiedene virtuelle Netzwerke (VLANs) und die konfigurierbare Firewall, durch die man die Kommunikation in und zwischen den Netzwerken selbst beregeln kann.

Ich bin sehr zufrieden mit dem Ergebnis! Gib's zu, du bist auch ein wenig stolz auf dich! Jetzt können wir uns eine ganze Ecke sicherer fühlen und uns voll auf den Ausbau unseres Smart Home konzentrieren :sunglasses:

## Quellen
### Artikel
1. [BSI: Smarthome sicher einrichten](https://www.bsi.bund.de/DE/Themen/Verbraucherinnen-und-Verbraucher/Informationen-und-Empfehlungen/Internet-der-Dinge-Smart-leben/Smart-Home/smart-home_node.html)
2. [Heimnetzen: Grundlagen Heimvernetzung](https://heimnetzen.de/grundlagen-heimvernetzung/)
3. [ComputerWeekly: Heim-VLANs zur Segmentierung des Netzwerkverkehrs nutzen](https://www.computerweekly.com/de/tipp/Heim-VLANs-zur-Segmentierung-des-Netzwerkverkehrs-nutzen)
4. [Administator.de: VLAN Installation und Routing mit pfSense, Mikrotik, DD-WRT oder Cisco RV Routern](https://administrator.de/tutorial/vlan-installation-und-routing-mit-pfsense-mikrotik-dd-wrt-oder-cisco-rv-routern-110259.html)
5. [The Smart Home Journey: Securing your smarthome devices – using VLANs to secure your home network](https://thesmarthomejourney.com/2021/07/19/vlan-secure-smarthome-network/)

### Videos
1. [Home Automation Guy: Advanced Smart Home Security - VLANs and Firewalls](https://youtu.be/eqr-vTC7EVk)
2. [The Hook Up: Part 2 - Ultimate Home Network 2021 - VLANs, Firewall Rules, and WiFi Networks for IoT UniFi 6.0](https://www.youtube.com/watch?v=vz3u6E3Fxi8)
3. [iDomix: DrayTek Vigor 130 als VDSL Modem einrichten Tutorial](https://www.youtube.com/watch?v=6Whbg_KnumM)
4. [iDomix: Supervectoring, Vigor 165 als Modem konfigurieren](https://www.youtube.com/watch?v=hMWVMd8-SYE)
5. [iDomiX: UniFi Firewall einstellen (VLAN Isolation, Security Gateway)](https://www.youtube.com/watch?v=7zCwntwpDOw)
