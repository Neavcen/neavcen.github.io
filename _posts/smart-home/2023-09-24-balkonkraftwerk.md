---
layout: post
title: Alles, was du zum Thema Balkonkraftwerk wissen musst
description: Ich beschäftige mich mit folgenden Fragen... Was ist ein Balkonkraftwerk?
  Aus welchen Komponenten besteht es? Was gibt es zu beachten? Kann auch ich ein Balkonkraftwerk
  betreiben?
image:
categories:
- Smart Home
tags:
- Balkonkraftwerk
- Photovoltaik
- Smart Home
date: 2023-09-24 18:27 +0200
---
## Motivation
Durch meine Faszination für Smart Home Komponenten bin ich zwangsläufig am Thema Balkonkraftwerk vorbeigekommen. Da ich Home Assistant einsetze, möchte ich natürlich auch die schöne Visualisierung für Einspeisung und Verbräuche nutzen.

Da ich zeitnah mein erstes Eigenheim beziehen werde, bietet mir ein Balkonkraftwerk die Möglichkeit mich mit geringer Investition in das Thema Photovoltaik einzufühlen. Die geringen Anschaffungskosten und die kurze Amortisationszeit machen die Investition zu einem No-Brainer.

Im Internet gibt es eine große Auswahl an verfügbaren Komplettsets. Aber auch bei den Komplettsets gilt, nicht jede angebotene Kombition ist wirklich eine gute Wahl.

Bei dem Unterfangen mir das notwendige Fachwissen anzueignen, habe ich mich durch etliche Quellen gewühlt. Ich will ja keinen Quatsch kaufen. Dabei ist mir aufgefallen, dass es die relevanten Informationen nirgends in der von mir gewünschten Detailtiefe gibt. Aus diesem Grund habe ich hier mal alles zusammengetragen, das ich im Zusammenhang mit Balkonkraftwerken als wissenswert erachte.



## Was ist ein Balkonkraftwerk?
Ein Balkonkraftwerk ist eine kleine, steckerfertige Photovoltaikanlage zur Stromerzeugung für den Privatgebrauch, die sich durch einen einfachen Aufbau auszeichnet. Das Balkonkraftwerk (BKW) wird direkt am Stromkreislauf des Haushalts angeschlossen und versorgt die eigenen Verbraucher. Entsprechend muss weniger Strom vom Netzbetreiber bezogen werden. Ist überschüssiger Strom vorhanden, der in den eigenen 4 Wänden gerade nicht verbraucht werden kann, wird dieser in das öffentliche Stromnetz eingespeist. 

Ein BKW speichert an sich keinen Strom, außer du hast einen Batteriestromspeicher in deinem System installiert. Deshalb ist ein herkömmliches Balkonkraftwerk vor allem interessant, um den Ruhestrombedarf deiner Wohnung oder deines Hauses abzudecken, da eingespeister Strom nicht vergütet wird. 

Hält man gewisse Rahmenbedingungen ein, kann ein Balkonkraftwerk gegenüber einer herkömmlichen Photovoltaikanlage in einem vereinfachten Anmeldeverfahren registriert werden.




## Wichtige Begriffe
Damit du mitdiskutieren und glänzen kannst, erkläre ich nachfolgend einige wichtige Begriffe, die du kennen solltest.

| Abkürzung | Begriff | Erläuterung |
| --- | --- | --- |
| - | Autarkiegrad | Prozentuales Verhältnis von selbstproduziertem Strom zu aus dem Netz bezogenen Strom |
| BKW |Balkonkraftwerk | Kleine Photovoltaikanlage zur Stromerzeugung (Alias: Mini-Photovoltaik-Anlage, Mini-PV, Steckerfertige PV-Anlage, Steckersolaranlage) |
| DTU | Data Transfer Unit | Gateway und Übertragungseinheit: Erfasst Daten vom Mikrowechselrichter (z.B. Einspeiseleistung) und ermöglicht deren Übertragung an andere Systeme. Zudem lässt sich teilweise damit die Einspeiseleistung regeln. |
| - | Eigenverbrauchsquote | Prozentuales Verhältnis von selbst verbrauchtem Strom zu selbst produziertem Strom. Da man für die Stromeinspeisung bei BKW keine Vergütung erhält, wird eine möglichst hohe Eigenverbrauchsquote angestrebt. |
| MPPT | Maximum Power Point Tracking | Ein MPPT Regler als Bestandteil eines Wechselrichters scannt die Leistungskurve der angeschlossenen Solarmoduls und findet so den höchsten Leistungspunkt, damit der größtmögliche Solarertrag erzeugt wird. |
| Peakleistung | Maximale Leistung der Module | Die Peakleistung stellt die theoretisch maximal mögliche Stromerzeugungsleistung dar, die die Solarmodule durch die Sonneneinstrahlung produzieren können |
| PV-Modul | Photovoltaik-Modul | Komponente zum Wandel von Solarenergie in elektrische Energie (Gleichstrom), besteht aus vielen Solarzellen, die den Solarstrom generieren |
| WR | Wechselrichter | Einheit zum Wandel von Gleichstrom in Wechselstrom, damit dieser ins Hausnetz eingespeist und von elektrischen Verbrauchern genutzt werden kann. |

## Relevante physikalische Grundlagen
In diesem Abschnitt möchte ich ein paar deiner physikalischen Grundkenntnisse auffrischen. Endlich kannst du mal die Inhalte des Physikunterrichts im Alltag anwenden!

### Elektrische Spannung (U):
Spannung entsteht, wenn positive Ladungen (+) und negative Ladungen (–) getrennt vorliegen. Elektrische Spannung wird durch die Einheit Volt (V) beschrieben. Sie beschreibt die Potenzialdifferenz zwischen zwei Punkten. D.h. mit welchem Druck der Strom durch die Leitung von einem Punkt zum anderen befördert wird.

