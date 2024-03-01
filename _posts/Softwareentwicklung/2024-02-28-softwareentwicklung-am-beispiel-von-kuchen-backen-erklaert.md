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

> In (Klammern) stehen die Begriffe aus der Softwareentwicklung. Mir geht es in der Anekdote nicht um 100% Korrektheit, sondern darum, ein grobes Verständnis der Begrifflichkeiten zu vermitteln.
{: .prompt-info }

Du hast zum Glück das Rezept für Omas legendären Schokoladenkuchen (**Software**) aufgeschrieben. Deine kleine Schwester (**Stakeholder/Kundin**) hätte ihn nur gerne etwas abgewandelt (**Customizing**). Kein Problem!

### Vorbereitung (Planung)
1. Auf der Notiz (**Ticket**), die deine kleine Schwester geschrieben hat, steht, dass der Kern des Kuchens mit Smarties gefüllt sein soll (**Feature/Anforderung**). Du hälst kurz Rücksprache mit ihr, ob du alles richtig verstanden hast (**Anforderungsklärung)**.
2. Jetzt ist etwas Gehirnschmalz gefordert. Du (**Softwareentwickler:in**) überlegst dir, wie du das originale Rezept anpassen musst, damit der Kern aus Smarties bestehen kann (**Refinement**). Dabei musst du analysieren, welche Auswirkungen die Veränderung auf den restlichen Kuchen hat (**Impact**). Du wirst ja sicherlich nicht mehr so viel Mehl benötigen.
3. Bevor du dich an die Arbeit machst, sprichst du noch mit 2 Freund:innen (**Entwickler:innen**), wie viel Zeit man voraussichtlich für die Änderung des Kuchenrezepts benötigt (**Estimation**).
4. Da deine Mutter die Chefin (**Product Owner**) in der Küche ist, schaut sie auf die anstehenden Arbeiten in der Küche (**Backlog)** und plant deine Back-Session ein (**Sprintplanung**).
5. Du prüfst, ob in der Küche ein Mixer ist, der dir das Verrühren der Zutaten erleichtert (**Dependency**). Der Mixer ist zwar da, aber beim genauen Hinschauen fällt dir auf, dass das Stromkabel gebrochen ist und eine Sicherheitslücke (**Common Vulnerabilities and Exposures, CVE**) beinhaltet. 
6. Das bisherige Modell des Mixers (**Version**) ist veraltet (**deprecated**) und wird nicht mehr produziert (**Maintenance**). Du musst nun eine neuere Version (**Update**) kaufen. Jetzt gilt es zu überprüfen, ob der neue Mixer noch zur vorhandenen Rührschüssel und den restlichen Utensilien passt (**Kompatibilität**). Falls nicht, musst du wohl oder übel auch bei diesen noch Anpassungen vornehmen (**Migration**).

### Rezept abarbeiten (Entwicklung)
7. Du nimmst das Kochbuch (**Repository**) mit Omas Kuchenrezept (**Source Code**) und schnappst dir einen Stift (**Integrated Development Environment, IDE**).
8. Damit du nicht einfach Omas Originalrezept (**Master Branch**) überschreibst, nimmst du dir lieber einen separaten Zettel (**Feature Branch**), wo du die Rezeptänderungen vornehmen kannst. 
9. Du schreibst das geänderte Rezept auf (**Implementierung**).
10. Wenn du denkst, dass du fertig bist, lässt lieber nochmal einen deiner Freunde (**4-Augen-Prinzip**) über die Änderungen schauen, ob alles soweit stimmig ist (**Review**).
11. Deine Tante schaut vorbei und prüft (**Codeanalyse**), ob du dich beim Rezept an die Vorgaben der Familie (**Unternehmensrichtlinien**) und nur Bio-Zutaten verwendet hast (**Code Conventions**).
12. Nun rufst du Oma an und fragst, ob du das originale Rezept mit den Änderungen überschreiben darfst (**Merge Request**). Du sprichst das orignale Rezept nochmal mit Oma durch und stellst sicher, dass sie es in der Zwischenzeit nicht selbst nochmal angepasst hat (**Pull**) und schaffst etwaige Widersprüche (**Merge Conflicts**) aus der Welt.
13. Da du Oma ohnehin schon am Hörer hast, lädst du sie für den Nachmittag zum Kuchen essen ein (**Release Planung**).

