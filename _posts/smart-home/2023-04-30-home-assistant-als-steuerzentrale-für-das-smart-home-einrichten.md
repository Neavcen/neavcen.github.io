---
layout: post
title: Home Assistant als Steuerzentrale für das Smart Home einrichten
description: Ich führe dich Schritt-für-Schritt durch die Inbetriebnahme meines Home Servers für die Nutzung von Home Assistant inkl. dessen Installation zur Steuerung deines Smart Home mit seinen Zigbee Geräten.
image:
categories: [Smart Home]
tags: [Philips Hue,Home Server,Home Assistant,Intel NUC,Zigbee,Home Assistant SkyConnect,Zigbee2Mqtt,Smart Home]
date: 2023-04-30 23:23 +0200
---
## Anekdote
Ich hatte schon immer einen kleinen Faible für Licht und Beleuchtung. Als Jugendlicher habe ich mir LED Strips und Leuchtröhren gekauft. Ganz wichtig war, dass sie verschiedene Farben und im besten Fall noch stroboskopartige Farbverläufe unterstützen. Mittlerweile haben sich meine Präferenzen etwas verändert :sweat_smile:

## Einleitung
In 2020 musste eine neue Nachttischbeleuchtung für die eigenen vier Wände her. Gerade im Schlafzimmer ist mir wichtig, dass ich das Licht dimmen kann und morgens nicht direkt mit grellem Licht geweckt werde. Also habe ich mich etwas belesen und die [Philips Hue Iris](https://www.idealo.de/preisvergleich/OffersOfProduct/200702156_-hue-white-and-color-ambiance-iris-limited-edition-led-bluetooth-philips.html) gefunden, die zum einen ein schönes Design und zum anderen RGB unterstützt und einen Sonnenaufgang simulieren kann. Theoretisch müsste das jede Lampe über die Philips Hue App können. Ich habe mich sofort in die Funktion verliebt und so bin ich schließlich zu meiner ersten smarten Lampe gekommen. 

Über die letzten Jahre haben sich viele weitere Smart Devices angesammelt. Aber natürlich habe ich keine Lust für jeden Hersteller einen separaten Hub zu kaufen und rumstehen zu haben, der am Ende Strom und Platz braucht. Hierfür benötigte ich eine Lösung.

## Unabhängig durch Home Assistant
Ich hatte mich durch meinen initialen Kauf auf Philips Hue commited. Damit bin ich auch nach wie vor sehr glücklich, da die Lampen schlichtweg super funktionieren. Zugegebenermaßen sind sie aber nicht die Günstigsten. Zudem haben andere Hersteller ebenfalls sehr gute Geräte im Portfolio. Ich habe von einigen Arbeitskollegen gehört, dass sie die Open Source Software [Home Assistant](https://www.home-assistant.io) als Steuerzentrale für ihre Smart Home Geräte nutzen. Der große Vorteil ist, dass man herstellerunabhängig wird und nicht zig Gateways benötigt, um Geräte verschiedener Hersteller steuern zu können. Klingt reizvoll oder?

## Informationsbeschaffung
Um mich schlau zu machen, was Home Assistant eigentlich ist und kann, habe ich die [offizielle Website](https://www.home-assistant.io) und Youtube bemüht. Hier direkt mal ein paar Empfehlungen für informative Kanäle:
* [Simon42](https://www.youtube.com/@simon42)
* [Home Automation Guy](https://www.youtube.com/@HomeAutomationGuy)
* [Everything Smart Home](https://www.youtube.com/@EverythingSmartHome)

## Hardware für den Betrieb
Ich wusste sofort, dass ich auch unbedingt Home Assistant brauche! Für den Betrieb der Software benötigt man beispielsweise einen Rasperry Pi 4 oder ähnliches. Prkatisch! Ich wollte schon immer meinen eigenen kleinen Server, um ein bisschen herumzuprobieren! Simon42 hat mich davon überzeugt, dass es kein Rasperry Pi werden soll, da diese im Dezember 2022 sehr gefragt waren und ca. 125€ gekostet haben. Stattdessen fiel die Wahl auf einen gebrauchten Mini PC. Dafür habe ich eine Weile auf eBay Kleinanzeigen gelauert und schließlich einen gebrauchten [Intel NUC7i3DNKE](https://ark.intel.com/content/www/de/de/ark/products/122495/intel-nuc-kit-nuc7i3dnke.html) für 160€ ergattert. Dieser ist mit einem Intel i3 Dual-Core, 8 GB RAM und 256 GB SSD ausgestattet. Wichtig ist weiterhin, dass der Stromverbrauch möglichst gering ist, da die Hardware 24/7 laufen muss, um die Kommunikation der Geräte zu managen.

## Installation der Software
### Verfügbare Installationsvarianten
Grundsätzlich gibt es verschiedene [Varianten um Home Assistant zu installieren](https://www.home-assistant.io/installation/). Ich habe mich für das bewährte [Home Assistant Operating System](https://www.home-assistant.io/installation/generic-x86-64#install-home-assistant-operating-system) entschieden, wie von Simon42. Da die Steuerzentrale einen zentrale Position im Smart Home einnimmt, ist besonders Ausfallsicherheit bzw. Stabilität relevant. Da ich komplett neu auf dem Gebiet war, habe ich mich gegen den Betrieb als Virtuelle Maschine (VM) in VirtualBox oder Proxmoxx, genauso wie den Betrieb als Container in Docker entschieden. Heute würde ich wahrscheinlich die VM-Variante wählen, weil sie mehr Möglichkeiten bietet, den eigenen Server für noch weitere Anwendungen zu nutzen.

### Home Assistant Operating System (HAOS) installieren
Um Home Assistant als Betriebssystem zu installieren, habe ich vorab ein Ubuntu Linux mit Elena Etcher auf einen USB-Stick geflashed. Im BIOS des Intel NUC muss der USB Boot sowie UEFI Boot aktiviert und der Secure Boot deaktiviert werden. Beim Booten vom USB-Stick habe ich Ubuntu Live ausgewählt, das nicht auf die interne Festplatte geflashed werden muss. Nach dem Start des Live-Betriebssystems muss für WLAN die Internetverbindung konfiguriert werden, damit das HAOS Image heruntergeladen werden kann. Jetzt flashst du das Image auf die interne SSD. Ich hatte hierbei mir Problemen bzgl. mangelnder Schreibrechte auf der Festplatte zu kämpfen. Falls dir das passiert, bitte ich dich Google zu nutzen. Dort findest du auf alle Fälle Hilfe! Anschließend kannst du das System herunterfahren und verbindest das Ethernetkabel, falls noch nicht geschehen. 

Du kannst jetzt den Intel NUC an seinen gewünschten Platz stellen, musst noch den USB-Stick mit Ubuntu entfernen und kannst das System wieder starten. Home Assistant sollte nach kurzer Zeit gestartet sein. Ab jetzt benötigst du nur noch einen Webbrowser und verbindest dich mit dem Home Assistant über die **Default-URL: homeassistant:8123** oder alternativ die IP-Adresse des Intel NUC ergänzt um den Port 8123. Im Aschluss legst du ein Benutzerkonto an und fertig ist die Installation des Basissystems. Nun geht es an die Integrationen und Add-Ons, die Home Assistant erst so wirkungsvoll machen.

## Zigbee Hub einrichten
Damit Home Assistant die Steuerung der existierenden Zigbee Geräte übernehmen kann, benötigst du einen Zigbee USB-Dongle. Das Team um Home Assistant hat einen eigenen USB-Stick entwickelt, der ebenfalls den Matter Standard supported: [Home Assistant SkyConnect](https://www.home-assistant.io/skyconnect/). Dieser funktioniert besonders gut mit der [Integration Zigbee Home Automation (ZHA)](https://www.home-assistant.io/integrations/zha/). Alternativ werden aber auch [viele andere Zigbee USB-Dongle unterstützt](https://www.home-assistant.io/integrations/zha/#known-working-zigbee-radio-modules). Weiterhin gibt es als [Integration Zigbee2Mqtt](https://github.com/zigbee2mqtt/hassio-zigbee2mqtt#installation), was in Verbindung mit einem Mqtt-Broker (z.B. Mosquitto Mqtt Server) ebenfalls die Steuerung der Zigbee Geräte übernehmen kann.

## Zigbee Geräte einbinden
Nach der Installation können die Geräte nacheinander von ihrem bisherigen, proprietären Zigbee Hub getrennt und in Home Assistant integriert werden. Hierbei sei aber gesagt, dass ggf. coole Features der Hersteller wegfallen. Die Simulation des Sonnenaufgangs der Philips Hue Iris müsste in Home Assistant beispielsweise durch eine Automation nachgebildet werden.

## Zusammenfassung und Fazit
Home Assistant bietet eine hervorragende und kostenlose Möglichkeit das eigene Smart Home zu steuern und herstellerunabhängig zu bestücken. Dafür wird jedoch separate Hardware und etwas Muse für die Einrichtung benötigt. Läuft das System erst einmal, hast du viele Einstellungsmöglichkeiten, um dein Smart Home auf deine persönlichen Bedürfnisse auszurichten. Ich kann dir nur dringend ans Herz legen dich mit dieser tollen Open Source Software auseinanderzusetzen, um schnellstmöglich in ihren Genuss zu kommen!