### Elektrische Stromstärke (I):
Elektrischer Strom entsteht, wenn eine Spannung bzw. Potenzialdifferenz vorliegt, die elektrischen Ladungen durch einen elektrischen Leiter fließen und sich ausgleichen können. Die elektrische Stromstärke hat die Einheit Ampere (A). Diese Größe beschreibt, wie viele Elektronen sich innerhalb eines bestimmten Zeitraums durch eine elektrische Leitung bewegen. 

### Reihenschaltung 
Bei einer Reihenschaltung werden elektrische Komponenten (z.B. Lampen) hintereinander geschaltet (s. Abbildung). Das bedeutet, dass alle Komponenten in einem einzigen Stromkreis arbeiten.

![Reihenschaltung](/assets/smart-home/elektrische-schaltung_reihe.pdf){: width="400"}
_Abbildung: Schematische Darstellung einer Reihenschaltung (Quelle: beleuchtungdirekt.de)_

Folgende **Eigenschaften** gelten für eine Reihenschaltung:
* I_Gesamt = I_1 = I_2 = ... = I_n:  
Durch alle Komponenten fließt der gleiche Strom, daher ist die Stromstärke an jeder Stelle des Stromkreises gleich groß.
* U_Quelle = U_1 + U_2 + ... + U_n:  
Die Spannung der elektrischen Quelle teilt sich auf die Komponenten im Stromkreis auf. Alle Teilspannungen addieren sich zur Gesamtspannung. Schließt man eine Lichterkette an 230 Volt aus der Steckdose an und hat diese beispielsweise 10 Lampen, so erhält jede davon 23 Volt.
* Dadurch leuchten zum Beispiel mehrere Glühlampen nicht so hell, wie wenn eine einzelne Glühlampe eingebaut wäre.
* Wenn man eine Glühlampe herausdreht ist der Stromkreis unterbrochen und alle anderen Lampen gehen aus.

**Anwendungsfälle:** Immer dann, wenn sehr viele Verbraucher an einer Quelle angeschlossen werden (z.B. Lichterketten) oder wenn ein Gerät mehrere Batterien benötigt. Diese sind auch in Reihe geschaltet, um eine möglichst hohe Spannung zu erzielen. Wenn eine Komponente entfernt wird, gehen alle anderen aus. 

**Transfer zum Balkonkraftwerk:**
* Solarzellen innerhalb eines Solarmoduls werden in Reihe geschaltet.
* Theoretisch lassen sich mehrere Solarmodule in Reihe schalten, um höhere Spannungen und damit Stromerträge zu erzielen.
* Die zulässige Anzahl der in Reihe geschalteten Solarmodule ist abhängig von der max. Eingangsspannung des Wechselrichters.
* Mikrowechselrichter sind auf 1-2 Solarmodule pro Eingang ausgelegt.

### Parallelschaltung
Bei einer Parallelschaltung werden zwei oder mehr zweipolige Bauteile (+/-) miteinander verbunden (s. Abbildung). Dabei ist es wichtig, dass die gleichnamigen Pole immer miteinander verbunden werden. Jede parallel geschaltete Lampe verfügt über einen eigenen Stromkreis. Die Einzelströme addieren sich zu einem Gesamtstrom. Die elektrische Spannung ist für jede angeschlossene Lampe identisch. Das bedeutet auch, dass bei einem Ausfall eines Leuchtmittels, nicht automatisch alle anderen ebenfalls ausfallen. Die intakten Verbraucher leuchten also weiterhin.

![Parallelschaltung](/assets/smart-home/elektrische-schaltung_parallel.pdf){: width="400"}
_Abbildung: Schematische Darstellung einer Parallelschaltung (Quelle: beleuchtungdirekt.de)_

Folgende **Eigenschaften** gelten für eine Parallelschaltung:
* I_Gesamt = I_1 + I_2 + ... + I_n:  
Die Leitung teilt sich auf und damit teilt sich auch der Strom auf. Alle Teilstromstärken addieren sich zur Gesamtstromstärke.
* U_Quelle = U_1 = U_2 = ... = U_n:  
An jedem Bauteil liegt die gleiche Spannung an.
* Daher leuchten zum Beispiel mehrere Glühlampen genauso hell, wie wenn eine Einzelne eingebaut wäre.
* Wenn man eine Glühlampe herausdreht, leuchten die anderen Lampen weiter, da deren Stromkreis nicht unterbrochen ist.

**Anwendungsfälle:** Wenn mehrere Geräte mit derselben Spannung versorgt werden sollen (z.B. Netzspannungsversorgung aus allen Steckdosen im Haushalt (230 V), Mehrfachsteckdosen, …). Zudem können, wenn ein einzelner Verbraucher ausfällt, alle weiteren betrieben werden.

**Transfer zum Balkonkraftwerk:**
* Solarmodule werden parallel geschaltet, damit ein Modulausfall nicht die anderen Module beeinflusst.
* An einen Wechselrichter können in Abhängigkeit seines maximal zulässigen Eingangsstroms nur bedingt viele Solarmodule parallel angeschlossen werden.

Ich hoffe, ich habe dich hier nicht schon verloren. Ab jetzt wird es weniger theoretisch - versprochen!

## Komponenten eines Balkonkraftwerk

Ein Balkonkraftwerk besteht prinzipiell aus folgenden Komponenten:
1. Mikrowechselrichter (WR)
2. PV-Modul(e)
3. Modulhalterung
4. Solarkabel WR -> PV-Modul
5. Anschlusskabel WR -> Steckdose
6. optional: Data Transfer Unit (DTU)
7. optional: Batteriestromspeicher

![Schematische Darstellung der Komponenten eines Balkonkraftwerks](/assets/smart-home/balkonkraftwerk-schema.png){: width="400"}
_Abbildung: Schematische Darstellung der Komopnenten eines Balkonkraftwerks (Quelle: Westermann Netzwerke)_


### PV-Module

Das PV-Modul oder Solarmodul ist das Herzstück der Photovoltaikanlage zur Erzeugung des Stroms. Ein Solarmodul besteht aus einer bestimmten Anzahl einzelner Solarzellen, die miteinander verschaltetet sind.

**Eigenschaften einer Solarzelle:**

