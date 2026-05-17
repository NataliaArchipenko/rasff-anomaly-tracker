# RASFF Anomaly Tracker

**Status:** 🟡 In Arbeit — wöchentliche Aktualisierung

Automatisierte ETL-Pipeline zur Erkennung statistischer Anomalien
in den Lebensmittelsicherheitsdaten des EU-Schnellwarnsystems (RASFF).

**Datenbasis:** [RASFF Window Portal](https://webgate.ec.europa.eu/rasff-window/portal/)
**Zeitraum:** 2000 – heute (wöchentlich aktualisiert)
**Sprache:** Python · SQL

---

## Projektziele

- [ ] ETL-Pipeline aufbauen: RASFF-Daten automatisch laden, bereinigen und in SQL speichern
- [ ] Anomalien erkennen: ungewöhnliche Häufungen nach Produktkategorie, Herkunftsland und Risikoart
- [ ] Ergebnisse visualisieren: nachvollziehbare Charts und Alert-Tabellen
- [ ] Projekt dokumentieren und auf GitHub veröffentlichen

**Leitfrage:** *Wo und wann treten statistisch auffällige Häufungen von Lebensmittelwarnungen auf —
und deuten diese auf ein systemisches Problem hin?*

---

## To-Do nach Phase

### Phase 1 — ETL-Pipeline (Wochen 1–4)

- [ ] **Woche 1** — Setup & Datenquelle erkunden
  - [ ] Repository anlegen, Ordnerstruktur erstellen
  - [ ] `requirements.txt` schreiben
  - [ ] RASFF-Datenstruktur analysieren (Felder, Formate, Qualität)
  - [ ] Erste manuelle Download-Tests

- [ ] **Woche 2** — ETL-Skript schreiben
  - [ ] RASFF-CSV-Download mit `requests` automatisieren
  - [ ] Rohdaten mit `pandas` bereinigen
  - [ ] Nullwerte, Duplikate und Datumsformate behandeln
  - [ ] Unit-Test für die Bereinigungslogik

- [ ] **Woche 3** — SQL-Datenbankschema designen
  - [ ] SQLite-Datenbank einrichten
  - [ ] Tabellen anlegen: `alerts`, `products`, `countries`, `hazards`
  - [ ] Primär- und Fremdschlüssel definieren
  - [ ] Schema in `schema.sql` dokumentieren

- [ ] **Woche 4** — Daten laden & erste Abfragen
  - [ ] Bereinigten DataFrame in SQLite laden
  - [ ] Erste SQL-Abfragen: Top-Produktkategorien, Top-Herkunftsländer, Alerts pro Jahr
  - [ ] Ergebnisse als Markdown-Tabelle in README eintragen

---

### Phase 2 — Anomalie-Erkennung (Wochen 5–8)

- [ ] **Woche 5** — Explorative Datenanalyse (EDA)
  - [ ] Zeitreihen pro Kategorie und Land plotten
  - [ ] Saisonale Muster identifizieren
  - [ ] Erste visuelle Ausreißer dokumentieren

- [ ] **Woche 6** — Statistische Methoden implementieren
  - [ ] Z-Score-Methode auf monatliche Alert-Häufigkeiten anwenden
  - [ ] IQR-Methode als Vergleich implementieren
  - [ ] Schwellenwerte definieren und begründen

- [ ] **Woche 7** — Machine-Learning-Methode
  - [ ] `Isolation Forest` (scikit-learn) auf multivariate Daten anwenden
  - [ ] Ergebnisse mit statistischen Methoden vergleichen
  - [ ] Falsch-Positive analysieren und Modell anpassen

- [ ] **Woche 8** — Ergebnisse zusammenführen
  - [ ] Anomalie-Tabelle in SQL speichern
  - [ ] Anomalien mit `plotly` visualisieren und markieren
  - [ ] Beispiel-Befund beschreiben: Produkt, Land, Zeitraum, Abweichung

---

### Phase 3 — Veröffentlichung (Wochen 9–12)

- [ ] **Woche 9–10** — Code-Qualität & Dokumentation
  - [ ] Code refaktorieren, Kommentare ergänzen
  - [ ] `README.md` mit Ergebnissen, Screenshots und Beispielabfragen aktualisieren
  - [ ] `CONTRIBUTING.md` anlegen

- [ ] **Woche 11** — GitHub & LinkedIn
  - [ ] Repository öffentlich schalten
  - [ ] LinkedIn-Post veröffentlichen
  - [ ] Projekt in GitHub-Profil pinnen

- [ ] **Woche 12** — Puffer & optionale Erweiterung
  - [ ] Streamlit-Dashboard (optional)
  - [ ] Automatisches wöchentliches Reporting per E-Mail (optional)
  - [ ] Weitere Datenquellen einbinden, z. B. EFSA-Daten (optional)

---

## Technologie-Stack

| Bereich | Tool |
|---|---|
| Sprache | Python 3.11+ |
| Datenverarbeitung | pandas, numpy |
| Datenbank | SQLite (lokal), optional PostgreSQL |
| Anomalie-Erkennung | scikit-learn, scipy |
| Visualisierung | plotly, matplotlib |
| Versionskontrolle | Git / GitHub |
| Datenbasis | RASFF Open Data (EU) |

---

## Projektstruktur

```
rasff-anomaly-tracker/
├── data/
│   ├── raw/          # heruntergeladene Rohdaten
│   └── processed/    # bereinigte Daten
├── db/
│   └── rasff.db      # SQLite-Datenbank
├── notebooks/        # explorative Analysen
├── src/
│   ├── etl.py        # Extraktion, Transformation, Laden
│   ├── detect.py     # Anomalie-Erkennung
│   └── visualize.py  # Charts und Reports
├── tests/
├── requirements.txt
├── schema.sql
└── README.md
```

---

## Erste Ergebnisse

*(wird nach Woche 4 befüllt)*

---

## Lizenz

MIT License — Daten: © Europäische Kommission (RASFF Open Data)
