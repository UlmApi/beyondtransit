# EVU-Open-Data-FAQ

## Wenn das EVU Daten zur Verfügung stellen sollte, wie kann eine Schnittstelle dafür aussehen?

Generell ist zwischen einer Schnittstelle (API-Endpunkt) und der Bereitstellung von Bulk-Datensätzen zu unterscheiden. Letztere waeren beispielsweise die DS100-Schlüssel samt relevanter Daten dazu (Koordinaten, weitere Schlüssel wie IBNR etc.) in einem offenen, strukturierten Format. Fuer Daten mit seltenen Änderungen wie einen Sollfahrplan ist die Bereitstellung als Bulk-Datensatz vorzuziehen.

Die Bereitstellung sollte sich an den [5 Sternen für offene Daten](http://5stardata.info/) orientieren und hier möglichst viele der 5 Sterne zu erreichen versuchen.

Fuer API-Endpunkte sollte sich die Bereitstellung an etablierten _internationalen_ Standards orientieren, deren Spezifikation frei verfuegbar ist.


## In welcher Form sollten dann die Daten zur Verfügung gestellt werden? (Roh oder veredelt; Mgl.1:Rohdaten, bereinigt um qualitative Fehler; Mgl.2:strukturelle Veränderung)

Rohdaten sind in den meisten Fällen vorzuziehen. Eine pauschale Aussage zu Veredelungen fällt schwer, das kommt auf den Einzelfall an. 

Wenn möglich, soll auch im Falle einer „Veredelung“ gleichzeitig Zugriff auf die Rohdaten gewährt werden. Die Erfahrung zeigt, dass sich quasi immer jemand aus der Community findet, die/der hilft, die Rohdaten für das jeweilige Projekt passend aufzubereiten. Häufig fällt es auch schwer, eine klare Grenze zu ziehen, wo bereits eine Veredelung stattfindet, und was noch _Roh_daten sind. Ein Verkehrsunternehmen soll die Daten in der granularsten Form anbieten, in der sie intern vorliegen.

Wirkliche Rohdaten haben bisweilen den Nachteil, dass sie schwierig zu interpretieren sind. Wenn beispielsweise für die Verspätungen (Prognosen) mehrere Hochrechnungen gemacht werden, dann sollte nur die wahrscheinlichste publiziert werden. Auch gute Dokumentation des Datenformats, idealerweise mit Beispielen, kann helfen, dass die Daten auch wirklich korrekt interpretiert und verwendet werden können.

## Welches Format wäre sinnvoll?

Für Sollfahrplandaten hat sich das GTFS-Format als de-facto-Standard etabliert. Da die auf Google Transit bereitgestellten GTFS-Daten nicht immer perfekt exportiert zu sein scheinen, böte sich auch das intern verwendete Austauschformat (vermutlich HAFAS) samt einer Dokumentation an. Die Open-Data-Community würde sich in diesem Fall selbst um eine Konversion kümmern. Dieser Weg wird z.B. in den Niederlanden gegangen.

Auch in der Schweiz werden die Daten von der SBB [als HAFAS-Rohdaten-Format publiziert](http://fahrplanfelder.ch/fahrplandaten) (eine Doku liegt ebenfalls dort). Die Daten werden von einer unabhängigen Stelle [regelmässig auf GTFS umgerechnet](http://gtfs.geops.ch), wobei auch komplexere Modellierungsfälle wie Flügelungen berücksichtigt werden.

Falls Echtzeitdaten im [GTFS-RT](https://developers.google.com/transit/gtfs-realtime/)-Format bereitgestellt werden, lassen sich diese Daten mit einem GTFS-Feed zu einer Gesamtlage mit Sollfahrplan und nur den Abweichungen über die Ist-Schnittstelle kombinieren. Diese Kombination ist im Vergleich zum klassischen VDV-Ansatz (Hafas, EFA oder neuerdings TRIAS) sehr datensparsam. Beim Ausfall der Echtzeitschnittstelle oder einem Netzausfall ist ein Rückfall auf den Sollfahrplan möglich. Analog funktioniert auch die Kombination von NeTEx und SIRI.

Durch die [Delegierte Verordnung (EU) 1926/2017](https://eur-lex.europa.eu/legal-content/DE/TXT/?uri=CELEX%3A32017R1926) werden die Datenformate NeTEx und SIRI für die Veröffentlichung gefordert. Natürlich ist es zulässig und ggf. auch sinnvoll, sowohl NeTEx/SIRI als auch GTFS/GTFS-RT bereitzustellen.

Theoretisch besteht die Möglichkeit, mit Linked Data verschiedene Datenquellen semantisch zu verknüpfen. Hierbei wird das Datenformat mit Semantikinformationen angereichert.

## Was könnte ein allgemeiner Mehrwert der Bereitstellung sein?

Die Bereitstellung offener Daten hat bislang in vielen Bereichen zur Entwicklung von innovativen Lösungen geführt, die vorher von den Dateneignern nicht realisiert werden konnten – entweder, weil sie den speziellen Anwendungsfall nicht erkannt hatten, oder weil ihnen das Know-How für die Erarbeitung fehlte, oder weil die Entwicklung einer Lösung für einen speziellen Anwendungsfall finanziell nicht leistbar war.

Ein EVU kann so indirekt die Ausweitung der Angebotspalette innovativer Mobilitätsanwendungen fördern, die auch seinen eigenen Kund_innen zugute kommen.

## Für wen könnte die Bereitstellung interessant werden?

Die Bereitstellung kann letztlich für vier Gruppen interessant sein:

 * interessierte ÖPV-Nutzer_innen mit IT-Hintergrund, die mit den Daten für sie alltägliche Probleme der OPV-Nutzung lösen können
 * ÖPV-Nutzer_innen ohne IT-Hintergrund, die mit denselben Problemen zu kämpfen haben, und die später auf die Entwicklungen der ersten Gruppe zurückgreifen kann
 * der ÖPV-Anbieter selbst, da seine Kund_innen auf ein deutlich vielfältigeres Angebot an helfenden Applikationen zurückgreifen können, und da er bewährte Lösungen ggf. in sein eigenes Angebot überführen kann
 * Anwendungsorientierte Forscher_innen im Bereich von Datenanalyse und Optimierung, die an neuen Suchverfahren (z.B. „robuste Fahrplanauskunft“) oder auch an betrieblichen Optimierungsverfahren („intelligente Umlaufplanung“) arbeiten. Der Nutzen liegt hier prinzipiell nicht darin, das datenliefernde EVU zu bewerten, sondern komplexe analytische Verfahren (weiter) zu entwickeln und mit realistischen Datensätzen zu testen. Ggf. ergeben sich hier dann auch mittelfristig Kooperationen mit den liefernden EVU.

### Beispiele für mögliche Lösungen (die Liste ist keineswegs abgeschlossen):

 * Plattformen zur Wohnungsvermittlung, die solche Daten später in die Suche einbeziehen könnten. Hierbei gab es z.B. ein Projekt vom Hasso-Plattner-Institut.
 * Offline-Apps, die rein mit dem Sollfahrplan arbeiten – unter Inkaufnahme, dass eventuelle Verspätungen oder Störungen nicht in das Routing einfließen. Dieser Anwendungsfall kann beispielsweise für Tourist_innen mit ausländischer SIM-Karte ohne oder mit nur sehr beschränktem Datenvolumen interessant sein – aber auch in Bereichen des ÖV, in denen nur sehr schwer mobiles Internet zu empfangen ist.
 * Robuste Fahrplanauskunft (oder auch realistische Fahrplanauskunft) bezieht heute typische Störungen noch nicht in die Offline-Planung ein (siehe oben). Er ist sicherlich nicht nur für Touristen interessant, sondern für alle ÖPNV-Nutzer_innen, die ihre Route vorher planen muss. Durch große Mengen von Realdaten können so auch sehr individuelle Reiseprofile berücksichtigt werden.
 * Deutlich individueller auf spezielle Anwendungsfälle zugeschnittene Beauskunftungen, beispielsweise eine Kombination bestimmter Verkehrsmitteln unter Ausschluss bestimmter Bahnhöfe mit variablen Umsteigezeiten. Dies kann interessant sein, um multimodale Auskünfte beispielsweise unter Berücksichtigung einer Fahrradnutzung (oder -mitnahme) oder unter Einbeziehung relevanter Daten aus Drittquellen zu ermöglichen.
 * Konkrete Beispiele sind z.B. die seit ca. 2018 entstandenen lokalen [digitransit-Installationen](https://transportkollektiv.github.io/digitransit-setup/), die neben ÖV-Fahrplänen auch weitere Informationen wie Bikesharing, Carsharing, Parkhausauslastung uvm integrieren und kombinieren.

## Wären Sie bereit für die Nutzung der Schnittstelle Geld zu bezahlen? Wenn ja/nein, warum?

Absolut nicht.

Das Ziel ist aus- und nachdrücklich **Open** Data – das bedeutet gemäß der [Open Definition](http://opendefinition.org/od/), dass das Erheben von Lizenzgebühren ausdrücklich nicht erlaubt ist.

Wenn Daten nur gegen Geld erhältlich sind, „lohnt“ sich die Entwicklung von Lösungen demzufolge nur, wenn diese Kosten z.B. durch den Verkauf des fertigen Produkts wieder gedeckt werden können. Dies bedeutet eine prohibitive Hürde für Lösungen, die sehr kleine, spezielle Zielgruppen ansprechen, und kein breites Publikum – beispielsweise Menschen mit Mobilitätseinschränkungen, die ohnehin an vielen Stellen im bisherigen Eisenbahnverkehr benachteiligt werden. Während viele Beitragende in der Open-Data-Bewegung willens sind, Personenarbeitsstunden in erheblichem Gegenwert für die Lösung von Problemen zu investieren, dürfte der Wille, für die nötigen Daten auch noch Geld zu bezahlen, keine weite Verbreitung haben.
Zudem leben viele (freie) Projekte vom Austausch –  beispielsweise, indem interessierte Nutzer_innen eines Programms Fehlerreporte oder sogar Bugfixes einreichen. Solch ein Austausch wäre unter unfreien Lizenzen nicht möglich, da die Beitragenden mangels eines eigenen API-Keys bzw. einer Nutzungslizenz keinen Zugriff auf die Datenquelle hätten.

Zudem sollte bedacht werden, dass es sich bei den bereitgestellten Daten in der Regel um Faktendaten handelt, deren _Nachnutzung_ (sobald sie einmal veröffentlicht sind) nicht eingeschränkt werden kann. So sind beispielsweise bei reinen Fahrplan- oder Lagedaten regelmäßig nicht die notwendigen Hürden für die Schöpfungshöhe nach dem Urheberrecht erfüllt (vgl. [Kapitel 2.6 des Abschlussbericht zum FoPS 70.825](https://fragdenstaat.de/anfrage/abschlussbericht-forschungsvorhaben-nr-70825-eigentums-und-nutzungsrechte-im-offentlichen-verkehr/82918/anhang/FoPS_70825_AbschlussbeNAME.pdf). Vor dem Hintergrund ist auch die immer noch übliche Praxis, auf dem Urheberrecht basierende Lizenzverträge wie CC BY oder DL-DE BY auf die Datensätze anzuwenden, enorm fragwürdig. ([siehe auch](http://simia.net/wiki/Free_data))


## Welchen Nutzen sehen Sie in den Daten für die OpenData Community?

Die Open-Data-Community könnte idealerweise auf einen verlässlichen Datenbestand zurückgreifen und ggf. sogar die Datenqualität des Anbieters verbessern. Viele interessante Daten sind bereits jetzt durch Interessierte per Crowdsourcing gesammelt worden und auf Plattformen wie Wikipedia, OpenStreetMap oder einschlägigen Foren (drehscheibe-online etc.) in verschiedenen Formaten und verschiedener Qualität verfügbar.

Durch eine offizielle Bereitstellung relevanter Daten würde dieser Datenbestand idealerweise 1.) größer, 2.) regelmäßiger und ggf. zuverlässiger aktualisiert. Gerade für Anwendungen, die über ein Prototypenstadius hinaus wachsen möchten, ist eine regelmäßig aktualisierte und verlässliche Datenquelle wichtig. Eine gute, offizielle Dokumentation, auf die verwiesen werden kann, erschließt die Nachnutzung der Daten zudem einer deutlich größeren Gemeine von Entwickler_innen.

Die Erfahrungen in der Zusammenarbeit mit Daten bereitstellenden Kommunen haben gezeigt, dass durch geeignete Feedbackprozesse oftmals auch die Datenqualität der veröffentlichenden Stelle verbessert werden konnte.

## Was macht die OpenData Community damit?

Das obliegt der Open-Data-Community, die eine heterogene Gruppe ist, und deren Verhalten nicht vorhergesagt werden kann ;)
Aufgrund des eher speziellen Themas ist nicht damit zu rechnen, dass eine Veröffentlichung von heute auf morgen einen überwältigenden Zustrom an Entwickler_innen mit mannigfaltigen Anwendungen mit sich bringen würde. Die Anwendung von Transitdaten hat sich jedoch als praktisches Beispiel für den Umgang mit offenen Daten in den Open Knowledge Labs, aber auch im Bereich der Hochschullehre etabliert. Es ist auch damit zu rechnen, dass es bereits viele Anbieter_innen bestehender Anwendungen und Apps gibt, die mit dem neuen Datenbestand den Funktionsumfang ihrer Anwendungen erweitern würden. Potenzielle Anwendungsgebiete wurden bereits vorher genannt.

Wie bereits beschrieben werden von den Aktiven in der Open-Data-Community häufig eigene Probleme gelöst, die sich im Alltag ergeben. Im Idealfall fördert die Bereitstellung offizieller Daten auch den Austausch zwischen verschiedenen Gruppen, wie dies bereits schon in anderen Kontexten passiert ist. Beispielsweise hat die Community zur schnellen und präzisen Aktualisierung von Stationsplänen beigetragen, nachdem die Berliner S-Bahn dazu übergegangen war, für ihre Bau- und Umsteigeinformationen die freie Weltkarte OpenStreetMap zu verwenden.


## Mit was könnte die OpenData Community nicht arbeiten, und warum nicht?

Die Community könnte grundsätzlich nicht mit „unfreien Daten“ arbeiten, d.h. allem mit proprietärer Lizenz, bei dem die Nachnutzung nicht einwandfrei gesichert ist. Auch NDAs, Service Level Agreements und ähnliche Vertragswerke schließen viele potenzielle Beitragende aus. Die Entwicklung von Lösungen in der Community basiert darauf, einen niederschwelligen Einstieg zu bieten, so dass alle* mit dem nötigen Know-How beitragen können. Jede Art rechtlicher Hürden, die nicht mit den einschlägigen freien Lizenzen vereinbar sind, stehen dem im Wege.

Weiter sind Daten problematisch, die in einem Format vorliegen, das nur mit proprietärer Software lesbar ist. Hierzu gehören z.B. Binärformate, oder Formate, die nur mit kommerzieller Software oder nur für bestimmte Betriebssysteme erhältlicher Software lesbar sind. Dies würde viele Freiwillige abhalten, sich mit den Daten zu beschäftigen.

Schwierig sind zudem Formate mit schlechter oder fehlender Dokumentation. Bisweilen werden zwar proprietäre Formate reverse-engineered – das bedeutet jedoch einen langwierigen Prozess, bei dem oft nicht gewährleistet werden kann, dass alle Eventualitäten abgedeckt sind.

Nicht zuletzt sollten Aktualisierungen von Datensätzen möglichst unverzüglich stattfinden. 


## Was sind die Tätigkeitsfelder der OpenData Community? An was wird sonst noch gearbeitet?

Die Community bearbeitet ein weites Feld an Problemen; in der Regel geht es darum, den eigenen Alltag oder den seiner Mitmenschen zu vereinfachen, oder politisches Handeln nachvollziehbar zu machen. Eine abschließende Aufzählung dürfte umfangreich werden; als Beispiel sei auf die [Projektübersicht der Open Knowledge Labs der OKF](http://codefor.de) verwiesen, das auf dem [Brigades-Programm von Code for America aus den USA](http://brigades.codeforamerica.org/) basiert.


## Evtl. weitere Sorgen, Ängste, Wünsche und Anregungen

 * Der Veröffentlichungsprozess bzw. der Zugriff auf die Daten sollte schnell und unbürokratisch sein, um möglichst vielen Interessierten zu Beiträgen zu animieren.
 * “Done is better than perfect”: Lieber eine noch-nicht-ganz-perfekte API bereitstellen, einen noch-nicht-supertollen-Datensatz, und dann kontinuierlich daran weiterverbessern. Lieber mehrfach in Häppchen liefern, als darauf zu warten, dass es „perfekt“ wird – und am Ende doch nichts passiert)
 * *Menschliche* Schnittstellen sollten klar definiert und erreichbar sein: Es sollte von außen klar sein, wer als Ansprechpartner_in fungieren kann, und diese Ansprechperson sollte auch erreichbar sein und auf Anfragen reagieren. Und sei es nur mit einem „geht gerade nicht“, und dann Updates, wenn sich etwas tut. Das bedeutet auch unternehmensinterne Kommunikationsverbesserung, damit diese menschliche Schnittstelle auch weiß, wen sie für Datensatz/Projekt/Idee XY ansprechen kann ;) Zeitnahe Antworten sind entscheidend – wenig ist frustrierender als eine spannende Idee, die letztlich auf der Halde landet, weil das Projekt unternehmensseitig nicht vorankommt bzw. kein Feedback kommt. Klare Ansprechpartner_innen können auch für zielgerichtetes Feedback dienen, wenn die Qualität der bereitgestellten Daten durch Input aus der Community verbessert werden kann.
 * Eine deutliche Kennzeichnung (Versionstand/Datum) in den jeweiligen Datensätzen wäre sehr hilfreich, um spätere Widerholung/Aktualisierung deutlich von früheren (veralteten Daten) abheben zu können.
 * eine *verständliche* Beschreibung der Daten, idealerweise samt einfach nachvollziehbarer Beispiele für die Anwendung, helfen beim Verständnis der Datenformate (Beispielabfragen, Erklärungen anhand eines konkreten Zuglaufs, etc.)

## Meta: Über dieses Dokument

Dieser Aufschrieb entstand kollaborativ durch Beitragende u.a. aus den Mailinglisten [open-data-nahverkehr](https://lists.okfn.org/pipermail/open-data-nahverkehr/) und [open-transport](https://lists.okfn.org/pipermail/open-transport/). Er steht, soweit möglich, unter einer [CC0-Lizenz](http://creativecommons.org/publicdomain/zero/1.0/)

> To the extent possible under law, the authors have waived all copyright and related or neighboring rights to EVU-Open-Data-FAQ. This work is published from: Deutschland.

### Changelog

 * 2015-04-20: Erste fixierte Version
 * 2020-07-16: Kleinere Ergaenzungen bei Datenformaten und Beispielen

### How to contribute

Dieser Text darf als lebendes Dokument verstanden werden. Sollten Änderungen erforderlich sein, dürfen gerne Pull Requests eingereicht werden.
