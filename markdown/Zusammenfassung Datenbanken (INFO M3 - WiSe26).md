# Zusammenfassung: Datenbanken (INFO M3 - WiSe26)

## Kapitel 1 - Einstig

**Eine Datenbank speichert Daten strukturiert, sodass Anwendungen sie abfragen, anzeigen und verändern können.** *Beispiel: Nutzerverwaltung, Büchereiverwaltung, …*

### Geschichte von Datenbanken

| Zeit             | Entwicklung         | Details                                                                             |
|------------------|---------------------|-------------------------------------------------------------------------------------|
| vor dem Computer | Karteikarten        | Analog auf Papier, jede Karte eine Info, Karten Sortierung ⇒ Struktur               |
| 1890             | Lochkarten          | Hollerith wertet die Volkszählung der USA mit Lochkarten und einer Zählmaschine aus |
| 1970             | Relationales Modell | Daten als Relationen, also Tabellen                                                 |
| 1974             | SEQUEL              | Entwicklung von SEQUEL als Vorgänger von SQL                                        |
| 1979             | Oracle V2           | Ein frühes kommerzielles Datenbanksystem mit SQL                                    |
| 1986             | SQL                 | SQL wird als Norm eingeführt                                                        |
| 2000             | SQLite              | SQLite, eine Datenbank, die vollständig in einer Datei gespeichert werden kann      |
| heute            | Überall             | Datenbanken besonders SQLite sind überall                                           |

**Wesentliche Entwicklung**: In relationalen Datenmodell werden Daten als Tabellen mit Zeilen und Spalten dargestellt. Dadurch entstand eine einheitliche Grundlage, um Daten strukturiert zu speichern und später mit SQL abzufragen.

### Aufbau einer (relationalen) Datenbank

Eine relationale Datenbank speichert Daten in **Tabellen (Relationen)**, die aus Zeilen und Spalten bestehen.

| Fachbegriff                       | Bedeutung                                          |
|-----------------------------------|----------------------------------------------------|
| **Relation**                      | Tabelle                                            |
| **Attribut**                      | Spalte einer Tabelle                               |
| **Tupel**                         | Zeile einer Tabelle                                |
| **Attributwert**                  | Einzelner Wert einer Zelle                         |
| **Schema**                        | Aufbau einer Tabelle mit Attributen und Datentypen |
| **Primärschlüssel (PRIMARY KEY)** | Identifiziert jeden Datensatz eindeutig            |
| **Fremdschlüssel (FOREIGN KEY)**  | Verweist auf einen Datensatz einer anderen Tabelle |

### Anomalien in Datenbanken

Anomalien entstehen, wenn Informationen in einer einzigen großen Tabelle mehrfach gespeichert werden (= **Redundanz**). Dadurch können beim Einfügen, Ändern oder Löschen von Daten Probleme auftreten.

#### 1. Änderungsanomalie

Dieselbe Information muss an mehreren Stellen geändert werden. Wird nur ein Teil angepasst, entstehen widersprüchliche Daten.

#### 2. Löschanomalie

Beim Löschen eines Datensatzes gehen unbeabsichtigt weitere Informationen verloren.

**Beispiel:** Wird die letzte Ausleihe eines Buches gelöscht welches zum 1. mal ausgeliehen wurde, verschwindet auch die einzige gespeicherte Information über das Buch.

#### 3. Einfügeanomalie

Neue Informationen können nicht unabhängig von anderen Informationen gespeichert werden, es entstehen Lücken.

#### Lösung: Verknüpfung mehrere Tabellen (Normalisierung)

Die große Tabelle wird in mehrere Tabellen aufgeteilt. Dadurch werden redundante Daten reduziert und die Anomalien vermieden.

Die Tabellen werden dabei über Schlüssel miteinander verknüpft:

- **Primärschlüssel:** Eindeutige Kennzeichnung eines Datensatzes.
- **Fremdschlüssel:** Verweis auf den Primärschlüssel einer anderen Tabelle.

*Beispiel Bücherei: Die große Tabelle `buecherei` wird in mehrere Tabellen aufgeteilt, z. B. `buch`, `person` und `ausleihe`. Diese werden über Primär- und Fremdschlüssel verknüpft.

### SQL: Reihenfolge

Die logische Ausführungsreihenfolge unterscheidet sich von der Schreibreihenfolge.

#### Logische Ausführungsreihenfolge

1. `FROM` – Tabelle auswählen
2. `WHERE` – Zeilen filtern
3. `GROUP BY` – Zeilen gruppieren
4. `SELECT` – Spalten auswählen und Berechnungen durchführen
5. `ORDER BY` – Ergebnis sortieren

#### Beispiel

```sql
SELECT genre, COUNT(*) AS anzahl
FROM ausleihliste
WHERE genre <> 'Klassiker'
GROUP BY genre
ORDER BY anzahl DESC;
```

### Tabellenkalkulation vs. Datenbank

#### Tabellenkalkulation

Geeignet für überschaubare Listen, einfache Berechnungen und einmalige Auswertungen.

**Beispiele:** WG-Haushaltskasse, kleine Umfragen.

#### Datenbank

Geeignet für große Datenmengen, zusammenhängende Daten und gleichzeitige Zugriffe mehrerer Personen.

**Beispiele:** Online-Shop, Schulverwaltung, Bücherei mit mehreren Standorten, Mensa-App.