Die von Solarzellen erzeugte Spannung ist abhängig vom Halbleitermaterial. Kristalline Silizium-Solarzellen erreichen eine Spannung von maximal etwa 0,7 V. Deshalb muss zur Herstellung eines Solarmoduls eine große Anzahl Solarzellen durch hauchdünne Leiterbahnen elektrisch in Reihe verschaltet werden. Bei einer 156 mm x 156 mm großen Siliziumzelle erreicht die maximale Stromstärke unter Bestrahlung mit einer Lichtintensität von 1000 W/m² etwa 5,5 A.

![Prinzipielle Strom-Spannungs-Kennlinie einer Si-Solarzelle](/assets/smart-home/solarzelle_strom-spannungs-kennlinie.jpg){: width="400"}
_Abbildung: Prinzipielle Strom-Spannungs-Kennlinie einer Silizium-Solarzelle (Quelle: solarserver.de)_

Ein handelsübliches Photovoltaik-Modul mit 72 Zellen liefert eine maximale Spannung von 46 V und einen maximalen Strom von 5,2 A. Am Arbeitspunkt (bei 36 V und 4,5 A) erreicht dieses PV-Modul eine Spitzenleistung (Peak-Leistung) von 165 Watt-peak (Wp). Um die Installation großer Photovoltaik-Anlagen zu vereinfachen, liefert die Industrie auch wesentlich größere PV-Module. Inzwischen werden bereits Module mit mehr als 500 Wp Leistung angeboten.

**Eigenschaften eines Solarmoduls:**

Die Eigenschaften von Solarmodulen werden mittels 2 verschiedener Sätze an Testbedingungen ermittelt: 

1. Standardtestbedingungen (Standard Test Conditions, STC)
2. Nennbetriebstemperatur (Nominal Operating Cell Temperature, NOCT)

STC stellt Optimalbedingungen dar und ist der Standard zur Ermittlung der Eigenschaften, die anschließend im Datenblatt stehen. NOCT prüft praxisnahere Umgebungsbedingungen ab.

_Tabelle: Testbedingungen nach STC und NOCT_

|Eigenschaft        |STC        |NOCT|
|---|:---:|:---:|
|Lichtintensität    |1.000 W/m2 |800 W/m2|
|Zellentemperatur   |25°C       |-|
|Lufttemperatur     |-          |20°C|
|Luftmasse          |1,5        |1,5|
|Windgeschwindigkeit|-          |1 m/s|

Nachfolgend möchte ich wichtige technische Daten von PV-Modulen anhand des Vergleichs zwei verschiedener Module beschreiben:

1. Trina Solar Vertex S+ TSM-440NEG9R 440Wp
2. Ja-Solar JAM54S31-405/MR

|Elektrische Daten          |Trina (STC)    |Trina (NOCT)   |Ja-Solar (STC) |Ja-Solar (NOCT)|
|---|:---:|:---:|:---:|:---:|
|Nennleistung P_MPP         |440 Wp         |335 W          |405 Wp         |306 Wp|
|Nennspannung U_MPP         |44 V           |41,0 V         |31,21 V        |29,47 V|
|Leerlaufspannung U_OC      |52,2 V         |49,4 V         |37,23 V        |35,12 V|
|max. Ausgangsstromstärke / I_MPP |10,01 A  |8,17 A         |12,98 A        |10,38 A|
|Kurzschlussstrom I_SC      |10,67 A        |8,60 A         |13,87 A        |11,10 A|
|Nennbetriebstemperatur     |25 °C          |43 °C (±2 K)   |25 °C          |43 °C (±2 K)|

|Weitere Eigenschaften      |Trina          | Ja-Solar|
|---|:---:|:---:|
|Solarzellen-Typ            |monokristallin |monokristallin|
|Temperaturkoeffizient von PMAX| –0.30 %/K  |–0.35 %/K |
|Wirkungsgrad               |22 %           |20,7 %|
|Zellen pro Modul           |144            |108|


**Nennleistung P_MPP:** Die Leistung eines Solarmoduls wird in der Regel in Watt Peak (Wp) angegeben. Die Angabe bezieht sich auf die maximale Leistung, die das Solarmodul unter optimalen Bedingungen erreichen kann. In der Realität wird die Leistung aufgrund verschiedenster Einflussfaktoren geringer sein:

1. Schwankende Lichtintensität
2. Abweichung vom optimalen Einstrahlwinkel
3. Außentemperatur gemessem am Temperaturkoeffizienten
4. Verschattung der Module
5. Leistungsdegradation durch Alterung
6. Verschmutzung der Module

Aus diesem Grund wählt man meist Solarmodule aus, die gesamt eine höhere Peakleistung aufweisen als die Ausgangsleistung des Wechselrichter. Die Peakleistung dient also eher als Richtwert zur Vergleichbarkeit der einzelnen Solarmodule und –anlagen untereinander. 

**Erläuterung einiger Einflussfaktoren auf die Leistung:**

**Lichtintensität:** Die solare Einstrahlung wird in W/m² gemessen. Grundsätzlich kann davon ausgegangen werden, dass höhere Einstrahlungen zu höheren Leistungswerten bei den Modulen führen.

**Einstrahlwinkel:** Den höchsten Ertrag erzielt eine PV-Anlage, wenn das Sonnenlicht während möglichst vieler Stunden im rechten Winkel auf die Solarzellen trifft. Dies lässt sich durch die Ausrichtung und den Neigungswinkel der Solarzelle beeinflussen. Es ist allerdings anzumerken, dass geringe und selbst größere Abweichungen von der idealen Ausrichtung die Photovoltaik-Erträge nur geringfügig beeinträchtigen.

**Temperatureinfluss und Temperaturkoeffizient:** Silizium-Solarzellen haben einen negativen Temperaturkoeffizienten. D.h. je wärmer die Solarzelle wird, desto geringer ist deren Ertrag. Der Wert P_max im Datenblatt des jeweiligen Herstellers beschreibt die Leistungseinbußen des Solarpanels. Er gibt an, um wie viel Prozent sich die Leistung pro 1 Kelvin, ausgehend von der Standardtemperatur 25°C erhöht oder verringert. Mit jedem Grad Celsius nach oben verringert sich die Leistung um diesen Faktor, mit jedem Grad nach unten erhöht sich die Leistung um diesen Faktor.

