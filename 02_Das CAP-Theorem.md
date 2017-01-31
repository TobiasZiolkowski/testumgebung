# 2. Grundlagen
In diesem Kapitel werden die Grundlagen beschrieben, die f�r das Verst�ndnis der sp�ter
folgenden Erkl�rung der konkreten Datenbank-Beispiele n�tig sind. Es wird das
CAP-Theorem beschrieben, als auch die Prinzipen ACID und BASE, die Datenbank-Typen
SQL und NoSQL, sowie die Eigenschaften der AP-Datenbanken im Allgemeinen.

## 2.1 Theoretische Datenbankkonzepte
Dieses Unterkapitel befasst sich mit theoretischen Konzepten von Datenbanken.
Es werden das CAP-Theorem, das ACID-Prinzip und das BASE-Prinzip erkl�rt.

### 2.1.1 Das CAP-Theorem
Das CAP-Theorem beschreibt laut [FHK17] den Ansatz, dass Datenbanken in
verteilten Datenbanksystemen lediglich zwei der drei Anforderungen Konsistenz,
Verf�gbarkeit und Ausfalltoleranz erf�llen k�nnen. Diese Theorie wurde 2000 von
Eric A. Brewer als Vermutung formuliert. Diese Vermutung konnte 2002 von
Gilbert und Nancy Lynch als das CAP-Theorem bewiesen werden und dient seit
dem als Basistechnologie f�r die meisten NoSQL-Systeme.

Der Name des Theorems ergibt sich durch die englischen Begriffe der
Eigenschaften, die im Folgenden n�her erkl�rt werden:

Die Consistency beschreibt in verteilten Systemen mit replizierten Daten die
Eigenschaft, dass nach Abschluss einer Transaktion auch alle Replikate des
manipulierten Datensatzes aktualisiert werden. Damit soll sichergestellt werden,
dass alle lesenden Zugriffe den aktuellen und gleichen Stand des Datensatzes
angezeigt bekommen.

Die Availability, oder Verf�gbarkeit, beschreibt dahingegen die Antwortzeiten
der Datenbank. Dies ist besonders f�r E-Commerce Plattformen wichtig. Je
langsamer eine Webseite zu bedienen ist, desto schneller suchen die Kunden
eine Alternative. Die Antwortzeit einer Webseite nimmt wesentlichen Einfluss
auf die Benutzbarkeit einer Webseite und somit auf die Zufriedenheit der 
Kunden. Wichtig ist hier Lastspitzen einzukalkulieren, sodass die Webseite
auch bei tempor�r gro�em Andrang annehmbare Antwortzeiten liefert.

Mit der Partition Tolerance ist die Ausfalltoleranz der Rechner- und Servernetze
gemeint. Das System muss also stabil weiterlaufen, auch wenn ein Server
geplant oder ungeplant ausf�llt. Ein geplanter Ausfall tritt ein, wenn eine Wartung
ansteht, oder ein Server aus Altersgr�nden aus dem Verbund extrahiert oder ein
neuer eingef�gt werden muss. Ungeplante Abst�rze treten dahingegen bei
technischen Defekten oder Softwarefehlern auf. Dar�ber hinaus muss auch der
Ausfall einer Kommunikationsverbindung verkraftet werden, ohne dass die
Anwender davon etwas mitbekommen. Eine L�sungsm�glichkeit daf�r ist, dass
die Daten repliziert auf verschiedenen Servern gespeichert werden.

Nachdem die Begrifflichkeiten gekl�rt wurden kann das Theorem n�her erl�utert
werden. Die folgende Abbildung dient dabei dem besseren Verst�ndnis:

![Die m�glichen drei Optionen des CAP-Theorems](https://github.com/achatzSWT/ostfalia_db_2016_hausarbeiten/blob/master/crdt/Bilder/CAP-Theorem.JPG)

Das CAP-Theorem sagt aus, dass in verteilten System die drei Anforderungen
nach Konsistenz, Verf�gbarkeit und Ausfalltoleranz nicht in G�nze vereinbar und
nur zwei von dreien erreichbar sind.

Es muss also f�r jede Anwendung individuell entschieden werden, ob sie als CA-.
CP- oder AP-Applikation realisiert wird. Hier gibt es wesentliche Unterschiede
zwischen relationalen und NoSQL-Datenbanken. W�hrend bei relationalen
Datenbanken die Konsistenz die wichtigste Anforderung ist, r�cken bei
NoSQL-Datenbanken die Verf�gbarkeit und sehr hohe Skalierbarkeit in den
Vordergrund. Dies ist in der obigen Abbildung veranschaulicht.

Bei RDBS wird die Konsistenz mittels des relationalen Transaktionskonzepts und
den ACID-Eigenschaften realisiert. Durch sehr leistungsf�hige und qualitativ
hochwertige Hardware sollen hier die Anforderungen nach Ausfalltoleranz und
Verf�gbarkeit erf�llt werden.
