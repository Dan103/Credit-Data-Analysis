# Kreditdatenanalyse

## Inhaltsverzeichnis

- [Zusammenfassung](#zusammenfassung)  
- [Einleitung & Zielsetzung](#einleitung--zielsetzung)  
- [Datenbeschreibung](#datenbeschreibung)  
- [Methodik](#methodik)  
- [Python-Analyse](#python-analyse)  
  - [Ausfallquote nach Altersgruppe](#ausfallquote-nach-altersgruppe)  
  - [Verteilung nach Beschäftigungsstatus](#verteilung-nach-beschaeftigungsstatus)  
  - [Zinssatz vs. Bonität](#zinssatz-vs-bonitaet)  
  - [Durchschnittliche Darlehenshöhe nach Darlehenszweck](#durchschnittliche-darlehenshoehe-nach-darlehenszweck)  
- [R-Analyse](#r-analyse)  
  - [Ausfallquote nach Einkommensstufe](#ausfallquote-nach-einkommensstufe)  
  - [Ausfallquote nach Bonität](#ausfallquote-nach-bonitaet)  
  - [Ausfallquote nach Bildungsniveau](#ausfallquote-nach-bildungsniveau)  
  - [Ausfallquote nach Beschäftigungsstatus](#ausfallquote-nach-beschaeftigungsstatus-in-der-r-analyse)  
  - [Ausfallquote nach Darlehenszweck](#ausfallquote-nach-darlehenszweck-in-der-r-analyse)  
- [Fazit & Empfehlungen](#fazit--empfehlungen)  
- [Anhang](#anhang)  

---

## Zusammenfassung

Die Analyse österreichischer Verbraucherdaten zeigt, dass Kreditnehmer:innen im Alter von 36–55 Jahren die höchste Bonität aufweisen. Ihre stabilen Einkommensstufen und Rücklagen senken die Ausfallquote signifikant. Junge Kreditnehmer:innen (18–25) sind häufig teilzeitbeschäftigt oder beziehen Studienbeihilfen, was zu unregelmässigen Einnahmen und höheren Ausfallquoten führt. Pensionist:innen verlassen sich auf fixe Renteneinkünfte, die nicht immer alle Lebenshaltungskosten abdecken. Vollzeitbeschäftigte und Pensionist:innen profitieren von planbaren Zahlungsströmen, während Studierende und Teilzeitbeschäftigte höhere Ausfallquoten aufweisen.

Die Bonität ist der stärkste Indikator: Personen mit Scores unter 580 tragen hohe Zinskosten und ein erhöhtes Ausfallrisiko, während Kreditnehmer:innen mit Scores ≥ 750 minimale Zinssätze erhalten und nahezu nie ausfallen. Einkommensstufen zeigen, dass bis € 24 000 jährlich oft knappe Budgets herrschen, während über € 60 000 ein finanzielles Polster schafft. Sanierungsdarlehen (Renovierungsdarlehen) verzeichnen geringere Ausfälle durch Immobilienbesicherung, während Autokredite wegen Wertminderung risikoreicher sind. Kleinere Konsum- und Ausbildungskredite werden meist rasch getilgt, können jedoch bei Studienabbruch oder unerwarteten Ereignissen ausfallen.

---

## Einleitung & Zielsetzung

Dieser Bericht beleuchtet das Ausfallverhalten österreichischer Verbraucherkredite. Ziel ist es, anhand demografischer Merkmale, finanzieller Daten und Darlehenszwecken herauszufinden, welche Kundensegmente besonders risikoreich sind und welche Faktoren dahinterstecken. Die Erkenntnisse sollen österreichischen Kreditinstituten helfen, Kreditentscheidungen, Zinsstrategien und Portfoliomanagement zu optimieren.

---

## Datenbeschreibung

Die Daten umfassen anonymisierte Verbraucherkreditdaten österreichischer Institute mit:

- **Demografie:** Altersgruppen (18–25, 26–35, 36–45, 46–55, 56–65, 66–75), Bildungsniveau, Beschäftigungsstatus  
- **Finanzen:** Einkommensstufe (0–24 k, 24–60 k, 60 k+), Bonitätsband (Poor, Fair, Good, Very Good, Exceptional), Zinssatz, Darlehenshöhe  
- **Darlehenszweck:** Auto, Ausbildung, Möbel/Haushalt, Sanierung, Sonstiges  
- **Ergebnis:** Kreditausfall innerhalb von 12 Monaten (ja/nein)

Alle Daten sind in Kategorien zusammengefasst, um den Datenschutz zu gewährleisten und dennoch detaillierte Analysen zu ermöglichen.

---

## Methodik

1. **Datenaufbereitung:** Bereinigung und Kategorisierung in Python und R  
2. **Ausfallquoten:** Berechnung der Ausfallquote je Kategorie  
3. **Grafische Aufbereitung:** Darstellung mit Matplotlib/Seaborn (Python) und ggplot2 (R)  
4. **Kontextanalyse:** Einordnung in das österreichische Arbeits- und Kreditmarktumfeld

---

## Python-Analyse

### Ausfallquote nach Altersgruppe

![Ausfallquote nach Altersgruppe](images/default_rate_by_age_group.png)

Junge Kreditnehmer:innen (18–25) weisen die höchste Ausfallquote auf, da Studium und Teilzeitbeschäftigung oft nur unregelmässige Einnahmen sichern. Zwischen 26–35 sinkt die Quote, da Berufserfahrung und Doppelverdienerhaushalte Stabilität bringen. In der Altersgruppe 36–45 steigt sie leicht an, weil grössere Darlehen für Wohneigentum und Fahrzeuge aufgenommen werden. Die niedrigsten Ausfallquoten finden sich bei 46–55 und 56–65, wenn Schulden abgebaut und Rücklagen gebildet sind. Ab 66 Jahren steigen sie wieder, da Renten nicht alle Lebenshaltungskosten decken.

Zusätzlich spiegelt der Verlauf auch unterschiedliche familiäre Verpflichtungen wider: Jüngere haben meist weniger finanzielle Puffer, während in der Mitte des Lebens oftmals doppelte Einkommen in den Haushalt fließen. In der Altersgruppe 36–45 können einmalige Ausgaben – etwa für Kinderbetreuung oder Immobilienrenovierung – kurzzeitig zu Zahlungsschwierigkeiten führen. Das Tief bei 56–65 Jahren deutet auf verbesserte Haushaltsbudgets und reduzierte Kreditbelastung hin, da viele Hypotheken dann abbezahlt sind. Der erneute leichte Anstieg bei den über 66-Jährigen lässt sich auf Lebenshaltungs- und Gesundheitskosten zurückführen, die im Ruhestand schwerer zu kompensieren sind. Insgesamt zeigt sich, dass Lebenszyklus-Effekte und Vermögensaufbau eine zentrale Rolle für die Kreditstabilität spielen.

---

### Verteilung nach Beschäftigungsstatus

![Verteilung nach Beschäftigungsstatus](images/employment_status_pie.png)

Vollzeitbeschäftigte profitieren von regelmässigen Gehältern und Zusatzleistungen, was ihre Ausfallquote senkt. Pensionist:innen stützen sich auf planbare Rentenzahlungen und familiäre Unterstützung. Studierende verfügen über Studienbeihilfen und Nebenjobs, wodurch ihre Einnahmen schwanken. Teilzeit- und arbeitslose Kreditnehmer:innen sind auf begrenzte Leistungen angewiesen, die nicht dauerhaft Kredite bedienen. Selbstständige erleben Geschäftsschwankungen, was zu moderaten Ausfällen führt. Die Gruppe „Sonstiges“ umfasst oft abhängige Kreditnehmer:innen mit Bürgen.

Ergänzend zeigt sich, dass gerade Studierende in Semesterferien oder bei Studienabbrüchen in Liquiditätsengpässe geraten können. Arbeitslose haben häufig nur kurzfristigen Zugang zu Sozialleistungen, was Kredite anfälliger macht. Selbstständige können durch saisonale Geschäfte oder konjunkturelle Schwankungen unter Druck geraten – hier wäre eine genauere Branchenbetrachtung spannend. Bei Pensionist:innen spielen familiäre Transfers und Ersparnisse eine Rolle, die in dieser Gesamtbetrachtung nicht differenziert werden. Für Kreditgeber:innen lohnt es sich, neben dem Beschäftigungsstatus auch die Dauer der Anstellung und Einkommensstabilität mitzuberücksichtigen.

---

### Zinssatz vs. Bonität

![Zinssatz vs. Bonität](images/interest_vs_credit_score.png)

Kreditinstitute staffeln Zinssätze nach Bonität: Unter 580 zahlen Kreditnehmer:innen bis zu 15 %, um potenzielle Verluste abzudecken. Mit steigendem Score sinken die Zinsen deutlich; bei ≥ 750 liegen sie bei 2–3 % und die Ausfallquote ist minimal. Die meisten Kreditnehmer:innen befinden sich im mittleren Bonitätsbereich (580–700), weshalb Maßnahmen zur Score-Verbesserung essenziell sind.

Interessant ist, dass die Zinssatz-Spanne bei schlechtester Bonität nicht nur breit, sondern auch volatil ist – Kreditinstitute passen sie oft an aktuelle Risikoprognosen an. Ab einem Credit Score von etwa 650 fällt eine deutliche „Knackstelle“ auf, ab der Konditionen merklich günstiger werden. Diese Schwelle kann als Triggerpunkt für Score-Optimierungsprogramme dienen. Zudem korreliert ein niedriger Zinssatz nicht nur mit geringerer Ausfallwahrscheinlichkeit, sondern oft auch mit längeren Laufzeiten und höheren Darlehensbeträgen. Ein Vergleich der Effektivität von Score-Verbesserungsmaßnahmen in der Fair- vs. Good-Kategorie könnte weitere Erkenntnisse liefern.

---

### Durchschnittliche Darlehenshöhe nach Darlehenszweck

![Durchschnittliche Darlehenshöhe nach Darlehenszweck](images/loan_amount_by_purpose.png)

Autokredite führen zu den höchsten Durchschnittssummen (ca. € 21 000), da Fahrzeugkosten und Wertverluste das Risiko erhöhen. Sanierungsdarlehen liegen bei etwa € 15 000 und sind durch Immobilienwerte abgesichert. Möbel- und Haushaltskredite (rund € 9 000) bergen moderates Risiko, da die Sicherheiten weniger stabil sind. Ausbildungskredite (ca. € 7 000) sind kleiner und werden oft gefördert, können aber bei Studienabbruch ausfallen. Die Kategorie „Sonstiges“ deckt dringende Bedürfnisse ab, die meist prioritär bedient werden.

Darüber hinaus zeigen Konsumkredite für Möbel/Haushalt eine relativ homogene Verteilung um ihren Mittelwert – dies weist auf standardisierte Finanzierungsprodukte hin. Für Ausbildungsdarlehen sind Zinsnachlässe oder Teilstundungen während der Studienzeit gängige Instrumente, die den tatsächlichen Ausfall beeinflussen. Sanierungsdarlehen profitieren zudem von staatlichen Förderungen bei Energieeffizienz, was das Ausfallrisiko weiter senken kann. Autokredite dagegen sind stark von Restwertschätzungen abhängig – schrumpfende Wiederverkaufspreise erhöhen hier das Risiko. Eine segmentierte Analyse nach Fahrzeugart (Gebraucht vs. Neuwagen) könnte noch tiefergehende Risikomechanismen aufdecken.

[💡 Python-Bericht ansehen](https://github.com/Dan103/Credit-Data-Analysis/blob/dd68f4f1668c9dab9b6f2bccefce564212432eda/Analysis.ipynb)

---

## R-Analyse

### Ausfallquote nach Einkommensstufe

![Ausfallquote nach Einkommensstufe](images/default_rate_by_annual_income_band.png)

Niedrige Einkommensstufen (0–24 k) weisen die höchsten Ausfallquoten auf, da kaum Budgetspielraum für unerwartete Kosten besteht. In der mittleren Stufe (24–60 k) führen Familienausgaben und Hypotheken zu gelegentlichen Engpässen. Spitzenverdiener:innen (> 60 k) verfügen über Rücklagen und mehrere Einnahmequellen, was die Ausfallwahrscheinlichkeit minimiert.

Ergänzend fällt auf, dass in der mittleren Einkommensklasse eine stärkere Streuung der Ausfallquoten besteht – verheiratete Haushalte schneiden hier oft besser ab als Alleinverdiener:innen. Die niedrigen Einkommen sind vermehrt auf Teilzeit- oder Saisonarbeit angewiesen, wodurch Schwankungen im Cashflow entstehen. Hohe Einkommen haben nicht nur mehr Rücklagen, sondern auch bessere Zugangskonditionen zu Refinanzierungen. Gerade für untere Einkommensgruppen empfiehlt sich eine dynamische Tilgungsstruktur, um plötzliche Einkommenseinbrüche abzufedern. Zudem könnten flexiblere Kreditlinien mit automatischen Tilgungsanpassungen helfen, Ausfälle zu reduzieren.

---

### Ausfallquote nach Bonität

![Ausfallquote nach Bonität](images/default_rate_by_credit_score_band.png)

Die Ausfallquote sinkt von 8,1 % (Poor) auf 4,7 % (Fair) und weiter auf 2 % (Good). Sehr gute und ausgezeichnete Bonitätsklassen zeigen nahezu keine Ausfälle, was disziplinierte Rückzahlung und Vertrauen der Institute widerspiegelt.

Bemerkenswert ist, dass bereits der Sprung von „Fair“ zu „Good“ eine Verdopplung der Rückzahlungswahrscheinlichkeit darstellt. Bei „Very Good“ und „Exceptional“ ist die Datenbasis meist kleiner, aber die konsistent niedrigen Ausfallquoten sprechen für robuste Risikoprofile. Die Grenzen zwischen den Bands sind oft fließend, da Scores aus unterschiedlichen Scoringmodellen stammen können. Ein genauer Blick auf die Verteilung innerhalb eines Bands könnte helfen, subkategoriale Risikofaktoren aufzuspüren. Außerdem lohnt eine Untersuchung, ob Up- und Downgrades im Score über die Kreditlaufzeit hinweg mit Ausfällen korrelieren.

---

### Ausfallquote nach Bildungsniveau

![Ausfallquote nach Bildungsniveau](images/default_rate_by_education.png)

Kreditnehmer:innen mit Pflichtschulabschluss fallen etwas häufiger aus, da ihre Einkommenschancen eingeschränkt sind. Lehrabschluss- und AHS-Absolvent:innen profitieren vom dualen System und stabilen Gehältern. Universitätsabsolvent:innen zeigen ähnliche oder leicht bessere Werte, was die Effektivität der tertiären Bildung unterstreicht.

Zusätzlich deuten diese Unterschiede auf potenzielle Bildungsprogramme hin: Eine gezielte Finanzbildung für Pflichtschulabsolvent:innen könnte hier die Ausfallquote senken. Die geringe Differenz zwischen Lehre/AHS und Universität/FH spricht für einen insgesamt hohen Fachkräftebedarf. In der tertiären Gruppe spielt das Einkommen nach Studienfach eine Rolle: Absolvent:innen technischer Studiengänge haben tendenziell geringere Ausfallraten als Geisteswissenschaftler:innen. Eine Verbindung von Bildungsabschluss und Berufsbranche würde noch granularere Erkenntnisse liefern. Ferner könnten Banken Studierende gezielt mit Studienkrediten fördern und begleitend coachen.

---

### Ausfallquote nach Beschäftigungsstatus (R)

![Ausfallquote nach Beschäftigungsstatus](images/default_rate_by_employment_status.png)

Studierende und Teilzeitbeschäftigte haben die höchsten Ausfallrisiken, weil ihre Einnahmen unregelmässig sind. Arbeitslose sind auf staatliche Leistungen angewiesen, die nicht dauerhaft Kredite bedienen. Selbstständige genießen Einkommenspotenzial, leiden aber unter Marktschwankungen. Pensionist:innen und Festangestellte profitieren von festen Einnahmen und sozialen Netzen, was ihre Ausfälle reduziert.

Interessant ist, dass Studierende trotz geringer Kreditvolumen pro Person eine überproportionale Ausfallquote aufweisen. Teilzeitkräfte sind oft in Branchen wie Handel oder Gastronomie beschäftigt, die saisonalen Schwankungen unterliegen. Bei Arbeitslosen spielt die Dauer der Arbeitslosigkeit eine Rolle – Langzeitarbeitslose fallen häufiger aus als kurzzeitige. Selbstständige mit gut diversifizierten Einnahmequellen (z. B. Freelancer:innen mit mehreren Kunden) schneiden besser ab als Einzelunternehmer:innen. Eine branchenspezifische Risikobetrachtung könnte hier weiterführende Erkenntnisse liefern.

---

### Ausfallquote nach Darlehenszweck (R)

![Ausfallquote nach Darlehenszweck](images/default_rate_by_loan_purpose.png)

Autokredite liegen vorne, da Fahrzeuge schnell an Wert verlieren und Darlehenssummen hoch sind. Ausbildungskredite sind kleiner, aber riskant bei Studienabbruch. Möbel- und Haushaltskredite bergen mittleres Risiko, da Sicherheiten begrenzt sind. Sanierungsdarlehen werden durch Immobilienwerte gestützt, wodurch Ausfallquoten geringer ausfallen. Die Kategorie „Sonstiges“ deckt dringende Bedürfnisse ab, die meist prioritär bedient werden.

Ergänzend lässt sich sagen, dass Sanierungsdarlehen häufig mit staatlichen Subventionen kombiniert werden, was das Rückzahlungsprofil verbessert. Autokredite für Neuwagen sind weniger riskant als für Gebrauchtwagen, da Neuwagen teils Restwertgarantien bieten. Konsumkredite für Möbel werden oft in Ratenverträgen mit Handelspartnern abgewickelt, wodurch Banken indirekt Sicherheiten haben. Ausbildungskredite könnten durch income-share-agreements (Einkommensbeteiligungen) weiter abgesichert werden. Die „Sonstiges“-Kategorie sollte bei der Kreditprüfung genau betrachtet und ggf. weiter aufgeschlüsselt werden, um versteckte Risiken zu erkennen.

[💡 R-Bericht ansehen](https://dan103.github.io/Credit-Data-Analysis/Analysis.html)

---

## Fazit & Empfehlungen

**Idealprofil:**  
- Alter 36–55  
- Vollzeit oder Pensionist:in  
- Einkommen > € 60 000  
- Bonität ≥ 700  
- Sanierungsdarlehen

**Hochrisiko-Profil:**  
- Unter 26 oder über 65  
- Studierende, Teilzeit, arbeitslos  
- Einkommen < € 24 000  
- Bonität < 600  
- Autokredit oder unbesicherter Konsumkredit

**Empfehlungen:**  
1. Zinssätze eng an Bonität und Einkommensstufe koppeln  
2. Mindesteinkommen und Beschäftigungsnachweise einfordern; Bürgschaften für risikoreiche Gruppen  
3. Feste Zinssätze und kürzere Laufzeiten für Risikogruppen anbieten  
4. Frühwarnmodelle für Studierende, Teilzeitkräfte und Geringverdiener implementieren  
5. Finanzbildung in Schulen und Unternehmen stärken

---

## Anhang

- **Quellen:** Interne Bankdaten; KSV/CRIF  
- **Code:** Python (`Analysis.ipynb`), R (`Analysis.R`)  
- **Weiteres:** Regionale Auswertungen, Laufzeitanalysen, Datenlexikon  
