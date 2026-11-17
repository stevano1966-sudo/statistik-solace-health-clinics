<!--
  Dateiname: README.md
  Projekt:   Portfolio-Statistik – Solace Health Clinics
  Ersteller: Milomir Stevanovic
  Version:   v01
  Änderungshistorie:
    v01 | 17.11.2026 | Erstfassung für das öffentliche GitHub-Repo (Inhalte aus Dokumentation_final.md übernommen)
-->

# Statistik-Analyse Solace Health Clinics

Abschlussprojekt im Modul Statistik der Weiterbildung **AI-Powered Data Analyst** (Masterschool / MSIT).
Fiktive Klinikkette mit vier Standorten, ein Quartal Besuchsdaten (1.209 Zeilen, 14 Spalten).
Ziel: Daten prüfen, Fragen der Betriebsleitung mit Hypothesentests beantworten und einen geplanten A/B-Test bewerten.

**Tools:** Python 3, Jupyter, pandas, NumPy, SciPy, Matplotlib

## Fragestellungen und Ergebnisse

| # | Frage | Methode | Ergebnis |
|---|---|---|---|
| 1 | Kann man den Daten trauen? | EDA, Fünf-Zahlen-Zusammenfassung, IQR-Ausreißerregel, fehlende Werte, Duplikate, Datentypen | Brauchbar mit dokumentierten Korrekturen: 9 exakte Duplikate entfernt, 14 auffällige Dauerwerte markiert (vermutlich Dezimalfehler), Kosten rechtsschief → Median berichten |
| 2 | Hält Downtown sein Versprechen „im Schnitt unter 15 Min. Wartezeit“? | Einseitiger Einstichproben-t-Test (α = 5 %) | Statistisch signifikant, H0 verworfen: im Schnitt 12,2 Min. (95-%-KI 11,41–12,95). Aber 28 % warten länger als 15 Min. |
| 3 | Wartet man in Riverside länger als in Downtown? | Zweiseitiger Welch-t-Test, Konfidenzintervall, Cohen's d, Gegenprobe mit Mann-Whitney-U und Permutationstest | Riverside wartet 8,6 Min. länger (95-%-KI 7,3–9,8), d = 1,04. Auch praktisch relevant (Mindestdifferenz 5 Min.) |
| 4 | Ist der geplante SMS-A/B-Test gültig? | Design-Review gegen sechs Voraussetzungen, Power-Analyse | Nicht durchführbar in dieser Form: Zuteilung nach Standort statt zufällig. Überarbeiteter Plan mit Randomisierung auf Patientenebene |

Weitere Befunde: Wartezeit und Zufriedenheit hängen mäßig negativ zusammen (r = −0,39); Termintyp und No-Show nur schwach (Cramérs V = 0,105, Chi-Quadrat-Test).

## Inhalt des Repos

```
01_EDA-Abschlussprojekt/
├── Solace_Health_Modulprojekt_final.ipynb               Notebook mit Code, Kommentaren und Ausgaben
├── Solace_Health_Modulprojekt_Dokumentation_final.md    Dokumentation (auf GitHub direkt lesbar)
├── Solace_Health_Clinics_Praesentation.pdf              Präsentation für die Betriebsleitung
├── solace_visits.csv                                    Datensatz
└── abbildungen/                                         Diagramme aus dem Notebook
```

**Einstieg:** Für einen schnellen Überblick die [Präsentation](01_EDA-Abschlussprojekt/Solace_Health_Clinics_Praesentation.pdf),
für die Details die [Dokumentation](01_EDA-Abschlussprojekt/Solace_Health_Modulprojekt_Dokumentation_final.md).

## Arbeitsweise

- Signifikanzniveau, Ausreißerregel und Testrichtung **vor** der Auswertung festgelegt
- Jede Zahl in den Texten wird im Notebook per `assert` gegen die Daten geprüft
- Entscheidungen im Daten-Audit mit Begründung und nicht gewählter Alternative protokolliert
- Aussagegrenzen offen benannt (z. B. zeigt der Test, *dass* Riverside langsamer ist, nicht *warum*)

## Notebook ausführen

```bash
pip install pandas numpy scipy matplotlib
jupyter notebook 01_EDA-Abschlussprojekt/Solace_Health_Modulprojekt_final.ipynb
```

Die CSV wird automatisch aus dem Ordner des Notebooks geladen.

---

**Milomir Stevanovic** · [LinkedIn](https://www.linkedin.com/in/milomir-stevanovi%C4%87-2734752ba/)