In konkreten Zahlen ausgedrückt: Erwärmt sich ein herkömmliches 330 W-Modul mit einem Temperaturkoeffizienten von -0,5% von 25 auf 26 Grad Celsius, reduziert sich die Leistung um 1,65 Watt. Bei einem Temperaturanstieg auf 60 Grad, sind es 57,75 Watt. Die Modulleistung liegt dann nur noch bei 272 Watt.

In der Regel wird in Deutschland zwischen Mai und Juli die meiste Energie aus PV-Modulen gewonnen. Die Hitze im August und die Bewölkung im Herbst/Winter wirken sich negativ auf die Leistung von Solarpanelen aus. Dennoch nutzen PV-Module das im Winter und Herbst eintreffende Licht effizienter. Der Grund ist einfach - niedrige Temperaturen wirken sich positiv auf die Photovoltaik-Leistung aus.

**Parallelschaltung von Solarmodulen:** Durch die Parallelschaltung am Wechselrichter sind die Solarmodule leistungstechnisch unabhängig voneinander und können jeweils ihre optimale Leistung bereitstellen. Jedes Solarpanel ist nämlich auch direkt mit dem Wechselrichter verbunden.

Die Stromstärke der PV-Module wird bei der Parallelschaltung addiert und bildet so die Gesamtstromstärke des Systems. Die elektrische Spannung der Panels bleibt dabei gleich. Fällt die erzeugte Spannung des Moduls und damit dessen Leistung ab, beispielsweise durch eine Teilbeschattung oder einen Modulfehler, beeinflusst dies nicht die Leistung der anderen Module, da die Spannung der PV-Module in paralleler Schaltung gleichbleibt. Diese erzeugen weiterhin den vollen Stromertrag.

![Parallelschaltung von Solarmodulen](/assets/smart-home/solarmodule_parallelschaltung.png){: width="400"}
_Abbildung: Parallelschaltung von Solarmodulen (Quelle: grünes.haus)_

Möchte man mehr Module am Wechselrichter anschließen, als dieser Eingänge hat, muss man Module in Reihe schalten. Hierbei ist die maximale Eingangsstromstärke des Wechselrichters zu beachten. Wird bei einer Reihenschaltung ein Solarmodul zum Teil verschattet, mindert das den Stromertrag der ganzen Modulreihe. Hier würde die Spannung der ganzen Modulreihe gemindert, während die Stromstärke gleich bleibt.

