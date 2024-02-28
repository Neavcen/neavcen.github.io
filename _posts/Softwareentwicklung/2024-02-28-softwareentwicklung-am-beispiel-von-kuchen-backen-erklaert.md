---
layout: post
title: Softwareentwicklung am Beispiel von Kuchen backen erklärt
description: Wenn man nicht in der Softwareentwicklung tätig ist, fällt es oft schwer
  zu verstehen, was die Menschen dort eigentlich tun. Ich möchte Abhilfe schaffen,
  indem ich eine Alltagssituation, nämlich Kuchen backen, mit der Entwicklung von
  Software vergleiche.
image:
  path: "/assets/softwareentwicklung/2024-02-28 swe-meets-cake.png"
  alt: Fotos von Jennifer Pallian und Christopher Gower auf Unsplash (bearbeitet)
categories:
- Softwareentwicklung
tags:
- Repository
- IDE
- Implementierung
- Review
- Quality Assurance
- Branch
- Merge Request
- Merge Conflict
- Source Code
- Build Tool
- Dependencies
- Build Pipeline
- Deployment
- Release
date: 2024-02-28 21:01 +0100
---
## Einleitung
Wenn du im Softwareentwicklungsumfeld tätig bist oder eben auch nicht, hat sich sicherlich nachfolgende Situation so oder so ähnlich schon bei dir zugetragen und du hast eine der zwei Rollen eingenommen:

Aus der Verwandtschaft oder dem Freundeskreis kommt die Frage, was du eigentlich in deinem Job machst. Du überlegst, wie du deine Aufgaben im IT Umfeld verständlich erklären kannst. Doch sobald du die ersten Fachbegriffe in den Raum wirfst, merkst du, wie dein Gegenüber abschaltet.

Für Menschen, die nicht aus der IT kommen, ist es meist schwierig zu verstehen, wie die abstrakt wirkenden Prozesse in der Softwareentwicklung ablaufen. Dabei ist es letztlich auch "nur" ein Handwerk. 

## Motivation
Während des Onboardings neuer Kolleg:innen in der IT-Projektleitung erkläre ich wichtige Begrifflichkeiten aus dem IT Projektumfeld. Doch wie erkläre ich diese teils sehr technischen Zusammenhänge so, dass auch IT-Neulinge sie verstehen? 

So kam mir während eines Termins mit einer neuen Kollegin die Idee, die abstrakten Begriffe der Softwareentwicklung mit einer Kuchen-Parabel zu vergleichen, um einen Alltagsbezug herzustellen. Siehe da, es lassen sich hervorragende Parallelen ziehen!

Also lass' uns Kuchen backen!

## Parallelen von Softwareentwicklung und Kuchen backen

Du hast zum Glück das Rezept für Omas legendären Schokoladenkuchen aufgeschrieben. Deine kleine Schwester hätte ihn nur gerne etwas abgewandelt. Kein Problem!

1. Erstmal die Änderungswünsche (**Anforderungen im Ticket**) deiner kleinen Schwester (**Stakeholder/Kundin**) lesen.
2. Du (**Softwareentwickelnde**) nimmst das Kochbuch (**Repository**) mit Omas Kuchenrezept (Source Code) und schnappst dir einen Stift (**Integrated Development Environment, IDE**).
3. Damit du nicht einfach Omas Originalrezept (**Master Branch**) überschreibst, nimmst du dir lieber einen separaten Zettel (**Feature Branch**), wo du das geänderte Rezept aufschreibst (**Implementierung**).
4. Du lässt lieber nochmal eine dritte Person (**4-Augen-Prinzip**) drüber schauen, ob das soweit stimmig ist (**Review/Quality Assurance**).
5. Nun rufst du Oma an und fragst, ob du das originale Rezept mit den Änderungen überschreiben darfst (**Merge Request**). Du sprichst das orignale Rezept nochmal mit Oma durch (**Pull**) und stellst sicher, dass sie es in der Zwischenzeit nicht selbst nochmal angepasst hat und schaffst etwaige Widersprüche (**Merge Conflicts**) aus der Welt.
6. Nun aber genug der Vorbereitung… jetzt geht es ans Backen! Du rufst mir (**Build Tool**) zu und sagst, dass ich jetzt mit dem Backen loslegen kann (**Build Pipeline**). Ich sammle alle Zutaten und notwendigen Backutensilien (**Dependencies**) ein und mache mich ans Werk.
7. Dank der hervorragenden Anleitung passieren keine Fehler (**Exceptions**) während des Backens und der Duft des fertigen Kuchens (**Kompilierter Code**) kommt aus dem Ofen.
8. Ich nehme den Kuchen und stelle ihn auf den gedeckten Tisch (**Deployment**), damit wir zur Kaffeezeit alle in dessen Genuss kommen (**Release**) und stillen damit den Hunger (**Kundenproblem**).

Wie hat dir unsere Back-Session gefallen? Hast du jetzt ein genaueres Bild davon, was Softwarentwicklende tagtäglich tun?

> Hinweis: Mir geht es hier nicht um 100% Korrektheit, sondern darum, ein grobes Verständnis der Begrifflichkeiten zu vermitteln.
{: .prompt-info }

## Zusammenfassung und Fazit
Ich habe dir in diesem Beitrag eine Anekdote erzählt, mit der du nächstes Mal interessierten Menschen aus deinem Bekanntenkreis erklären kannst, was Softwareentwicklung ist und wie sie abläuft. Prima, oder?

Hier noch eine Zusammenfassung der genannten Begriffe inkl. Erklärung und Kuchen-Parabel (kein Anspruch auf Vollständigkeit):

![Wenn Softwareentwicklung Kuchen backen wäre](/assets/softwareentwicklung/2024-02-28%20Wenn%20SWE%20Kuchen%20backen%20waere.png){: w="500" } 
_Zusammenfassung der Begriffe aus der Softwareentwicklungs inkl. Erklärung und Kuchen-Parabel_

## Quellen

### Bildverweise
1. Schokoladenkuchen: Foto von [Jennifer Pallian](https://unsplash.com/de/@foodess) auf [Unsplush](https://unsplash.com/de/fotos/schokoladenkuchen-gRZYR210m0U)
2. Softwareentwicklung: Foto von [Christopher Gower](https://unsplash.com/de/@cgower) auf [Unsplash](https://unsplash.com/de/fotos/ein-macbook-mit-codezeilen-auf-dem-bildschirm-auf-einem-belebten-schreibtisch-m_HRfLhgABo)