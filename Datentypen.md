<!--

author:   
email:    
date:     
version:  
language: de
narrator: 
repository: 

comment:  

icon:     https://www.uni-kiel.de/ps/cgi-bin/logos/files/cau/norm-en/cau-norm-en-lilawhite-rgb.svg

link:     link: https://raw.githubusercontent.com/RDM4CAU/Intro-to-RDM/refs/heads/main/cau-style.css

-->

# Daten und Datentypen (S2)

## Lernziele

- Studierende können den Begriff Forschungsdaten erläutern.
- Studierende können typische Beispiel für Daten in der Ur- und Frühgeschichte benennen.
- Studierende können den Begriff Datentyp erläutern.
- Studierende können relevante Datentypen im archäologischen Kontext benennen und zuordnen. 
- Studierende können reflektieren und diskutieren, wie die Wahl des Datentyps spätere Datenbanknutzung, Abfragen und Analysen beeinflusst.

## Einstieg: Daten und Datentypen (ca. 10 min)

      {{0-1}}
***********************
>**Warm-up**: Notiert spontan ein oder mehrere Beispiele für „Daten“ in der Ur- und Frühgeschichte: https://www.oncoo.de/hd2d 

??[](https://www.oncoo.de/t/hd2d)

-> Die Sammlung wird im Plenum gemeinsam nach Ähnlichkeit aka Datentyp sortiert, Erinnerung an Definition "Forschungsdaten"

*****************************

      {{1}}
*******************************

>**Was ist denn jetzt ein Datentyp?**

>*Ein Datentyp ist eine Klassifikation von Daten, die **Wertebereiche für Daten** definiert. Grundlegende Datentypen sind zum Beispiel Ganzzahlen (Integer), Dezimalzahlen (Real oder Float), Zeichenketten (String) oder Boolean (wahr, falsch). Auch Mischformen und Zusammensetzungen sind möglich. Mit einem Datentyp sind bestimmte **Operationen vorgegeben**.* 
>
>[Glossar zur Lernzielmatrix FDM](https://liascript.github.io/course/?https://raw.githubusercontent.com/dini-ag-kim/fdm-lernziele/refs/heads/main/LZM-Glossar/LZM-FDM_V3_de_Glossar.md#17)


>Ein Datentyp ist eine systematische Klassifikation, die festlegt, welche Art von Daten in einem Attribut gespeichert werden können und welche Operationen damit ausgeführt werden dürfen. 
>
>Jeder Datentyp definiert:
>
>- den Wertebereich (welche Werte zulässig sind)
>- die erlaubten Operationen
>- die internen Speicherstrukturen
>- die Formatvorgaben
>
>[vgl. Forschungsdatenzentrum Archäologie & Altertumswissenschaften](https://ianus-fdz.de/it-empfehlungen/dateiformate/datenbanken/#datenbankmodelle)

**************************

## Alternativer Einstieg oder Vertiefung: Sort the Data (15-20 Min)

>**Aufgabe (Kleingruppen):**
>
>Sortiert die Schnipsel nach Datentyp.
>
>Diskutiert: Sind die Datentypen immer eindeutig zuweisbar? Welche Auswirkungen könnten durch die Auswahl eines bestimmten Datentys entstehen, wenn man diesen Datentyp in einer Datenbank nutzen will?
>
>Fasst Eure Ergebnisse kurz im Plenum zusammen.

---

**Durchführung**

Material: 15–20 „Datenschnipsel“ 

- analog auf Moderationskarten oder 
- digital, z. B. mit Miro -> [siehe Beispiel](https://miro.com/app/board/uXjVJEHg2Po=/?share_link_id=858947682348)


## Input: Relevante Datentypen (30 min)

**Nummerische Daten**

- INT (Integer)
- FLOAT
- DECIMAL (auch NUMERIC)

**Textuelle Daten**

- TEXT
- VARCHAR
- CHAR

**Räumliche Daten**

- GEOMETRY + Subtypen:

  - POINT – ein einzelner Ort (x, y)

  - LINESTRING – eine Linie (z. B. Weg, Fluss)

  - POLYGON – eine geschlossene Fläche (z. B. See, Grabungsfläche)

  - MULTIPOINT, MULTILINESTRING, MULTIPOLYGON – Gruppen dieser Objekte

  - GEOMETRYCOLLECTION – Sammlung verschiedener Geometrien

**Datum und Zeit**

- DATE
- TIME

**Multimediale Daten**

- BLOB (Binary Large Object)
- externe Repositorien


### Numerische Daten

Numerische Daten können in unterschiedlichen Datentypen gespeichert werden. Die Wahl eines Datentyps hat Auswirkungen auf Performance und Abfrage- bzw- Auswertungsmöglichkeiten.

| Datentyp      | INT (Integer)                                                                    | FLOAT (Floating Point)                                    | DECIMAL (auch NUMERIC)  |
| ------------- | -------------------------------------------------------------------------------- | --------------------------------------------------------- | ----------------------- |
| Bedeutung     | Ganzzahliger Datentyp (keine Nachkommastellen)                                   | Fließkommazahl (Gleitkommazahl) mit binärer Approximation | Dezimalzahl mit fester Genauigkeit und Skalierung (z. B. DECIMAL(8,4) 9999.9999                   |
| Speicherung   | Binär, feste Größe                                                               | Mantisse + Exponent, z. B. IEEE 754 Standard                                                      | Dezimal-basiert, oft als String oder BCD (Binary Coded Decimal).                    |
| Eigenschaften | schnell in Berechnungen, keine Rundungsfehler                                    | kann sehr große und sehr kleine Zahlen darstellen, aber: Rundungsfehler (0.1 kann nicht exakt binär gespeichert werden!)                                                      | exakt für Dezimalzahlen (kein Rundungsfehler wie bei FLOAT), langsamer als INT oder FLOAT                    |
| Beispielwerte | -12, 0, 4572                                                                     | 3.14159, 2.73                                                     | 123.45, 0.10, -9999.99                    |
| Einsatz       | IDs (Primärschlüssel in relationalen DBs), Zählungen (Stückzahlen, Anzahl Funde) | Messwerte, Berechnungen, Simulationen, wenn begrenzte Genauigkeit ok ist                                                      | normierte Maße, die exakt sein müssen (z. B. Gewicht mit 2 Nachkommastellen), überall dort, wo Rundungsfehler unzulässig sind                    |


**Kurz und bündig**:

- INT: „Zählt Dinge“ → klein, exakt, schnell, aber ohne Nachkommastellen
- FLOAT: „Misst Dinge“, kann Nachkommastellen → riesiger Wertebereich, aber mit Ungenauigkeit.
- DECIMAL: „Misst Dinge“, kann Nachkommastellen -> langsam, aber genau.

#### Quiz

>**Welcher Datentyp ist für die Angabe `12,3 cm` am besten geeignet?**
>
>- [[ ]] Integer
>- [[x]] Float
>- [[ ]] String
>- [[ ]] Point
>- [[ ]] Decimal

---

>**Welche Datentypen würdest Du jeweils zuweisen?**
>
>- [[String (Text)] [Integer (Ganzzahl)] [Float (Fließkommazahl)] [komplexer Datentyp]]
>- [    [ ]          [ ]           [X]             [ ]     ]  12,3 cm
>- [    [ ]          [X]           [ ]             [ ]     ]  Fundzahl 274
>- [    [ ]          [ ]           [ ]             [X]     ]  540 ± 30 BP
>- [    [ ]          [ ]           [X]             [ ]     ]  48 g



### Textuelle Daten

Auch textuelle Daten können in Datenbanken in verschiedenen Datentypen gespeichert werden:

| Datentyp     | CHAR(n)                                              | VARCHAR(n)                                           | TEXT                        |
|--------------|------------------------------------------------------|------------------------------------------------------|-----------------------------|
| Bedeutung    | Fester Texttyp mit genau `n` Zeichen                 | Variabler Texttyp mit max. `n` Zeichen               | Langer, unstrukturierter Text |
| Speicherung  | Immer exakt `n` Zeichen, kürzere Texte werden aufgefüllt (Padding mit Leerzeichen) | Nur tatsächliche Zeichen + Längeninformation         | Je nach DB-System in separaten Speicherbereichen |
| Eigenschaften| schnell bei fester Länge, vorhersehbar              | speichereffizient, flexibel                          | geeignet für sehr lange Inhalte (z. B. Beschreibungen), langsamer im Zugriff |
| Beispielwerte| 'JA', 'NEIN', 'OST'                                  | 'Keramikfragment', 'Bronzenadel'                     | 'In Grube 3 wurde ein vollständig erhaltenes Gefäß mit Rillenmuster gefunden...' |
| Einsatz      | Codes, Abkürzungen, standardisierte Einträge         | Namen, Bezeichnungen, Kommentare                     | Freitext, Beschreibungen, Texteingaben ohne Längenlimit |



**Kurz und bündig**:

Nutze CHAR(n), wenn:

- Alle Einträge gleich lang sind (z. B. ISO-Codes wie „DE“, „EN“).

- Performance bei vergleichbaren Zeichenketten wichtig ist.
\

Nutze VARCHAR(n), wenn:

- Die Texte unterschiedlich lang, aber nicht sehr lang sind.

- Du Platz sparen willst und Flexibilität brauchst.
\

Nutze TEXT, wenn:

- Du lange, freie Texte speichern willst (z. B. Grabungsdokumentationen).

- Kein festes Limit notwendig ist.

#### Quiz

**Welche Datentypen passen zu den folgenden Texten?**

[(CHAR[n])   [VARCHAR (n)]     [TEXT]]
[    (X)           ( )             ( )     ]  DE
[    ( )           (X)             ( )     ]  Bronzenadel mit Dreilappenknauf
[    ( )           ( )             (X)     ]  Beschreibung der Fundsituation in Grube 4: ...
[    ( )           (X)             ( )     ]  Keramikfragment, leicht beschädigt
[    ( )           (X)             ( )     ]  Meier, S. 24
[    (x)           ( )             ( )     ]  Nein
[    ( )           ( )             (x)     ]  Notiz: Funde wurden für eine weitere Analyse...


### Datentypen für Datum und Zeit

Auch Zeitangaben müssen in passenden Datentypen gespeichert werden. Diese erlauben nicht nur die Speicherung, sondern auch Datumsrechnungen (z. B. Differenzen, Sortierung, Zeitfilter).

| Datentyp   | DATE                            | TIME                           | TIMESTAMP                         |
|------------|----------------------------------|--------------------------------|-----------------------------------|
| Bedeutung  | Kalendertag (ohne Uhrzeit)      | Uhrzeit (ohne Datum)           | Kombination aus Datum & Uhrzeit   |
| Speicherung| Tage seit Referenzdatum         | Sekunden seit Mitternacht      | Sekunden seit Startzeitpunkt      |
| Eigenschaften | Ideal für historische Daten  | Sinnvoll bei Messwerten        | Für vollständige Zeitstempel      |
| Beispielwerte | `2025-09-23`                 | `14:30:00`                      | `2025-09-23 14:30:00`             |
| Einsatz    | Funddatum, Grabungsbeginn       | Messzeitpunkt                  | Änderungsdatum, Scans             |

---

**Kurz und bündig:**

DATE: Nur Kalenderdatum – ideal für historische Angaben oder Grabungstage.

TIME: Nur Uhrzeit – sinnvoll bei Messwerten ohne Datum.

TIMESTAMP: Datum + Uhrzeit – z. B. für digitale Funde oder Protokolle.

#### Quiz

> Welche Datentypen passen zu folgenden Angaben?

[(DATE)   [TIME]     [TIMESTAMP]]
[ (x)       ( )         ( )     ]  2023-05-17
[ ( )       (x)         ( )     ]  14:57:08
[ ( )       ( )         (x)     ]  2023-05-17 14:57:08
[ (x)       ( )         ( )     ]  Funddatum: 12.08.1984
[ ( )       ( )         (x)     ]  Geändert am: 2024-11-05 10:12:00


### Datentypen für räumliche Daten

Räumliche Daten werden verwendet, um Punkte oder Flächen im Raum zu beschreiben. Sie benötigen spezielle Datentypen, um Geometrie und Bezugssystem zu speichern.

| Datentyp   | POINT                           | LINESTRING                      | POLYGON                           |
|------------|----------------------------------|----------------------------------|-----------------------------------|
| Bedeutung  | Einzelpunkt (Koordinaten)       | Linie aus Punkten               | Geschlossene Fläche               |
| Speicherung| Koordinatenpaar (x, y)          | Liste von Punkten               | Punktfolge, Start = Ende          |
| Eigenschaften | Einfach, präzise             | Darstellung linearer Objekte    | Fläche mit Struktur               |
| Beispielwerte | `POINT(13.40 52.52)`         | `LINESTRING(1 1, 2 2, 3 3)`     | `POLYGON((0 0, 1 1, 1 0, 0 0))`   |
| Einsatz    | Fundstelle, GPS-Koordinaten     | Mauerverlauf, Profil            | Fläche der Grabung oder Befund    |


#### Quiz

> Welche räumlichen Datentypen passen zu folgenden Angaben?

[(POINT)   [LINESTRING]     [POLYGON]]
[ (x)         ( )               ( )     ]  GPS-Fundkoordinate
[ ( )         (x)               ( )     ]  Mauerverlauf
[ ( )         ( )               (x)     ]  Fläche der Grabung
[ (x)         ( )               ( )     ]  Messpunkt eines Sensors
[ ( )         (x)               ( )     ]  Verlauf eines Bachbetts
[ ( )         ( )               (x)     ]  Umriss eines Gebäudes


### Datentypen für multimediale Daten

| Datentyp   | BLOB (Binary Large Object)      | TEXT (Pfad/URL)                 | JSON-Metadaten                    |
|------------|----------------------------------|----------------------------------|-----------------------------------|
| Bedeutung  | Binärdaten direkt in DB         | Verweis auf Datei               | Beschreibung der Datei            |
| Speicherung| Als Bytes in DB                 | Pfad als Text                   | Strukturierter Text (JSON)        |
| Eigenschaften | Direkte Speicherung          | Einfache Verwaltung             | Flexibel, erweiterbar             |
| Beispielwerte | (Binärdaten eines Bildes)    | `/media/audio1.wav`             | `{"format":"jpg","größe":"2MB"}`  |
| Einsatz    | Bilder, Audios, Videos          | Dateipfade, Web-URLs            | Zusatzinfos zu Medien             |

---

#### Quiz

> Welche Speicherform passt zu den folgenden Medien?

[(BLOB)   [Pfad als TEXT]     [JSON-Metadaten]]
[ (x)         ( )                 ( )     ]  Direkt gespeichertes JPG-Foto
[ ( )         (x)                 ( )     ]  `/files/audio/fundbericht.wav`
[ ( )         ( )                 (x)     ]  `{"typ": "video", "dauer": "45s"}`
[ ( )         (x)                 ( )     ]  `https://medien.db/scan42.pdf`
[ (x)         ( )                 (x)     ]  Binärdaten + Beschreibung


### Komplexe archäologische Daten

Angaben wie „540 ± 30 BC“ sind mehrwertige, zusammengesetzte Informationen und lassen sich nicht direkt in einem einzelnen Standard-Datentyp wie INT oder DECIMAL speichern.

`540 ± 30 BP = unscharfe/unsichere Zeitangabe`, bestehend aus:

- Einem Schätzwert oder Mittelwert: 540
- Einer Unsicherheit/Toleranz: ±30
- Einer Zeitskala / Datierungsform: BC

---

>--> Speicherung Datenbanken via Zerlegung der Informationen in mehrere Spalten, z. B.:

<!-- data-type="none" -->
| Information | Datentyp | Beispiel            |
| ----------- | -------- | ------------------- |
| methode     | VARCHAR  | Dendro, Radiocarbon | 
| mittelwert  | INT      | 540                 |
| toleranz    | INT      | 30                  |
| mittelwert  | INT      | 540                 |
| einheit     | CHAR     | BC, AD, BP          |


## Übung

Klassifizieren Sie die Daten Ihrer eigenen Fallstudie und weisen Sie entsprechende Datentypen zu.

## Zusammenfassung

| **Datentyp** | **Beispiel**     | **Typisches Problem**                                 | **Folgen für Datenbanknutzung**                    | **Mögliche Lösung**                                              | 
| ------------ | ----------------------------------- | ----------------------------------------------------- | -------------------------------------------------- | ----------------------------------------------------------------- |
| Numerisch    | Länge: 12,3 cm                      | Rundungsfehler, falsches Zahlenformat                 | Berechnungen fehlerhaft, Verlust von Genauigkeit   | Einheit festlegen, `DECIMAL` statt `FLOAT`                        |
| Textuell     | „rotpolierte Keramik, Fragment …“   | Uneinheitliche Schreibweisen, Synonyme                | Keine eindeutige Abfrage, erschwerte Statistik     | Normdaten/Thesauri, kontrollierte Vokabulare                      |
| Räumlich     | Koordinate: 51.3401, 6.5723 (WGS84) | Unterschiedliche Referenzsysteme, unklare Genauigkeit | Funde nicht vergleichbar, GIS-Analysen unbrauchbar | Einheitliches CRS (z. B. WGS84), Genauigkeit dokumentieren        |
| Multimedial  | Foto: Grabungsprofil.jpg            | Dateigröße, fehlende Metadaten                        | Datei auffindbar, aber nicht kontextualisierbar    | Speicherung von Metadaten, externe Repositorien                   |
| „Komplex“   | Datierung: 500 ±30 BC         | Unschärfe, kein spezieller Datentyp zuweisbar                | Ohne strukturierte Trennung (z. B. in mittelwert, toleranz, einheit) ist keine verlässliche Auswertung möglich.         | Informationen in mehrer Spalten aufteilen |




