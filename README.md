# Kreditdatenanalyse

## Inhaltsverzeichnis

- [Executive Summary (Kurzfassung)](#executive-summary-kurzfassung)  
- [Introduction & Objective (Einleitung & Zielsetzung)](#introduction--objective-einleitung--zielsetzung)  
- [Data Description (Datenbeschreibung)](#data-description-datenbeschreibung)  
- [Methodology (Methodik)](#methodology-methodik)  
- [Python Analysis (Python-Analyse)](#python-analysis-python-analyse)  
  - [Default Rate by Age Group (Ausfallquote nach Altersgruppe)](#default-rate-by-age-group-ausfallquote-nach-altersgruppe)  
  - [Employment Status Distribution (Verteilung nach Beschäftigungsstatus)](#employment-status-distribution-verteilung-nach-beschaeftigungsstatus)  
  - [Interest Rate vs Credit Score (Zinssatz vs. Bonität)](#interest-rate-vs-credit-score-zinssatz-vs-bonitaet)  
  - [Average Loan Amount by Purpose (Durchschnittliche Darlehenshöhe nach Zweck)](#average-loan-amount-by-purpose-durchschnittliche-darlehenshoehe-nach-zweck)  
- [R Analysis (R-Analyse)](#r-analysis-r-analyse)  
  - [Default Rate by Annual Income Band (Ausfallquote nach Einkommensstufe)](#default-rate-by-annual-income-band-ausfallquote-nach-einkommensstufe)  
  - [Default Rate by Credit Score Band (Ausfallquote nach Bonitätsband)](#default-rate-by-credit-score-band-ausfallquote-nach-bonitaetsband)  
  - [Default Rate by Education Level (Ausfallquote nach Bildungsniveau)](#default-rate-by-education-level-ausfallquote-nach-bildungsniveau)  
  - [Default Rate by Employment Status (Ausfallquote nach Beschäftigungsstatus)](#default-rate-by-employment-status-ausfallquote-nach-beschaeftigungsstatus)  
  - [Default Rate by Loan Purpose (Ausfallquote nach Darlehenszweck)](#default-rate-by-loan-purpose-ausfallquote-nach-darlehenszweck)  
- [Conclusions & Recommendations (Fazit & Empfehlungen)](#conclusions--recommendations-fazit--empfehlungen)  
- [Appendix (Anhang)](#appendix-anhang)  

---

## Executive Summary (Kurzfassung)

Die Analyse österreichischer Verbraucherkreditdaten zeigt, dass **Alter**, **Beschäftigungsstatus**, **Bonität**, **Einkommen** und **Darlehenszweck** die zentralen Treiber für die Ausfallquote sind. Kreditnehmer:innen im Kernalter (36–55) weisen dank stabiler Einkommensverhältnisse und etablierter Kreditverläufe die niedrigsten Ausfallquoten auf, während jüngere und ältere Kohorten aufgrund von Einkommensschwankungen bzw. fixen Pensionen erhöhten Risiken ausgesetzt sind. Vollzeitbeschäftigte und Pensionist:innen liegen unter dem Durchschnitt, Studierende und Teilzeitkräfte darüber. Die Bonität bleibt der stärkste Prädiktor: Die Ausfallquote sinkt von **8,1 %** („Poor“) auf **0 %** („Exceptional“), was sich in den risikobasierten Zinssätzen gemäß Basel III widerspiegelt. Niedrige Einkommensstufen (< € 24 000) fallen mit **4,4 %**, hohe Einkünfte (> € 60 000) mit **2,4 %** aus. Durch Immobilien besicherte Darlehen (Sanierung) sind risikoärmer als abschreibungsanfällige Finanzierung (Auto). Diese Erkenntnisse legen nahe, Underwriting und Pricing stringent an Profilen auszurichten: Bevorzugung von Bonität ≥ 700 und Einkommen > € 60 000, strengere Konditionen für Hochrisikogruppen.

---

## Introduction & Objective (Einleitung & Zielsetzung)

Dieser Bericht liefert eine deskriptive Analyse österreichischer Verbraucherkreditdaten, um demografische, finanzielle und zweckspezifische Einflussfaktoren auf das Ausfallrisiko zu identifizieren. Die Ziele sind:

1. Ermittlung der Segmente mit höheren bzw. niedrigeren Ausfallquoten.  
2. Kontextualisierung der Ergebnisse in Österreichs Wirtschafts-, Sozial- und Regulierungsumfeld.  
3. Ableitung praxisrelevanter Empfehlungen für Kreditinstitute zur Optimierung von Kreditrichtlinien, Zinspolitik und Risikomanagement.

---

## Data Description (Datenbeschreibung)

Der Datensatz umfasst anonymisierte Verbraucherkreditdaten österreichischer Institute:

- **Demografie:** Altersgruppe, Bildungsniveau, Beschäftigungsstatus  
- **Finanzen:** Einkommensstufe, Bonitätsband, Zinssatz, Darlehenshöhe  
- **Darlehenszweck:** Auto, Ausbildung, Möbel/Haushalt, Sanierung, Sonstiges  
- **Ergebnis:** Kreditausfall innerhalb von 12 Monaten (ja/nein)

Die Aggregation nach Kategorien gewährleistet Datenschutz und ermöglicht dennoch detaillierte Subgruppenanalysen.

---

## Methodology (Methodik)

- **Werkzeuge:**  
  - **Python** (pandas, Matplotlib, Seaborn) für explorative Analysen und interaktive Charts  
  - **R** (tidyverse, ggplot2) für feingliedrige Ausfallratenübersichten und mehrschichtige Visualisierungen  
- **Vorgehen:**  
  1. Berechnung der Ausfallquote je Kategorie  
  2. Erstellung grafischer Darstellungen zur Erkennung von Trends und Korrelationen  
  3. Einbettung der Erkenntnisse in Österreichs sozioökonomischen und regulatorischen Kontext  
- **Umfang:** Deskriptive Analyse ohne prädiktive Modellierung; Fokus auf Klarheit und Umsetzbarkeit.

---

## Python Analysis (Python-Analyse)

### Default Rate by Age Group (Ausfallquote nach Altersgruppe)

![Default Rate by Age Group](default_rate_by_age_group.png)

**Analyse**  
Die U-förmige Kurve signalisiert zwei Haupttreiber: Einkommensvolatilität bei jungen Kreditnehmer:innen (18–25) und fixe Pensionszahlungen bei älteren (66–75). Erstere kombinieren niedrige Einstiegsgehälter mit Studienverpflichtungen, letztere kämpfen mit steigenden Lebens­haltungs- und Gesundheitskosten.

**Österreichischer Kontext**  
Mit einer NEET-Quote von rund 12 % ist die junge Zielgruppe besonders exponiert. Pensionen in der Höhe von median € 25,8 k decken nicht immer alle Ausgaben ab, vor allem angesichts jüngster Inflationserhöhungen.

**Sub-Fazit**  
Kreditnehmer:innen im Alter von **36–55** gelten als sicherstes Segment; für < 26 Jährige und > 65 Jährige ist erhöhte Sorgfalt angebracht.

---

### Employment Status Distribution (Verteilung nach Beschäftigungsstatus)

![Employment Status Distribution](employment_status_pie.png)

**Analyse**  
Vollzeitbeschäftigte (55 % Portfolio) fallen mit **3,2 %** am seltensten aus. Studierende (5,1 %) erreichen **5,2 %**, Teilzeit und Arbeitslose liegen bei rund **4 %**, Selbstständige bei **3,4 %**.

**Österreichischer Kontext**  
Arbeitslosengeld und Pensionssystem puffern Einkommensschocks, doch Übergangsphasen können Zahlungslücken erzeugen. Das duale System stützt Selbstständige, jedoch bleiben KMU-Inhaber:innen konjunkturempfindlich.

**Sub-Fazit**  
Gängige Gruppen (Vollzeit, Pensionist:innen) sind risikoarm. Für Studierende, Teilzeitkräfte und Arbeitslose empfiehlt sich erweiterte Dokumentationspflicht bzw. Bürgschaft.

---

### Interest Rate vs Credit Score (Zinssatz vs. Bonität)

![Interest Rate vs. Credit Score](interest_vs_credit_score.png)

**Analyse**  
Ein starker negativer Zusammenhang bestätigt risikobasierte Preisbildung: Bonität < 580 → Zinssätze bis 15 %, Bonität ≥ 750 → 2–3 %. Die Ausfallquote fällt von 8,1 % auf 0 %.

**Österreichischer Kontext**  
KSV/CRIF liefern umfassende Scoring-Daten. Regulatorische Zinsobergrenzen nach EU-Recht begrenzen Usura, dennoch differenzieren Institute strikt nach Score-Bändern.

**Sub-Fazit**  
Die Bonität ist Haupthebel für Pricing und Kreditentscheidung. Automatisierte Prozesse sollten „Exceptional“ und „Very Good“ priorisieren, während „Poor“ und „Fair“ manuelle Prüfung bzw. zusätzliche Sicherheiten erfordern.

---

### Average Loan Amount by Purpose (Durchschnittliche Darlehenshöhe nach Zweck)

![Average Loan Amount by Purpose](loan_amount_by_purpose.png)

**Analyse**  
Autokredite: Ø € 21 000 – hohe Exposition durch Abschreibung. Sanierungsdarlehen: Ø € 15 000 – implizite Besicherung durch Immobilien. Ausbildung: Ø € 7 000 – staatliche Förderungen, moderates Risiko. Möbel/Haushalt und Sonstiges: Ø € 9 000–11 000, ungesicherte Konsumkredite.

**Österreichischer Kontext**  
54,5 % Eigentumsquote ermöglichen günstige Energieeffizienz-Sanierungsdarlehen. Fahrzeugfinanzierung korreliert mit Pendelbedürfnissen, erzeugt jedoch Volatilität.

**Sub-Fazit**  
Zweckabhängig variiert Darlehenshöhe und Collateral-Qualität. Sanierungsdarlehen rechtfertigen höhere Limits, Auto- und ungesicherte Kredite strengere Underwriting-Limits.

[💡 Python-Report ansehen](https://github.com/Dan103/Credit-Data-Analysis/blob/dd68f4f1668c9dab9b6f2bccefce564212432eda/Analysis.ipynb)

---

## R Analysis (R-Analyse)

### Default Rate by Annual Income Band (Ausfallquote nach Einkommensstufe)

![Default Rate by Annual Income Band](default_rate_by_annual_income_band.png)

**Analyse**  
Inverse Beziehung: 0–24 k → **4,4 %**, > 60 k → **2,4 %**. Geringverdienende verfügen über begrenzte Rücklagen und priorisieren oftmals Grundkosten.

**Österreichischer Kontext**  
Progressives Steuersystem und Sozialtransfers mildern Volatilität, doch < € 24 000 bleiben Einkommensengpässe – v. a. bei Alleinverdienern.

**Sub-Fazit**  
Einkommensstufe als zentrales Underwriting-Kriterium: Mindest­einkommen und skalierbare Kreditlimits senken das Risiko.

---

### Default Rate by Credit Score Band (Ausfallquote nach Bonitätsband)

![Default Rate by Credit Score Band](default_rate_by_credit_score_band.png)

**Analyse**  
Anstieg in kleinen Score-Schritten führt zu überproportionalem Rückgang der Ausfälle von 8,1 % (Poor) auf 0 % (Exceptional).

**Österreichischer Kontext**  
Auch kleine Darlehen werden an KSV/CRIF gemeldet, was Scoring-Genauigkeit erhöht und automatisierte Entscheidungen fördert.

**Sub-Fazit**  
Score-Bänder sollten direkt Kredit­richtlinien zugeordnet werden: Automatisierung für Good+, verstärkte Prüfung für Fair und Poor.

---

### Default Rate by Education Level (Ausfallquote nach Bildungsniveau)

![Default Rate by Education Level](default_rate_by_education.png)

**Analyse**  
Enge Bandbreite (3,3 %–3,5 %), marginal höhere Ausfälle bei Pflichtschulabschluss, was auf geringere Einkommenschancen rückschließen lässt.

**Österreichischer Kontext**  
Das duale System sorgt für hohe Beschäftigungsquoten across education levels, weshalb Bildungsniveau nur indirekten Einfluss auf Ausfälle hat.

**Sub-Fazit**  
Bildungsniveau liefert begrenzten Mehrwert für Risikobewertung; Fokus auf Finanz- und Bonitätskennzahlen bleibt zentral.

---

### Default Rate by Employment Status (Ausfallquote nach Beschäftigungsstatus)

![Default Rate by Employment Status](default_rate_by_employment_status.png)

**Analyse**  
Studierende: 5,2 %, Teilzeit: 4,0 %, Arbeitslose: 3,9 %, Vollzeit & Pensionist:innen: 3,2 %, Selbstständige: 3,4 %.

**Österreichischer Kontext**  
Arbeitslosengeld dämpft kurzfristig, doch Leistungsauszahlungen und Benefit-Ende erzeugen Zahlungslücken. Hohe Sozialversicherungsabgaben stabilisieren Einkommen von Angestellten.

**Sub-Fazit**  
Beschäftigungsstatus ist Schlüssel­dimension: Strikte Einkommensnachweise und Benefit-Dokumentation für non-standard borrowers erforderlich.

---

### Default Rate by Loan Purpose (Ausfallquote nach Darlehenszweck)

![Default Rate by Loan Purpose](default_rate_by_loan_purpose.png)

**Analyse**  
Autokredite: 3,9 %, Sanierung: 3,2 %, Sonstiges: 2,7 %. Höhere Ausfälle bei zweckbezogenen, ungesicherten Krediten.

**Österreichischer Kontext**  
Immobilienpreise steigen stabil, reduzieren LGD bei Sanierung. Fahrzeugfinanzierung bleibt anfällig für Abschreibung und variable Folgekosten.

**Sub-Fazit**  
Darlehenszweck muss Underwriting steuern: Collateralised Home Loans bevorzugen, Auto und Unsecured strengere Down-Payment-Anforderungen.

[💡 R-Report ansehen](https://dan103.github.io/Credit-Data-Analysis/Analysis.html)

---

## Fazit & Empfehlungen

- **Zusammenfassung:**  
  - **Demografie:** Alter 36–55, Vollzeit oder Pensionist:in, Einkommen > € 24 000, Bonität ≥ 700 → niedrigste Ausfallquoten.  
  - **Finanzkennzahlen:** Bonität und Einkommen sind stärkste Prädiktoren; Darlehenszweck und Collateral-Qualität verfeinern das Risikoprofil.  

- **Strategische Empfehlungen:**  
  1. **Risikobasierte Preisbildung:** Zinssätze streng an Bonität und Einkommen koppeln.  
  2. **Underwriting-Kontrollen:** Mindest­einkommen € 24 000, stabile Beschäftigungsnachweise, höhere Sicherheiten/Bürgschaften für Hochrisikogruppen.  
  3. **Produktgestaltung:** Kurzfristige, festverzinsliche Kredite für zins­empfindliche Kreditnehmer:innen.  
  4. **Monitoring & Bildung:** Frühwarnsysteme für Studierende und Teilzeitkräfte; gezielte Finanzbildungsangebote.  

- **Idealprofil:**  
  Alter 36–55,
  Vollzeitbeschäftigt,
  Einkommen > € 60 000,
  Bonität ≥ 700,
  Sanierungsdarlehen.  

- **Worst-Case-Profil:**  
  Alter < 26 oder > 65,
  Studierende/Teilzeit/Arbeitslose,
  Einkommen < € 24 000,
  Bonität < 600,
  hoher Autokredit.

---

## Appendix (Anhang)

- **Datenquellen:** Interne Bankdaten österreichischer Institute; KSV/CRIF.  
- **Repositories:**  
  - Python-Notebook: `Analysis.ipynb`  
  - R-Skripte: `Analysis.R`  
- **Zusatzmaterial:** Regionale Analysen, Laufzeitstudien, vollständiges Datenlexikon.  