**Jahresertrag:** Laut [Photovoltaic Geographical Information System (PVGIS)](https://re.jrc.ec.europa.eu/pvg_tools/en/) kann in Süddeutschland beispielsweise von einer Jahresleistung von einer Kilowattstunde (kWh) pro genannter Wattzahl (Wp) der Nennleistung einer Photovoltaikanlage ausgegangen werden. Im Norden Deutschlands dürfte der Wert etwas darunter liegen, da hier die Sonnenstrahlung niedriger ist.

**Nennspannung U_MPP:** Die Nennspannung eines Solarmoduls bezieht sich auf die maximale Spannung, die das Modul erzeugen kann, wenn es unter Standardtestbedingungen (STC) betrieben wird. Die Nennspannung wird in Volt (V) angegeben und ist ein Standardwert, der von den Herstellern von Solarmodulen festgelegt wird. Die Nennspannung eines Solarmoduls hängt von seiner Größe und Leistung ab und ist ein wichtiger Faktor bei der Auswahl und Planung einer Solaranlage.

**Leerlaufspannung U_OC:** Die Leerlaufspannung von Solarmodulen ist die höchstmögliche Spannung, die erzeugt werden kann, wenn dem Modul kein Strom entnommen wird. Sie tritt auf, wenn das Solarmodul mit offenen Klemmen betrieben wird und keine Last angeschlossen ist.

**Wirkungsgrad:** Der Wirkungsgrad gibt an, welcher Anteil der eingestrahlten Sonnenenergie in elektrische Energie umgewandelt wird. Die Wirkungsgrade von auf dem Markt erhältlichen PV-Modulen reichen von 15 bis 22%. 


### Wechselrichter
Ein Wechselrichter dient zur Umwandlung des in den Solarmodulen erzeugten Gleichsstroms (DC) in Wechselstrom (AC) für das Stromnetz. Dies passiert mittels DC/AC-Spannungswandler. Er wandelt diesen in die notwendige Spannungshöhe von 230 V und Frequenz von 50 Hz im deutschen Netz. 

Wechselrichter schalten sich ab, falls im Stromnetz keine Netzspannung mehr festgestellt wird, um eine unkontrollierte Einspeisung zu verhindern. Die Lebensdauer von Wechselrichtern beträgt ungefähr 15 Jahre.

Ich möchte einige wichtige technische Daten anhand zweier Wechselrichter des Herstellers Hoymiles (HM-800 und HMS-1600-4T) beschreiben.

|Eingangsdaten                |Hoymiles HM-800    | Hoymiles HMS-1600-4T   |
|---|:---:|:---:|
|Max. Panelleistung         |500 Wp             |540 Wp|
|Üblicherweise verwendete Modulleistung|2x 320 bis 500 Wp|2x 320 bis 540+ Wp|
|Empfohlene PV-Module (Zellen/Halbzellen)       |60/120 bis 72/144 | 54/108 bis 72/144|
|Eingangsspannungsbereich   |16 - 60 V          |22 - 65 V|
|MPP-Spannungsbereich       |34 - 48 V          |16 - 60 V|
|Einschaltspannung          |22 V               |22 V|
|max. Eingangsstrom         |2 × 12,5 A         |4x 15 A|
|max. Eingangskurzschlussstrom|2x 15 A|         |4x 25 A|
|Anzahl MPP-Tracker         |2                  |4|

|Ausgangsdaten                |Hoymiles HM-800    | Hoymiles HMS-1600-4T   |
|---|:---:|:---:|
|Ausgangsleistung           |800 W              |1.600 W|
|Ausgangsspannungbereich    |230 V, 180 - 275 V |230 V, 180 - 275 V|
|max. Ausgangsstromstärke   |3,48 A             |6,96 A|

**Max. Panelleistung:** Sie gibt die zulässige Peakleistung der angeschlossenen Solarmodule an.

**Eingangsspannungsbereich:** Maximale Spannung, die an den Eingängen des Wechselrichters durch die PV-Module anliegen darf.

**MPP-Spannungsbereich:** Spannungsbereich der PV-Module, in denen der MPPT den optimalen Leistungsbereich regeln kann. Die Module sollten entsprechend in diesem Spannungsbereich arbeiten.

**Max. Eingangsstrom:** Maximaler Strom, der an den Eingängen des Wechselrichters durch die PV-Module anliegen darf.

**Einschaltspannung:** Spannung, die am Wechselrichter durch die PV-Module anliegen muss, damit dieser die Umwandlung des Gleichstroms in Wechselstrom und damit die Einspeisung ins Stromnetz startet.

**Wirkungsgrad:** Trotz ihrer zahlreichen Aufgaben benötigen die Geräte selbst nur wenig Energie und bei der Energieumwandlung geht nur wenig Energie verloren. Die heute üblichen Wirkungsgrade liegen in einem Bereich von 95 bis 98 Prozent.

**Maximum Power Point Tracking (MPPT):** Punkt, an dem das Solarmodul mit der maximal möglichen Leistung (also im Idealfall der Nennleistung) arbeitet. Der Wechselrichter hat Einfluss auf den MPPT. In allen Wechselrichtern werden standardmässig sogenannte MPP-Tracker verbaut. Die Tracker steigern die Solarerträge, indem sie den optimalen Betriebspunkt („Maximum Power Point” = MPP) der Solarmodule ermitteln und halten. Hierbei wird im Wechselrichter die Spannung und Stromstärke durch Veränderung des Lastwiderstands so angepasst, dass die höchstmögliche Leistung ausgegeben werden kann. Dieser Prozess wird Maximum Power Point Tracking, kurz MPPT genannt. Bei gleicher Anzahl der MPP-Tracker und Module kann für jedes Modul der Höchstleistungspunkt einzeln errechnet werden, wodurch die Effizienz der gesamten Photovoltaikanlage optimiert wird.

**Ausgangsleistung:** Maximale Leistung, die der Wechselrichter an Wechselstrom zur Verfügung stellen kann. 

### Verbindungskabel
Der Mikro-Wechselrichter wird zuerst mit MC4-Solar-Steckern an das Solarmodul angeschlossen. Für den Betrieb der Photovoltaikanlage muss er dann noch an eine haushaltsübliche Steckdose oder eine Wieland-Einspeisesteckdose angeschlossen werden.


### Modulhalterung und Aufstellung
Die Modulhaltung dient zur Befestigung der Solarmodule auf dem Balkon, an der Fassade oder an anderen geeigneten Orten.

Es gibt verschiedene Aufstellungsarten für Balkonkraftwerke, die jeweils eine unterschiedliche Art der Befestigung bzw. Aufständerung benötigen:
1. Flachdach
2. Ziegeldach
3. Balkongeländer


### Optional: Data Transfer Unit (DTU)
Die Datenübertragungseinheit (engl.: Data Transfer Unit, DTU) dient, wie der Name bereits suggeriert, der Übertragung von Informationen des Wechselrichters. Mithilfe der DTU lassen sich Betriebs- und Leistungsdaten auslesen, Einstellungen verwalten oder auch Fehler analysieren. Bei Hoymiles Wechselrichtern lässt sich mittels DTU zudem die maximale Ausgangsleistung auf die regionale Leistungslimitation für Balkonkraftwerke drosseln.

### Optional: Batteriestromspeicher
Gegenbenenfalls kann ein Balkonkraftwerk noch zusätzlich durch einen Batteriestromspeicher erweitert werden, um die Eigenverbrauchsquote weiter zu steigern. Aufgrund der hohen Anschaffungskosten für den Speicher im Vergleich zum Rest des Balkonkraftwerks und dem niedrigen Stromertrag durch die wenigen Solarmodule muss die Investition auf Sinnhaftigkeit geprüft werden.


## Was muss ich tun, um ein Balkonkraftwerk betreiben?
Alles klar, jetzt habe ich verstanden, aus welchen Komponenten ein Balkonkraftwerk besteht und welche Faktoren Einfluss auf meinen Solarertrag nehmen. Und wie kann ich jetzt loslegen?

### Richtige Kombination von PV-Modul und Mikrowechselrichter
Moderne Wechselrichter sind die Steuerungszentrale der Solaranlage. Nicht jeder Wechselrichter passt zu jedem Solarmodul und ist damit kompatibel. Wichtig sind die technischen Eigenschaften der Solarmodule. Die Größe des Wechselrichters sollte auf die Größe der Anlage abgestimmt sein. Als ganz grob vereinfachte Daumenregel benötigst du pro kWp installierter Modulleistung einen Wechselrichter mit einer Nennleistung von 1 kVA. In der Praxis ist das Verhältnis nicht genau 1:1. Denn nur in den seltensten Fällen erzielt eine Solaranlage ihre theoretische Spitzenleistung. Die tatsächliche Leistung hängt von der Dachneigung, der Ausrichtung der Solarpanele und etwaigen Verschattungen ab.

Für eine passende Kombination von Mikro- oder Modulwechselrichter und Solarmodul reicht es nicht aus, nur die Leistung der Solarmodule in Watt zu kennen. Die elektrische Leistung ist das Produkt aus Spannung in Volt und Strom in Ampere (P = U * I). Die Ausgangsspannung und der Ausgangsstrom variieren bei unterschiedlichen Solarmodulen, auch wenn sie die gleiche Leistung in Watt haben. Ein Solarmodul mit 300 Watt kann z. B. eine maximale Ausgangsspannung von 32,75 V und einen maximalen Ausgangsstrom von 9,16 A haben. Multipliziert man beide Werte, ergibt das 300 Watt. Ein anderes Solarmodul mit der gleichen Leistung von 300 Watt hat eine Ausgangsspannung von 29,25 V und einen Ausgangsstrom von 10,25 A.

Ein geeigneter Wechselrichter muss sowohl die Spannung als auch den Strom des Solarmoduls der Photovoltaikanlage verarbeiten können. Das heißt, die auf dem Modul angegebene Spannung muss im Spannungsbereich des Wechselrichters liegen. Das Gleiche gilt für den Strom. Oftmals entstehen Fehler bei der Installation von Balkonkraftwerken, weil man nicht auf diese technischen Details achtet. Dann wird ein Defekt des Wechselrichters vermutet, obwohl die Ursache darin liegt, dass Wechselrichter und Solarmodul nicht aufeinander abgestimmt wurden.

### Anmeldung des Balkonkraftwerks
Bisher sind für die Anmeldung eines Balkonkraftwerks zwei Schritte zu tun:
1. Anmeldung bei der Bundesnetzagentur mittels [Marktstammdatenregister](https://www.marktstammdatenregister.de/MaStR) 
2. Anmeldung beim [örtlichen Netzbetreiber](https://www.ovag-netz.de/netzbetrieb/netzbetreiber-suche.html)

Zukünftig soll nur noch die Anmeldung beim Marktstammdatenregister notwendig sein. Die Daten werden dann an den Netzbetreiber weitergeleitet.

Die Bundesnetzagentur stellt eine Anleitung zur Anmeldung bereit: [Hilfe für Anmeldung des Balkonkraftwerks beim Marktstammdatenregister](https://www.marktstammdatenregister.de/MaStRHilfe/files/regHilfen/Registrierungshilfe_Balkonkraftwerk.pdf).
In folgendem Artikel findest du [weitere Infos zur Anmeldung](https://www.homeandsmart.de/balkonkraftwerk-anmelden). 


## Was gibt es zu beachten?
Um die Regularien für den Betrieb eines Balkonkraftwerk einzuhalten, gibt es einige Punkte zu beachten. Diese möchte dir nachfolgend erläutern.

**Systemgesamtleistungsgrenze**
Beim Kauf eines Balkonkraftwerks ist grundsätzlich die Nennleistung des Wechselrichters ausschlaggebend, weil dieser die Einspeisung des Balkonkraftwerks beschränkt. Die bisher zulässige Maximalleistung für Balkonkraftwerke liegt in Deutschland bei 600 W (DIN VDE V 0126-95:2022-11). Diese wird perspektivisch auf 800 W im Jahr 2024 erhöht, wie es bereits der europäische Standard ist (EU Verordnung 2016/631). 

**Peakleistung der Solarmodule**
Bisher gbit es keine Beschränkung für die installierte Gesamtleistung der Solarmodule bei Balkonkraftwerken. Die Solarmodule selbst können entsprechend eine höhere Maximalleistung aufweisen, z. B. 1200 Watt, als die zulässige Ausgangsleistung des Wechselrichters. Dies kann sinnvoll sein, um bei geringerer Sonneneinstrahlung trotzdem eine hohe Einspeiseleistung zu erzielen. In 2024 soll voraussichtlich die installierte Modulleistung auf 2.000 Wp für BKW beschränkt werden.

**Gefahr von Kabelbrand durch zu hohe Ströme**
In deutschen Haushalten werden normalerweise Sicherungen eingesetzt, die Ströme von 16 A zulassen. Damit wird der Betrieb von Verbrauchern mit maximal 3.680 Watt Leistungsabnahme abgesichert (230 V * 16 A).

Bei einem Balkonkraftwerk können nun weitere 600 Watt Leistungsabnahme dazu kommen. Diese werden nicht durch den Sicherungsautomaten begrenzt, da der Strom direkt über die Steckdose ins Hausnetz einspeist wird. Erreicht das Balkonkraftwerk seinen Maximalertrag von 600 W und sind zudem 4.280 Watt (3.680 W + 600 W) Leistungsabnehmer eingeschaltet, würden 18,6 A (4.280 W / 230 V) im Hausnetz fließen, ohne dass die Sicherung greift. 

Für moderne, normkonforme Elektroinstallationen ist das nicht ausreichend, um einen Kabelbrand zu verursachen. Lediglich bei einer veralteten Elektroinstallation sollte die Absicherung auf 13 A reduziert werden, um das Brandrisiko zu minimieren. Bei maximaler Einspeisung des Balkonkraftwerks würden 13 A + 2,6 A = 15,6 A im Hausnetz fließen, was die Elektroleitungen bedenkenlos aushalten. Bestenfalls kannst du das Balkonkraftwerk an einen eigenen Stromskreis oder einen Stromkreis mit Verbrauchern mit niedriger Leistungsaufnahme anschließen, damit das Risiko zu hoher Strömeflüsse gar nicht erst aufkommt.

**Anschluss ans Hausnetz**
Für den Anschluss des Balkonkraftwerks an das Hausnetz wird vom Verband der Elektrotechnik, Elektronik, Informationstechnik e. V. (kurz: VDE) eine Wieland Einspeisesteckdose empfohlen (DIN VDE V 0100-551-1). Diese muss durch eine Elektrofachkraft eingebaut werden. Sie bietet höhere Sicherheit gegenüber der herkömmlichen Schutzkontaktsteckdose (SchuKo). Der Anschluss an einer SchuKo-Steckdose soll aber durch den VDE geduldet und zukünftig ebenfalls offiziell akzeptiert werden.

**Anmeldung des Balkonkraftwerks notwendig**
Der Netzbetreiber ist für die Netzsicherheit verantwortlich. Haushalte, die Strom in das öffentliche Netz einspeisen, können nicht durch den Netzbetreiber reguliert werden und stellen somit Störeinflüsse dar. Der Netzbetreiber muss über den eingespeisten Strom und die entsprechende Leistung Bescheid wissen, um die Netzsicherheit zu gewährleisten. Wer ein Balkonkraftwerk betreibt, ohne es anzumelden und im Markstammdatenregister einzutragen, riskiert eine Strafe. Dem Netzbetreiber muss vor der Inbetriebnahme des Balkonkraftwerks mit der Anmeldung dessen ein Vorlauf von 2 Wochen gewährt werden, um ggf. den bestehenden Stromzähler zu tauschen.

**Austausch von alten Stromzählern notwendig**
Besitzt du in deinem Haushalt noch einen Einrichtungs-Stromzähler, der keine Rücklaufsperre besitzt, dreht sich dieser rückwärts, sofern überschüssiger Strom in das Stromnetz eingespeist wird. Dies ist unzulässig und deshalb tauscht dein Netzbetreiber nach Anmeldung deines Balkonkraftwerks kostenlos den bisherigen Zähler gegen einen Einrichtungs-Stromzähler mit Rücklaufsperre oder einen Zweirichtungszähler.

**Eingespeister Strom wird nicht vergütet**
Für den Strom, der durch dein Balkonkraftwerk erzeugt und ins öffentliche Stromnetz eingespeist wird, bekommst du keine Vergütung durch den Netzbetreiber. Entsprechend ist es nicht lukrativ, viele Module anzuschaffen, wenn du den erzeugten Strom überhaupt nicht selbst verbrauchen kannst. 

**Genehmigung von Vermieter oder Eigentümergemeinschaft notwendig**
Falls du zur Miete wohnst, solltest du dir die Genehmigung deiner Vermieterin bzw. deines Vermieters einholen. Bist du Eigentümer:in einer Wohnung und es gibt eine Eigentümergemeinschaft, musst du auch dort eine Genehmigung einholen, da es beim Aufbau eines Balkonkraftwerks um eine Veränderung der Fassade geht.


## Zusammenfassung und Fazit
Ein Balkonkraftwerk stellt eine niedrigschwellige Möglichkeit dar, um einen Teil deines Stromverbrauchs durch selbst erzeugten Solarstrom abzudecken. Dadurch kannst du deine Stromrechnung senken und gleichzeitig etwas für die Umwelt tun. 

Auf dem Weg zum eigenen Balkonkraftwerk gibt es einige Dinge zu beachten. Zum einen die bestehenden Regularien für dessen Betrieb und zum anderen die Auswahl geeigneter Komponenten. Ich habe dir in diesem Beitrag versucht alle wichtigen zusammenzutragen.

Nun will ich dir verraten auf welche Kombination von Wechselrichter und Solarmodul es bei mir hinauslaufen wird. Ich werde mir einen Hoymiles HM-800 Wechselrichter zusammen mit 2 Trina Solar Vertex S+ Modulen mit 144 Zellen kaufen. Welche Peakleistung der Module es am Ende wird, hängt vom besten Preis-Leistungs-Verhältnis zum Kaufzeitpunkt ab. Den Wechselrichter werde ich mittels OpenDTU auslesen und in Home Assistant integrieren. Wie eingangs erwähnt, geht es mir neben der Stromerzeugung auch um die Vernetzung und Integration in meinem bestehenden Smart Home System.

Falls du die Option hast ein Balkonkraftwerk zu betreiben, kann ich dir dies wärmstens ans Herz legen. Unter guten Bedingungen und hoher Eigenverbrauchsquote beträgt die Amortisationszeit ungefähr 3-4 Jahre für ein Balkonkraftwerk mit einer Leistung von 800 Wp bei Anschaffungskosten um die 500€.

## Quellen

Websites:
1. ![Website](/assets/img/book_888888.png){: w="14" } [Home and Smart: Hoymiles DTU Stick – Was kann er? (abgerufen am 03.09.2023)](https://www.homeandsmart.de/hoymiles-dtu)
2. ![Website](/assets/img/book_888888.png){: w="14" } [Bundesnetzagentur: Marktstammdatenregister](https://www.marktstammdatenregister.de/MaStR/)
5. ![Website](/assets/img/book_888888.png){: w="14" } [VDE: VDE schlägt einfachere Regeln für Balkonkraftwerke vor (Stand: 11.01.2023)](https://www.vde.com/de/presse/pressemitteilungen/2023-01-11-mini-pv)
6. ![Website](/assets/img/book_888888.png){: w="14" } [Haustec: Mino-PV: So werden Mikrowechselrichter richtig geplant (abgerufen am: 04.09.2023)](https://www.haustec.de/energie/wechselrichter/so-werden-mikrowechselrichter-richtig-geplant)
7. ![Website](/assets/img/book_888888.png){: w="14" } [Priwatt: Wechselrichter-Photovoltaik-Funktion: So arbeitet Dein Mikro-Wechselrichter (abgerufen am: 04.09.2023)](https://priwatt.de/blog/wie-funktioniert-ein-mikrowechselrichter/)
8. ![Website](/assets/img/book_888888.png){: w="14" } [Solar-Ratgeber: Wechselrichter auswählen: Qualität, Preise und Hersteller im Vergleich (abgerufen am: 05.09.2023)](https://solar-ratgeber.ch/solaranlage/vergleich-test/wechselrichter-auswaehlen/)
9. ![Website](/assets/img/book_888888.png){: w="14" } [PV-Insel: Welcher Wechselrichter passt zum Solarmodul meines Balkonkraftwerks? (abgerufen am: 05.09.2023)](https://pv-insel.de/pages/welcher-wechselrichter-passt-zum-solarmodul-meines-balkonkraftwerks)
10. ![Website](/assets/img/book_888888.png){: w="14" } [Energie-Experten: Einflussfaktoren auf die Leistung von Solarmodulen (abgerufen am: 05.09.2023)](https://www.energie-experten.org/erneuerbare-energien/photovoltaik/solarmodule/leistung)
11. ![Website](/assets/img/book_888888.png){: w="14" } [Photovoltiac Geographical Information System (PVGIS)](https://re.jrc.ec.europa.eu/pvg_tools/en/)
12. ![Website](/assets/img/book_888888.png){: w="14" } [Grünes Haus: Solarpanel-Leistung: darauf sollten Sie achten in 2023 (abgerufen am: 05.09.2023)](https://gruenes.haus/solarmodul-leistung/)
13. ![Website](/assets/img/book_888888.png){: w="14" } [The Greenwatt: STC vs NOCT: Understanding Test Conditions For Solar Panels (abgerufen am: 05.09.2023)](https://thegreenwatt.com/stc-vs-noct/)
14. ![Website](/assets/img/book_888888.png){: w="14" } [Solarwatt: Photovoltaik Ausrichtung (abgerufen am: 07.09.2023)](https://www.solarwatt.de/ratgeber/photovoltaik-ausrichtung)
15. ![Website](/assets/img/book_888888.png){: w="14" } [Grünes Haus: Solarmodule parallel schalten: Vor- und Nachteile der Parallelschaltung (abgerufen am: 07.09.2023)](https://gruenes.haus/solarmodule-parallel-schalten)
16. ![Website](/assets/img/book_888888.png){: w="14" } [Solarserver: Photovoltaik – Von der Solarzelle zum Modul (abgerufen am: 07.09.2023)](https://www.solarserver.de/wissen/basiswissen/photovoltaik-typen-und-eigenschaften-von-solarzellen)
17. ![Website](/assets/img/book_888888.png){: w="14" } [Enercity: Was ist elektrische Spannung und Stromstärke? (abgerufen am: 07.09.2023)](https://www.enercity.de/magazin/unsere-welt/stromspannung-stromstaerke-leistung-unterschied#)
18. ![Website](/assets/img/book_888888.png){: w="14" } [Simpleclup: Reihen- & Parallelschaltung (abgerufen am: 07.09.2023)](https://simpleclub.com/lessons/physik-reihen-parallelschaltung)

Datenblätter:
1. ![PDF](/assets/img/pdf_888888.png){: w="14" } [Hoymiles: Datenblatt Mikro- Wechselrichter HMS-1600 bis HMS-2000 (abgerufen am: 24.09.2023)](https://www.hoymiles.com/wp-content/uploads/2023/02/Datasheet_HMS-160018002000_LA_EN_V202301.pdf)
2. ![Website](/assets/img/book_888888.png){: w="14" } [Idealo: Hoymiles HM-800 - Datenblatt (abgerufen am: 05.09.2023)](https://www.idealo.de/preisvergleich/OffersOfProduct/202006605_-hm-800-mikrowechselrichter-hoymiles.html#datasheet)
3. ![Website](/assets/img/book_888888.png){: w="14" } [Idealo: Hoymiles HMS-800-2T - Datenblatt (abgerufen am: 05.09.2023)](https://www.idealo.de/preisvergleich/OffersOfProduct/203000415_-hms-800-2t-hoymiles.html#datasheet)
4. ![Website](/assets/img/book_888888.png){: w="14" } [Idealo: Trina Solar Vertex S+ TSM-440NEG9R 440Wp - Datenblatt (abgerufen am: 05.09.2023)](https://www.idealo.de/preisvergleich/OffersOfProduct/203198925_-vertex-s-tsm-440neg9r-440wp-trina-solar.html#datasheet)
5. ![PDF](/assets/img/pdf_888888.png){: w="14" } [Trina: Datenblatt Solarmodul Trina Vertex+ (abgerufen am: 05.09.2023)](https://static.trinasolar.com/sites/default/files/NEG9R.28_DE.pdf)
6. ![PDF](/assets/img/pdf_888888.png){: w="14" } [Ja-Solar: Datenblatt Solarmodul JAM54S31 (abgerufen am: 05.09.2023)](https://www.jasolar.com/uploadfile/2021/0706/20210706053145844.pdf)

Videos:
1. ![Video](/assets/img/video_888888.png){: w="14" } [Simon42: Balkonsolaranlage in Home Assistant einrichten (Energie Dashboard)](https://www.youtube.com/watch?v=t9qtMJCvfs4)
2. ![Video](/assets/img/video_888888.png){: w="14" } [Andreas Smitz: 0€ Balkonkraftwerk Dashboard einfach selbstgemacht](https://www.youtube.com/watch?v=RKOk74RxYus)

Normen:
1. ![Website](/assets/img/book_888888.png){: w="14" } [DIN VDE V 0126-95:2022-11 - Steckersolargeräte für Netzparallelbetrieb](https://www.vde-verlag.de/normen/1100702/e-din-vde-v-0126-95-vde-v-0126-95-2022-11.html)
2. ![Website](/assets/img/book_888888.png){: w="14" } [DIN VDE V 0100-551-1:2018-05 - Errichten von Niederspannungsanlagen](https://www.vde-verlag.de/normen/0100460/din-vde-v-0100-551-1-vde-v-0100-551-1-2018-05.html)
3. ![Website](/assets/img/book_888888.png){: w="14" } [EU Verordnung 2016/631 (Stand: 14. April 2016](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ%3AJOL_2016_112_R_0001)


Bildverweise:
1. Darstellung von Westermann Netzwerke: [Schematische Verbindung der Komponenten eines Balkonkraftwerks](https://www.westermann-netzwerke.de/wp-content/uploads/2020/04/Wieland_RST20_2_shop-ohne-dose.png)
2. Darstellung von Beleuchtungdirekt: [Schematische Darstellung einer Reihen- und Parallelschaltung](https://www.beleuchtungdirekt.de/blog/reihen-und-parallelschaltung)
3. Darstellung von Solarserver: [Prinzipielle Strom-Spannungs-Kennlinie einer Si-Solarzelle](https://www.solarserver.de/wissen/basiswissen/photovoltaik-typen-und-eigenschaften-von-solarzellen)
4. Darstellung von Grünes Haus: [Parallelschaltung von Solarmodulen](https://gruenes.haus/solarmodule-parallel-schalten)