### Backen (Kompilierung)
12. Nun aber genug des Schreibens… jetzt geht es ans Backen! Du rufst mir (**Build Tool**) zu und sagst, dass ich jetzt mit dem Backen loslegen kann (**Build Pipeline**). Ich sammle alle Zutaten und notwendigen Backutensilien (**Dependencies**) ein und mache mich ans Werk.
13. Als das Rezept schon halb durchlaufen ist, fällt mir auf, dass noch eine Zutat fehlt (**Blocker**). Du beauftragst deinen Vater (**Projektmanager**) schnell noch in den Supermarkt zu fahren und die fehlende Zutat einzukaufen (**Problemlösung**).
14. Dank der hervorragenden Anleitung gibt es keine weiteren Komplikationen und Fehler (**Exceptions**) während des Backens bleiben aus.

### Probieren & Essen (Testing & Release)
15. Du zeigst deiner Schwester das Zwischenergebnis (**Sprint Review**).
16. Jetzt kommt der Duft des fertigen Kuchens (**Kompilierter Code**) aus dem Ofen.
17. Bevor der Kuchen von der ganzen Familie (**User**) gegessen wird, lässt du deine kleine Schwester und deinen großen Bruder (**Key User**) probieren (**Testphase**), ob der Schokoladenkuchen mit Smarties auch wirklich so geworden ist, wie angefordert (**Customer Quality Assurance**) oder irreguläre Abweichungen (**Bugs**) beinhaltet.
18. Ich nehme den Kuchen und packe ihn (**Bereitstellung**) erstmal in einem Kuchenbehälter (**Repository/Registry**). 
19. Wenn die Zeit gekommen ist, stelle ich den Kuchen (**Deployment**) auf den gedeckten Tisch (**Infrastruktur/OnPremise/Cloud**), damit zur Kaffeezeit die ganze Familie in dessen Genuss kommen (**Release**) und ihren Kuchenhunger (**Kundenproblem**) stillen kann. Es regnet positives Feedback (**Kundenzufriedenheit**).
20. Weil ich so stolz auf mein Werk bin, schreibe ich meinen Freunden, wie lecker der Kuchen geschmeckt hat und wie schön cremig er gewesen ist (**Dokumentation**). Ein voller Erfolg!

## Zusammenfassung und Fazit
Ich habe dir in diesem Beitrag eine Anekdote erzählt, mit der du nächstes Mal interessierten Menschen aus deinem Bekanntenkreis erklären kannst, was Softwareentwicklung ist und wie sie abläuft. Prima, oder?

Ehrlicherweise muss ich sagen, dass man in der Softwareentwicklung oft mehrere Schleifen drehen muss, bis die Anpassungen die gewünschte Qualität haben. Zum Glück muss man aber nicht komplett von vorne anfangen, wie es bei einem Kuchen wahrscheinlich der Fall wäre.

Hier noch eine Zusammenfassung der genannten Begriffe inkl. Erklärung und Kuchen-Parabel (kein Anspruch auf Vollständigkeit):

![Wenn Softwareentwicklung Kuchen backen wäre](/assets/softwareentwicklung/2024-02-28%20Wenn%20SWE%20Kuchen%20backen%20waere.png){: w="500" } 
_Zusammenfassung der Begriffe aus der Softwareentwicklungs inkl. Erklärung und Kuchen-Parabel_

## Quellen

### Bildverweise
1. Schokoladenkuchen: Foto von [Jennifer Pallian](https://unsplash.com/de/@foodess) auf [Unsplush](https://unsplash.com/de/fotos/schokoladenkuchen-gRZYR210m0U)
2. Softwareentwicklung: Foto von [Christopher Gower](https://unsplash.com/de/@cgower) auf [Unsplash](https://unsplash.com/de/fotos/ein-macbook-mit-codezeilen-auf-dem-bildschirm-auf-einem-belebten-schreibtisch-m_HRfLhgABo)