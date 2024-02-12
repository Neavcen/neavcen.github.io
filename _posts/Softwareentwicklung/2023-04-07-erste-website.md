---
layout: post
title: Ich habe meine erste eigene Website!
description:
image:
categories: [Softwareentwicklung]
tags: [website,github-pages,hosting,jekyll,chirpy-theme]
date: 2023-04-07 11:45 +0200
---
Wow, das ist der erste Blog-Beitrag meines Lebens!

Zugegebenermaßen wollte ich nie einen Blog schreiben. Leute, die sowas tun, waren für mich immer Wichtigtuer:innen. Als ob das Leben eines Normalos so spannend sei, dass man allen davon im Internet erzählen müsste...
Bin ich stolz auf meinen Blog? Ja! Aber nicht aufgrund der Inhalte, sondern weil ich eigenständig (naja, ist Auslegungssache) die Infrastruktur dafür geschaffen habe.

## Motivation

Diese Website ist aus reiner Neugierde entstanden, weil ich schon immer wissen wollte, wie man so ein Projekt realisiert und was alles dazu gehört. Ich wollte schon immer meine eigene Website besitzen, habe aber nie den ersten Schritt gemacht, da ich es mir nicht zugetraut habe. Im März 2023 war's dann soweit. 

## Domain

Aufhänger war ein Deal auf [Mydealz](https://www.mydealz.de), bei dem ich mir für ca. 1,50€/Jahr meine eigene de-Domain erwerben konnte. In meinem Fall war es bei [Netcup](https://www.netcup.de), aber es gibt auch unzählige andere. Einfach mal vergleichen, wo es gerade ein gutes Angebot gibt.

Jetzt hatte ich zwar eine eigene Domain, aber diese sagte nichts weiter als _"Diese Domain ist geparkt"_. Das ist zugegebenermaßen noch keine Errungenschaft um vor Stolz zu platzen. Also habe ich mich damit auseinandergesetzt, wie ich ohne großartige Programmierkenntnisse eine Website ins Leben rufen kann. Ich wollte aber nicht Wordpress, Jimdo o.ä. verwenden. 

## Hosting

Ich habe zwar einen kleinen Home Server zu Hause, aber diese Möglichkeit zum Hosten war mir als erster Schritt zu heiß. Ich kenne mich nicht gut genug mit Cyber Security und Netzwerksicherheit aus, um allen Leuten aus dem Internet Zugriff auf mein Heimnetzwerk gewähren zu wollen. Letztlich bin ich auf [Github Pages](https://pages.github.com) als kostenlose Möglichkeit des Hostings gestoßen. Da ich ohnehin einen Github Account habe, lag es nahe dies mal auszuprobieren. Gesagt, getan. Was tut man zuerst? Klar, die Dokumentation öffnen und speziell das Getting Started lesen. 

## Frameworks

Schnell war klar, ist alles gar nicht so kompliziert, wenn man ein Framework wie [Jekyll](https://jekyllrb.com) an die Hand bekommt, das den Rahmen schafft und den Großteil der Arbeit übernimmt. Das [Video zu Jekyll von Techno Tim](https://www.youtube.com/watch?v=F8iOU1ci19Q) hat mir bei der Einrichtung geholfen und so habe ich mich auch für das [Theme "Chirpy"](https://github.com/cotes2020/jekyll-theme-chirpy) entschieden.

Das Deployment wird über ein enthaltenes Deployment Skript aus dem Chirpy Repository und Github Actions übernommen. Kurz noch die eigene Domain hinterlegen und fertig ist die eigene Website! Wow, das ging deutlich leichter als erwartet! Ein richtiger Erfolg für mich! :)

## Zusammenfassung

Hier nochmal die **notwendigen Schritte kurz und bündig zusammengefasst**:
1. Github Account registrieren
2. IDE (z.B. VSCode) installieren
3. SSH Key generieren und in Github Account hinterlegen
4. Chirpy Repository in eigenes Repository ("username".github.io) kopieren
5. In den Einstellungen von Github Pages "Github Actions" als Build und Deployment Methode hinterlegen
6. Optional, falls eigene Domain gewünscht:
   1. Eigene Domain bei einem Anbieter buchen
   2. Beim Domain-Provider die URL des Github Pages Repository hinterlegen
   3. In den Einstellungen von Github Pages die eigene Domain als Custom Domain hinterlegen 
7. Eigenes Repository mit VSCode verbinden und clonen
8. Notwendige Abhängigkeiten (Dependencies) in VSCode aus dem Jekyll Getting Started Guide installieren
9. Anpassungen vornehmen, committen und auf Github pushen
10. Website aufrufen und fertig!

## Nutzung

Da ich diesen Meilenstein geschafft habe, nutze ich meine Website, um zukünftig ein paar der Themen zu präsentieren, die mich beschäftigen. Weniger um berühmt zu werden und Leute mit meinem Content zu nerven, als vielmehr um meine Gedanken zu sortieren und einen Ort für diese zu haben. Wenn am Ende etwas Spannendes für die Öffentlichkeit dabei ist, umso besser.