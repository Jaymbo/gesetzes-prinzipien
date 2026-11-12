# Implementierungsplan: Bürger-Beteiligungsplattform für Gesetzesvorhaben

> **Aufgabe:** Die 24 Pflichtpunkte (0–23) aus `00-gesetzes-prinzipien.md` auf das System selbst anwenden (Punkt 21 = detaillierter Implementierungsplan, Punkt 22 = offene Fragen, Punkt 23 = nächste Schritte).
>
> **Ziel:** Einführung in allen relevanten politischen Ebenen (Kommunen, Landesparlamente, Bundestag, EU-Parlament)
>
> **Status:** Version 2.0, zur Diskussion

---

## 0. Kernkonzept (Zusammenfassung)

| Aspekt | Beschreibung |
|--------|--------------|
| **Problem** | Aktuelle Gesetzgebung ist anfällig für Lobbyismus, Kurzfristdenken und Mehrheitsmissbrauch. Bürger haben zu wenig direkten Einfluss. |
| **Lösung** | Offene Beteiligungsplattform: Gesetzesvorhaben als Repositories, alle Bürger können Issues erstellen, Arbeitsgruppen verarbeiten Feedback strukturiert. |
| **Betroffene** | Alle Bürger (83 Mio. DE), besonders Minderheiten und zukünftige Generationen. |
| **Ziel** | Höhere Gesetzesqualität, mehr Legitimität, Minderheitenschutz, weniger Lobby-Einfluss. |
| **Alternativen** | Repräsentative Demokratie (Problem bleibt), direkte Demokratie (Populismus-Gefahr), Experten-Gremien (undemokratisch), Bürgerräte per Losverfahren (begrenzte Beteiligung). |
| **Kosten** | Einmalig ~4–10 Mio. €, laufend ~8–16 Mio. €/Jahr (DE). |
| **Dauer** | 2–3 Jahre bis voll implementiert (GitLab-Basis + Gesetzesänderungen + Piloten). |

**Executive Summary:**

> Dieses System behandelt Gesetzesvorhaben wie Software-Projekte: versioniert (Repos), transparent (Commits/Diffs), mit offener Feedback-Verfolgung (Issues). Alle verifizierten Bürger können über die GitLab-Instanz (Web-UI) Feedback geben – Login per Personalausweis-Verifizierung, wahlweise anonym sichtbar, mit Rate-Limits statt Blockierung. Arbeitsgruppen müssen Feedback strukturiert verarbeiten (Clustering, Zusammenfassung, Antwortpflicht) statt sich nur auf Lobbyisten und Berater zu stützen. Umsetzung schrittweise: erst Kommunen, dann Länder, zuletzt Bund/EU.

---

## 1. Warum wird es benötigt?

**Problem:**
- Aktuelle Gesetzgebung ist anfällig für Lobbyismus, Kurzfristdenken und Mehrheitsmissbrauch
- Bürger haben zu wenig direkten Einfluss auf Gesetzestexte
- Minderheiten werden überstimmt ohne Gehör
- Gesetze werden oft ohne umfassende Impact-Analyse beschlossen

**Betroffene:**
- Alle Bürger (direkt betroffen durch Gesetze)
- Besonders: Minderheiten, zukünftige Generationen
- Politik (muss Prozess ändern), Verwaltung (muss Prozess umsetzen)

**Wenn nichts getan wird:**
- Weiterhin schlechte Gesetze ohne breite Zustimmung
- Vertrauensverlust in Demokratie
- Lobbyismus dominiert Gesetzgebung

---

## 2. Was ist der aktuelle Stand?

**Bestehende Strukturen:**
- Grundgesetz (Art. 20, 38 – Demokratie-Prinzip)
- Gemeindeordnungen der Länder, Geschäftsordnungen von Bundestag und Landtagen
- EU-Verordnungen zu Bürgerbeteiligung
- E-Petitionssysteme (Bundestag, Landtage), Konsultationsportale

**Lücken:**
- Keine verpflichtende, strukturierte Bürgerbeteiligung vor Gesetzgebung
- Keine Antwortpflicht auf Bürger-Feedback
- Keine öffentliche Rückverfolgbarkeit, welches Feedback eingearbeitet wurde
- Petitionen laufen oft ins Leere (keine Pflicht zur Reaktion)

**Stand der Technik/Wissenschaft:**
- **Decidim/Consul**: Open-Source-Beteiligungsplattformen, produktiv im Einsatz (Barcelona, Madrid)
- **vTaiwan**: Online-Deliberation mit Pol.is-Clustering – Vorbild für Cluster-Ansatz
- **GitLab/GitHub-Workflows**: Issues, PRs, Versionierung erprobt für Massen-Kollaboration
- **eID/BundID**: Verifizierungs-Infrastruktur existiert in DE bereits

---

## 3. Welche Alternativen gibt es?

| Alternative | Beschreibung | Vor- und Nachteile |
|-------------|--------------|-------------------|
| **A: Nichts tun** | Repräsentative Demokratie ohne Ergänzung | ✅ Einfach<br>❌ Probleme bleiben |
| **B: Direkte Demokratie** | Alle Gesetze per Referendum | ✅ Bürger entscheiden direkt<br>❌ Populismus-Gefahr, zu aufwändig |
| **C: Experten-Gremien** | Nur Fachleute entscheiden | ✅ Fachlich fundiert<br>❌ Elitär, undemokratisch |
| **D: Bürgerräte per Los** | Zufällig ausgeloste Gremien | ✅ Repräsentativ, erprobt (Irland, Frankreich)<br>❌ Nur ~800 Beteiligte, keine dauerhafte Beteiligung, hoher Koordinationsaufwand |
| **E: Offene Beteiligungsplattform (dieser Vorschlag)** | Alle Bürger können Issues erstellen | ✅ Universelle Teilhabe, dauerhaft, skalierbar<br>⚠️ Flut-Schutz nötig, Beteiligungsheterogenität |

**Warum Alternative E besser ist:**
- Universelle Teilhabe statt Auswahl von 800 Personen
- Dauerhafte Infrastruktur statt einmaliger Gremien
- Minderheiten kommen automatisch zu Wort (nicht nur wenn ausgelost)
- Feedback ist versioniert und nachvollziehbar (Git-Prinzip)
- Evidenzbasiert: Decidim, vTaiwan, Open-Source-Kollaboration erprobt

---

## 4. Vergleich zu Ähnlichem und Entferntem ziehen

**Andere Länder/Plattformen:**
| Land/Projekt | System | Erfahrungen |
|--------------|--------|-------------|
| **Taiwan** | vTaiwan + Pol.is | Massen-Deliberation mit Clustering, erfolgreiche Gesetzgebung (Uber-Regulierung) |
| **Spanien** | Decide Madrid (Consul) | Über 1 Mio. Nutzer, 27.000+ Vorschläge, teils umgesetzt |
| **Estland** | e-Residency, eID | Verifizierungs-Infrastruktur etabliert, hohe Digitalisierung |
| **Island** | Better Reykjavik | Bürgervorschläge in Stadtpolitik, dauerhafter Betrieb |
| **Deutschland** | E-Petitionen Bundestag | 50.000+ Unterschriften möglich, aber keine Antwortpflicht auf Inhalte |

**Verwandte Bereiche:**
- **Open Source Software**: Issues, PRs, Code-Review vor Merge – erprobt für Massen-Kollaboration
- **Wissenschaft**: Peer-Review vor Publikation – Qualitätsstandard
- **Wikipedia**: Massen-Kollaboration mit Verhaltensregeln + Moderation

---

## 5. Welche Positionen gibt es dazu?

### ⚠️ Die Macht-Frage: Warum sollten Politiker zustimmen?

**Harte Realität:**
- Politiker geben **nicht freiwillig** Macht ab
- Lobbyisten haben **Milliarden** in Einfluss investiert
- 2/3-Mehrheit für Grundgesetzänderung = **fast unmöglich** ohne Druck

**Das Korruptions-Problem:**

| Problem | Ausmaß | Beispiel |
|---------|--------|----------|
| **Parteispenden** | ~200 Mio. €/Jahr | Konzerne spenden an Regierungsparteien |
| **Nebenjobs** | ~30% der Abgeordneten | Aufsichtsräte, Beraterverträge |
| **Drehtür-Effekt** | ~50 Fälle/Jahr | Minister → Lobby → Minister |
| **Informelle Treffen** | Nicht dokumentiert | "Abendessen" mit Lobbyisten |

**Fazit:** Ohne **MASSIVEN Bürger-Druck** wird es nicht passieren.

### Detaillierte Stakeholder-Analyse

| Stakeholder | Untergruppen | Interesse | Gewinn/Verlust | Wahrscheinlichkeit |
|-------------|--------------|-----------|----------------|-------------------|
| **Bürger (allgemein)** | Desinteressierte (40%) | Keine Veränderung | ⚠️ Neutral | ❌ Keine Teilnahme |
| | Engagierte (30%) | Mehr Einfluss | ✅ Gewinnen | ✅✅✅ Stark dafür |
| | Frustrierte (30%) | System ändern | ✅✅ Gewinnen | ✅✅ Dafür |
| **Minderheiten** | Ethnische | Schutz vor Diskriminierung | ✅✅ Gewinnen | ✅✅✅ Stark dafür |
| | Soziale | Umverteilung | ⚠️ Unsicher | ⚠️ Abhängig vom Gesetz |
| | Zukünftige Gen. | Langfristdenken | ✅✅ Gewinnen | ❌ Keine Stimme (noch) |
| **Politiker (etabliert)** | Karriere-Politiker | Macht erhalten | ❌❌ Verlieren | ❌❌❌ Dagegen |
| | Idealisten | Bessere Politik | ⚠️ Ambivalent | ⚠️ Teilweise dafür |
| | Junge Politiker | Zukunft gestalten | ✅ Gewinnen | ✅✅ Dafür |
| **Lobbyisten** | Konzerne | Einfluss behalten | ❌❌ Verlieren | ❌❌❌ Dagegen |
| | NGOs | Strukt. Beteiligung | ✅ Gewinnen | ✅✅✅ Stark dafür |
| | Gewerkschaften | Arbeiter vertreten | ⚠️ Unsicher | ⚠️ Abhängig |
| **Verwaltung** | Beamte | Planbarkeit | ⚠️ Neutral | ⚠️ Neutral |
| | Politiker-Stab | Einfluss | ❌ Verlieren | ❌ Dagegen |
| **Medien** | Öffentlich-Rechtliche | Transparenz | ✅ Gewinnen | ✅ Dafür |
| | Private Medien | Klicks/Quoten | ⚠️ Ambivalent | ⚠️ Abhängig |
| **Tech-Community** | Open Source | Transparente Systeme | ✅✅ Gewinnen | ✅✅✅ Stark dafür |
| | Plattform-Betreiber | Marktanteil | ⚠️ Ambivalent | ⚠️ Abhängig |
| **Jugendliche** | 14–18 Jahre | Frühe Beteiligung | ✅✅ Gewinnen | ✅✅✅ Stark dafür |
| | 18–25 Jahre | Zukunft gestalten | ✅✅ Gewinnen | ✅✅✅ Stark dafür |

---

## 6. Wie werden diese Positionen angesprochen?

**Kernstrategie:**
- **Bürger:** Aufklärung + niedrige Hürden (GitLab-Issues, Lese-Zugang ohne Account) + sichtbare Erfolge (Issues, die etwas bewirkt haben)
- **Politiker:** Druck + Anreize (Wählerdruck, junge Politiker, entlastete Gesetzesarbeit durch strukturiertes Feedback)
- **Lobbyisten:** Macht begrenzen + Transparenz erzwingen (Sponsoren-Offenlegung der Arbeitsgruppen)
- **Medien:** Multiplikatoren nutzen (ÖR, lokal, Social Media) – öffentliche Issue-Statistiken als Datenquelle
- **NGOs & Tech-Community:** Koalition bilden (Decidim/Consul-Community, Chaos Computer Club für Audits)
- **Jugendliche:** Schul-Projekte + altersgerechter Zugang (ab 14)

---

## 7. Kosten / Dauer

**Implementierungskosten:**

| Posten | Einmalig | Laufend (pro Jahr) |
|--------|----------|-------------------|
| **GitLab-Instanz + eID-Anbindung** | 0,5–1,5 Mio. € | 0,5–1 Mio. € |
| **Gesetzesänderungen** | 0,5–1 Mio. € | – |
| **Schulung Verwaltung** | 2–5 Mio. € | 0,5 Mio. € |
| **Bürolektoren (Cluster-Prüfung)** | – | 3–8 Mio. € |
| **LLM-Betrieb (souverän, gehostet)** | – | 2–4 Mio. € |
| **Öffentlichkeitsarbeit** | 1–2 Mio. € | 0,5 Mio. € |
| **Security-Audits + Bug-Bounty** | – | 1 Mio. € |
| **Evaluation** | – | 0,5 Mio. € |
| **Gesamt** | **~4–10 Mio. €** | **~8–16 Mio. €** |

**Zeitrahmen:** 2–3 Jahre bis voll implementiert (GitLab-Basis spart 12+ Monate Entwicklung)

*Hinweis: Deutlich günstiger als ursprünglich geschätzt, weil keine Custom-App gebaut wird – GitLab-Standard + eID-Anbindung statt Eigenentwicklung. Größter Kostenblock bleibt der Flut-Schutz (Lektoren + LLM).*

*Hinweis: Günstiger als ein Bürgerrat-System mit Gremien (keine Sitzungs-/Reisekosten für 800+ Personen), dafür höhere Plattform-Kosten.*

---

## 8. Was ist der Weg dorthin?

| Phase | Dauer | Meilensteine | Verantwortlich |
|-------|-------|--------------|----------------|
| **1. Vorbereitung** | 6 Monate | Plattform-Spezifikation, Gesetzentwurf, Koalitionssuche | Initiatoren + NGOs |
| **2. Plattform-Einrichtung** | 6–12 Monate | GitLab-Instanz aufsetzen + eID-Anbindung + Account-Verwaltung, Security Audits, Beta-Testing | Tech-Team + Auditors |
| **3. Pilot (Kommunen)** | 12 Monate | 10–20 Kommunen opt-in, erste Vorhaben mit Issue-Verarbeitung, Evaluation | Pilot-Kommunen |
| **4. Landes-Ebene** | 12 Monate | 2–3 Bundesländer opt-in, Anpassung basierend auf Pilot | Landesparlamente |
| **5. Bundes-Ebene** | 12 Monate | Bundesweites Rollout, Antwortpflicht gesetzlich verankern | Bundestag + Bundesrat |
| **6. EU-Ebene** | 24 Monate | EU-Richtlinie, Mitgliedstaaten implementieren | EU-Parlament + Kommission |

---

## 9. So kompliziert wie nötig, so einfach wie möglich

| Element | Begründung der Komplexität |
|---------|---------------------------|
| **20 Pflichtfragen** | Notwendig für umfassende Prüfung |
| **Clustering + LLM-Zusammenfassung** | Ohne Flut-Schutz wäre Feedback unbrauchbar |
| **Rate-Limits statt Bans** | Einfachster Schutz gegen Flooding ohne Ausschluss |
| **Verifizierung + optionale Anonymität** | Kompromiss: Missbrauchsschutz ohne Vergeltungsrisiko |
| **Nutzer-einstellbarer Feed** | Entfällt – GitLab-Standard-Sortierung statt Custom-Feed |

**Vereinfachungen vorgenommen:**
- ❌ ~~Losverfahren + Bürgerrat-Gremien~~ → ✅ Direkte offene Beteiligung
- ❌ ~~Expertenrat als eigenes Gremium~~ → ✅ Fachliches Feedback kommt als normale Issues
- ❌ ~~Durchrotations-Protokolle~~ → ✅ Git-Historie dokumentiert alles automatisch
- ❌ ~~Custom-App mit Feed-Algorithmus~~ → ✅ GitLab-Standard-Oberfläche, keine eigene Entwicklung

---

## 10. Existierendes anpassen, bevor drauf/dazu gebaut wird

| Bestehend | Anpassung |
|-----------|-----------|
| **Decidim/Consul** | Nur als Referenz für Beteiligungs-Workflows (nicht als Basis) |
| **BundID/eID** | Verifizierungs-Backend (Login per Personalausweis) |
| **E-Petitionssystem Bundestag** | Migration oder Anbindung (offene Frage, siehe 22) |
| **GitLab-CE** | Plattform-Basis: Issues, MRs, Versionierung, rollenbasierte Rechte |
| **Pol.is / LLM-Clustering** | Semantische Gruppierung von Feedback |
| **Wahlregister** | Verifizierungs-Referenz (nur Hash) |
| **Volkshochschulen** | Schulungen + Terminals für Nicht-Smartphone-Nutzer |

---

## 11. Langlebigkeit / langfristig / Nachhaltigkeit

- **Dauerhaft** (wie Grundgesetz) – Plattform als dauerhafte Infrastruktur
- Evaluationsklausel alle 5 Jahre
- Technologie-neutral formuliert (Oberfläche kann sich ändern, Prinzipien bleiben)
- Rate-Limits und Cluster-Schwellen anpassbar

---

## 12. Wartbarkeit / Anpassbarkeit

| Element | Anpassungsmechanismus |
|---------|----------------------|
| **Rate-Limits** | Verordnung (anpassbar nach Pilot-Daten) |
| **Cluster-Schwelle** | Verordnung (dynamisch konfigurierbar) |
| **Plattform** | Open Source (Community-Updates, Forks möglich) |
| **24 Punkte** | Grundgesetzänderung (2/3-Mehrheit) |
| **Feed-Algorithmus** | Entfällt – GitLab hat keinen Feed-Algorithmus; Chronologisch/Labels/Votes sind Standard, nichts zu tunen |
| **Moderationsregeln** | Eigenes Regel-Repositorium mit öffentlicher Beteiligung |

**Review-Zyklus:** Alle 5 Jahre Evaluation durch unabhängige Kommission

---

## 13. Entsorgung einplanen

**Aufhebungs-Bedingungen:**
- 2/3-Mehrheit im Parlament
- ODER: Volksentscheid mit 51% Zustimmung
- ODER: Systematisches Scheitern (Fehlschlag-Kriterien, siehe Punkt 16)

**Rückbau:** Plattform-Code bleibt als Open Source erhalten; Daten exportierbar (Export-Pflicht); keine andauernden Verpflichtungen für Bürger.

---

## 14. Was verändert sich dadurch?

**Impact-Analyse:**

| Bereich | Direkter Effekt | Indirekter Effekt |
|---------|-----------------|-------------------|
| **Gesetzgebung** | Langsamer, aber besser | Höhere Akzeptanz |
| **Politiker** | Weniger Kontrolle | Mehr Legitimität |
| **Lobbyisten** | Weniger Einfluss | Müssen öffentlich argumentieren |
| **Bürger** | Mehr Einfluss, dauerhaft | Höheres politisches Interesse |
| **Minderheiten** | Besser geschützt | Weniger Diskriminierung |
| **Verwaltung** | Mehr Feedback zu verarbeiten | Neu-Organisation der Anhörungen |

**Second-Order Effects:**
- ✅ Höheres Vertrauen in Demokratie
- ✅ Weniger Populismus (Feedback ist argumentbasiert)
- ✅ Politische Bildung durch Teilnahme
- ⚠️ Anfangs Widerstand von etablierten Politikern
- ⚠️ Sehr hohe Feedbackmengen in den ersten Monaten (Hype-Effekt)

---

## 15. Robustheit / Lücken

**Gegen welche Szenarien robust?**

| Szenario | Robust? | Begründung |
|----------|---------|------------|
| **Lobby-Versuchung** | ✅ Ja | Pflicht-Dokumentation, öffentliche Cluster |
| **Bot-Farmen / Sniping** | ✅ Ja | Verifizierung + Rate-Limits + Anomalie-Erkennung |
| **Feed-Manipulation** | ✅ Ja | Kein Feed-Algorithmus (GitLab-Standard-Sortierung) – nichts zu manipulieren |
| **Überschwemmung der Arbeitsgruppen** | ✅ Ja | Clustering + Zusammenfassung + Antwortpflicht nur über Schwelle |
| **Technische Manipulation** | ✅ Ja | Open Source + Audits + Export-Pflicht |
| **Krise (Pandemie)** | ✅ Ja | Online-nativ |

**Schlupflöcher:**
- ❗ Definition "Bürger" (Alter, Staatsbürgerschaft, Wohnsitz?)
- ❗ Kampagnen mit vielen *echten* Verifizierten (z.B. religiöse Gruppen) – legale Koordination
- ❗ Digitale Spaltung ohne Terminals
- ❗ LLM-Zusammenfassung könnte systematisch verzerren (Bias im Modell)

---

## 16. Messmetrik: Was bedeutet Erfolg? Was Fehlschlag?

**KPIs für Erfolg:**

| Metrik | Zielwert | Messzeitpunkt |
|--------|----------|---------------|
| **Registrierung** | >10% der Berechtigten im Jahr 1 | Jährlich |
| **Aktive Beteiligung** | >2% erstellen regelmäßig Feedback | Quartalsweise |
| **Zufriedenheit** | >70% finden Prozess fair | Jährlich |
| **Antwort-Quote** | 100% der Cluster über Schwelle beantwortet | Pro Vorhaben |
| **Feedback → Änderung** | >20% der Cluster führen zu Commit | Pro Vorhaben |
| **Minderheiten-Schutz** | >80% fühlen sich gehört | Jährlich |
| **Lobby-Einfluss** | <10% vermuten Einfluss | Jährlich |
| **Plattform-Sicherheit** | 0 erfolgreiche Angriffe | Kontinuierlich |

**Fehlschlag-Kriterien:**
- ❌ Registrierung <3% nach 2 Jahren
- ❌ Antwort-Quote <90% (Cluster werden ignoriert)
- ❌ Nachweisliche Manipulation von Clustering oder Account-Verifizierung
- ❌ Gesetzesvorhaben dauern >2x länger ohne Qualitätsvorteil

---

## 17. Was passiert, wenn es nicht klappt?

**Exit-Strategie:**

| Szenario | Maßnahme |
|----------|----------|
| **Zu wenig Beteiligung** | Öffentlichkeitskampagne + Zugang vereinfachen + Erfolgs-Storys |
| **Flut nicht beherrschbar** | Cluster-Schwelle anpassen + mehr Lektoren |
| **Politiker blockieren** | Kommunale/Länder-Piloten ausbauen + öffentlichen Druck |
| **Plattform kompromittiert** | Backup-System aktivieren + Forensik |
| **LLM-Bias nachgewiesen** | Zusammenfassung auf manuellen Prozess umstellen |
| **Kosten explodieren** | Vereinfachung: manuelles Clustering |

**Abbruch-Kriterien:** Siehe Fehlschlag-Kriterien (Punkt 16).

---

## 18. Wie skaliert es, wenn es überall so ist?

| Ebene | Skalierung | Herausforderung |
|-------|------------|-----------------|
| **Kommunen** | ~11.000 in DE | Lokale Verifizierung, kleinere Feedbackmengen |
| **Landkreise** | ~400 in DE | Überschneidungen vermeiden |
| **Bundesländer** | 16 in DE | Unterschiedliche Gesetze, gemeinsame Infrastruktur |
| **Bund** | 1x DE | Antwortpflicht als Gesetz |
| **EU** | 27 Mitgliedstaaten | Übersetzung, Verifizierung über Ländergrenzen |
| **Weltweit** | ~200 Länder | Sehr unterschiedliche Systeme |

**Unintendierte Konsequenzen:** Hype-Feedbackwellen, Kompetenz-Gefälle (digitaleaffine Gruppen dominieren), Fragmentierung wenn jeder Betrieb sein eigenes System baut (→ Open Source Standard).

---

## 19. Bekannte Unsicherheiten

| Unsicherheit | Annahme |
|--------------|---------|
| **Beteiligung** | >10% registrieren sich, >2% sind aktiv |
| **Kampagnen-Verhalten** | Transparenz-Anforderungen reichen |
| **LLM-Qualität** | Fehlerquoten tolerabel mit Human-Review |
| **Politische Kultur** | Wird sachlicher durch Argument-Struktur |
| **Technologie** | Audits finden kritische Lücken vor dem Start |

**Nachbesserungs-Bedingungen:**
- Beteiligung <5% nach 2 Jahren → Zugang überarbeiten + Kampagne
- LLM-Fehler >5% → mehr Lektoren oder manuelles Clustering
- Manipulation nachgewiesen → Audits + Code-Überarbeitung

---

## 20. Gegenargumente & Widerlegungen

| Gegenargument | Wer bringt es vor? | Ist es berechtigt? | Widerlegung / Anpassung |
|---------------|-------------------|-------------------|-------------------------|
| **"Bürger sind inkompetent"** | Etablierte Politiker, Lobbyisten | Teilweise | Argument-Struktur + Clustering filtert Lärm; Fachwissen kommt als belegte Issues |
| **"Zu teuer"** | Steuerzahler-Lobby, Finanzminister | Nein | ~15 Mio. €/Jahr vs. Milliarden Lobby-Einfluss; günstiger als Bürgerrat-Gremien |
| **"Verfassungswidrig"** | Konservative Juristen | Nein | Ergänzt repräsentative Demokratie (Arbeitsgruppe entscheidet), ersetzt sie nicht |
| **"Populismus durch Masse"** | Medien, Politikwissenschaftler | Teilweise | Keine Mehrheitsentscheidung über Inhalte; Arbeitsgruppe muss begründen, nicht folgen |
| **"Digitale Spaltung"** | Sozialverbände | Ja | Terminals + VHS-Schulungen + Lese-Modus ohne Account (offene Frage: Umfang) |
| **"Sniping/Kampagnen kapern es"** | Kritiker | Ja | Verifizierung + Rate-Limits + transparente Cluster + Anomalie-Statistiken |
| **"LLM verzerrt Zusammenfassungen"** | Tech-Kritiker, Datenschützer | Ja | Open Source Modelle + Human-Review + Fehlerquoten-Reporting |
| **"Anonym = alles totgeschlagen"** | Politikwissenschaftler | Teilweise | Verifizierung erzwingt Identität hinter der Anzeige; Rate-Limits + Moderation |
| **"Politiker blockieren es"** | Realisten | Ja | Kommunale Piloten schaffen Beweise + öffentlichen Druck |

---

## 21. Implementierungsplan (detailliert)

### 21.1 Plattform-Grundarchitektur: "Gesetze als Repository"

Jedes Gesetzesvorhaben (neues Gesetz, Änderung, Aufhebung) ist ein **Repository**, analog zu GitHub/GitLab:

| Element | Entsprechung | Inhalt |
|---------|--------------|--------|
| **Repo** | Repository pro Vorhaben | Gesetzentwurf als versionierte Dateien (Markdown/Law-Format) |
| **Commits** | Versionierung | Jede Änderung nachvollziehbar (diff, wer, wann, warum) |
| **Issues** | Feedback-Kanäle | Einwände, Verbesserungsvorschläge, Fragen, Fehlermeldungen |
| **Pull Requests** | Änderungsvorschläge | Konkrete Textänderungen mit Begründung |
| **Labels** | Kategorisierung | z.B. `kritik`, `verbesserung`, `frage`, `betroffenheit`, `datenfehler` |
| **Milestones** | Phasen | Einreichung → Kritik → Überarbeitung → Beschluss |
| **Changelog** | Historie | Was wurde aus welchem Feedback übernommen/verworfen? |

**Hosting:**
- **Souveräne Infrastruktur:** Betrieben von öffentlichem Träger (z.B. Bund) oder öffentlich-rechtlicher Stiftung – **nicht** privates Unternehmen
- **Open Source:** Plattform-Code ist öffentlich, auch **self-hostable** (Fork auf eigenem Server möglich)
- **Spiegel-Hosting:** Read-only Spiegel auf GitHub/GitLab etc. für Sichtbarkeit und externe Tools; authentische Quelle bleibt die souveräne Instanz
- **Export-Pflicht:** Jedes Repo jederzeit als Datei-Paket exportierbar (Kein Vendor-Lock-in)

### 21.2 Identität: Verifiziert, aber wahlweise anonym sichtbar

**Grundprinzip: 1 Person = 1 Account**
- **Pflicht-Verifizierung bei Registrierung** (z.B. eID/BundID, Ausweis-Verfahren oder PostIdent-Äquivalent)
- Der Staat/Träger prüft nur: "Ist das eine reale, berechtigte Person?" – **keine** weiteren Daten
- **Doppel-Accounts werden technisch verhindert** (Verifizierungs-Datensatz wird nach Prüfung gelöscht bzw. nur als Hash gespeichert)
- Minderjährige: Teilnahme ab 14 (Altersfrage final klären, siehe Punkt 22)

**Pseudonym + optionale Anonymität:**

| Modus | Was sehen andere? |
|-------|-------------------|
| **Pseudonym** | Name frei wählbar, Account-Historie einsehbar |
| **Anonym** | Kommentar ohne Namen sichtbar, nur "verifizierter Bürger"-Badge |

- Anonymität schützt vor Vergeltung (Arbeitgeber, Nachbarn, Online-Mobbing)
- **Anonyme Beiträge sind moderiert** (etwas strengere Qualitätsprüfung möglich)
- Interne Verknüpfung Account ↔ Beiträge bleibt für Missbrauchsbekämpfung (Rate-Limits, Strafrecht) – **niemals öffentlich**

**Warum Verifizierung zwingend?**
- Ohne Verifizierung: Bots, Trollfarmen, Massen-Accounts → Plattform unbrauchbar
- Verifizierung ist die Voraussetzung dafür, dass **alle** mitreden dürfen, ohne dass Fakes das Vertrauen zerstören

### 21.3 Teilnahme-Limits statt Blockierung

**Grundprinzip: Niemand wird gesperrt oder stummgeschaltet – es gibt nur Geschwindigkeitslimits.**

**Rate-Limits (Startwerte, final zu kalibrieren):**

| Aktion | Limit |
|--------|-------|
| **Kommentare/Beiträge pro Tag** | 100 (Vorschlag, muss evaluiert werden) |
| **Neue Issues pro Tag** | 5 |
| **Voting pro Issue** | 1 Stimme pro Account |
| **Pull Requests pro Tag** | 3 |

- Limits sind **global gleich** für alle – keine Privilegien, kein "verifizierter Premium-Bürger"
- Bei Erreichen: Account kann weiterhin **lesen und voten**, nur schreiben pausiert bis zum nächsten Tag
- Limits wirken gegen Flooding/Sniping, aber ein engagierter Bürger kann pro Vorhaben problemlos mitdiskutieren

**Missbrauchsabstufung (von sanft zu hart):**

| Stufe | Maßnahme |
|-------|----------|
| 1 | Limit-Verkürzung für den Einzelfall (z.B. 50/Tag für 7 Tage) |
| 2 | Beiträge verbergen sich hinter Qualitätsschwelle (nur aufklappbar) |
| 3 | Temporäre Schreibsperre (Tage) – **nur** bei gerichtlich überprüfbarem Regelverstoß |
| 4 | Dauersperre – **nur** bei Straftat (Beleidigung, Volksverhetzung, Bot-Farm-Betrieb), mit Rechtsmittel |

- **Jede Maßnahme muss begründet, dokumentiert und anfechtbar sein** (Transparenz-Log öffentlich, Namen anonymisiert)
- Ziel: Beschwerden wie "ich darf nichts sagen" vermeiden – Limit ≠ Ausschluss

### 21.4 Oberfläche: GitLab-Standard, keine Custom-App

**Grundsatz:** Keine eigene App-Entwicklung. GitLab bringt alles mit: Issue-Diskussionen, Votes, Sortierung, Suche, Benachrichtigungen, mobile Web-UI.

**Zugangsstufen:**

| Stufe | Zugang | Rechte |
|-------|--------|--------|
| **Lesen** | Ohne Account (Web-UI) | Repos, Issues, Diffs, Historie einsehen |
| **Feedback geben** | Verifizierter Account | Issues erstellen, kommentieren, voten |
| **Änderungen vorschlagen** | Verifizierter Account | Merge Requests (PRs) |
| **Entwurf pflegen** | Arbeitsgruppen-Mitglied | Push-Rechte im eigenen Repo (nur hier!) |

**Kernpunkt der Sicherheitsarchitektur: Account-Verwaltung**

Der **einzige** kritische Baustein ist: *Steckt wirklich ein deutscher Berechtigter hinter jedem Account?* Alles andere ist Standard-GitLab.

- **Login per Personalausweis-Verifizierung** (eID/BundID – Infrastruktur existiert bereits, siehe 21.2)
- **1 Person = 1 Account**, technisch erzwungen (Hash-Prüfung, siehe 21.2)
- **Berechtigungsgruppen nach Ebene:** Bund / Land / Kreis / Kommune – ein Account sieht und kann überall mitlesen, aber Vorhaben-Einreichung nur in der eigenen Gebietskörperschaft
- **Push-Rechte ausschließlich für Arbeitsgruppen** – normale Bürger committen nichts, sie erstellen Issues und MRs (GitLab rollenbasiert abgedeckt)
- **Keine Custom-Auth-Logik:** GitLab-Standard-Auth + OIDC/SAML-Anbindung an eID-Provider = bewährter Pfad, kein selbstgebautes Login

**Warum das günstig und robust ist:**
- Kein Feed-Algorithmus → keine Manipulationsfläche, keine Bias-Diskussionen, keine Audits nötig
- Sortierung ist chronologisch/chronologisch-umgekehrt + Labels + Votes – GitLab-Standard
- GitLab ist ausgereift, self-hosted bewährt (gitlab.com, countless Enterprise-Instanzen)
- Wartung = GitLab-Updates + eID-Anbindung, kein Custom-Code

### 21.5 Anti-Flut & Anti-Sniping: Feedback muss verarbeitbar bleiben

**Problem:** 84 Mio. Bürger können zehntausende Issues erzeugen. Die Arbeitsgruppe kann das nicht lesen – und organisierte Kampagnen (Sniping/Botting) könnten den Prozess kapern.

**Clustering & Deduplizierung:**
- **Automatisches Clustering:** Inhaltlich identische Beiträge werden zusammengefasst ("4.200 Bürger melden denselben Punkt")
- **Ähnlichkeits-Erkennung:** Semantische Gruppierung (nicht nur Keywords) – "Das kostet zu viel" zählt als ein Cluster mit 4.200 Stimmen, nicht 4.200 Issues
- **Jeder Beitrag zählt:** Die Supporter-Anzahl pro Cluster ist sichtbar – niemand fühlt sich ignoriert

**Zusammenfassung (Human-in-the-Loop):**
- **LLM-gestützte Vor-Zusammenfassung** pro Cluster (Open Source, auditierbar, läuft souverän)
- **Verifizierte Bürolektoren** prüfen und korrigieren die Zusammenfassung – die KI fasst zusammen, Menschen verantworten
- **Zusammenfassung + vollständige Liste:** Die Arbeitsgruppe sieht beides – kompaktes Cluster-Bundle UND jeden Einzelbeitrag abrufbar

**Triage-Workflow für die Arbeitsgruppe:**

| Status | Bedeutung | Pflicht |
|--------|-----------|---------|
| **Neu** | Eingegangen | Automatisch geclustert |
| **Geprüft** | Zusammenfassung erstellt | – |
| **Verarbeitet** | Arbeitsgruppe hat reagiert | Antwort + Umsetzung im Entwurf ODER begründete Ablehnung |
| **Verworfen** | Duplikat/Off-Topic | Begründung, zählt weiter im Cluster |

**Kernregel (Antwortpflicht):** Jedes Cluster mit über Schwelle X Beiträgen **muss** eine dokumentierte Antwort bekommen:
- ✅ Eingearbeitet → mit Commit + Begründung
- ❌ Abgelehnt → mit Begründung (muss die stärksten Argumente direkt ansprechen)
- 🤷 Unentschieden → als offener Punkt dokumentiert, geht in finale Risiko-Bewertung

**Anti-Sniping-Maßnahmen:**

| Bedrohung | Gegenmaßnahme |
|-----------|---------------|
| **Bot-Farmen / Massen-Accounts** | Verifizierung (1 Person = 1 Account) + Rate-Limits |
| **Organisierte Kampagnen** | Kampagnen sind **legal, aber transparent**: Koordinierte Aktionen dürfen nicht vertuscht werden; Cluster-Anzeige zeigt realen Support |
| **Astroturfing (falsche "Bürger"-Stimme)** | Kostenloser verifizierter Zugang macht echte Bürger-Stimme billig – kein Bedarf für bezahlte Schein-Grassroots |
| **Kapern von Trending** | Kein Trending-Feed (GitLab sortiert chronologisch + Labels/Votes) – Sichtbarkeit folgt Aktivität, nicht Viralität |
| **Externe Einflussnahme** | Aggregierte Statistiken (Regionen, Zeitmuster) werden veröffentlicht; Anomalien werden geprüft |

**Gewichtung: Quantität ≠ Qualitäts-Gewinn:**
- **Up/Down-Votes** auf Argumente, nicht auf Meinungen ("gut begründet" vs. "stimmt einfach zu")
- **Argument-Struktur:** Beiträge können "Pro/Kontra + Beleg" formatiert sein – gut belegte Argumente werden sichtbarer
- **Keine direkte Mehrheitsentscheidung über Inhalte** – die Plattform aggregiert Meinungsbilder, **entscheiden tut die Arbeitsgruppe (mit dokumentierter Begründung)**. Das verhindert Populismus-by-Feed.

### 21.6 Arbeitsgruppen: Wer macht das?

**Bildung:**
- Die **Einreicher-Gruppe** (Bürgerinitiative, NGO, Ministerium, einzelner Abgeordneter…) verfasst und pflegt den Entwurf
- Jede Arbeitsgruppe **registriert sich** mit: Mitglieder, Sponsoren/Finanzierung, Interessenkonflikte (öffentliche Pflichtangabe)
- **Offene Einladung:** Jeder verifizierte Bürger kann der Arbeitsgruppe beitreten oder als Reviewer wirken

**Pflichten:**

| Pflicht | Beschreibung |
|---------|--------------|
| **Alle 24 Punkte beantworten** | Vor "in Bearbeitung"-Status (Templates aus `00`) |
| **Issue-Verarbeitung** | Jedes Cluster über Schwelle beantworten (siehe 21.5) |
| **Transparenz** | Alle Meetings, Entscheide, Kontakt zu Lobbyisten dokumentiert im Repo |
| **Fristen einhalten** | Review-Phasen sind öffentlich nachvollziehbar |
| **Keine Filterung** | Arbeitsgruppe darf Kritik NICHT löschen – nur moderieren nach klaren Regeln (Beleidigung, Spam, Off-Topic), jede Moderation dokumentiert |

### 21.7 Schutzmechanismen

| Bedrohung | Schutz |
|-----------|--------|
| **Lobbyismus im Verborgenen** | Pflicht-Dokumentation aller Kontakte + Sponsoren der Arbeitsgruppe; Plattform-Kontakte sind öffentlich |
| **Überschwemmung der Arbeitsgruppe** | Clustering, Zusammenfassung mit human review, Triage mit Antwortpflicht nur über Schwelle |
| **Sniping / Bot-Farmen** | 1 Person = 1 Account, Rate-Limits, Anomalie-Statistiken öffentlich |
| **Feed-Manipulation / Bias** | Entfällt – kein Feed-Algorithmus (GitLab-Standard) |
| **Ausschluss von Minderheiten** | Jeder verifizierte Bürger kann mitmachen; anonym sichtbar; Minderheits-Positionen werden im Abschlussdokument explizit ausgewiesen |
| **Populismus-by-Feed** | Plattform entscheidet nichts – sie aggregiert; Arbeitsgruppe muss begründet antworten, nicht der Mehrheit folgen |
| **Moderations-Missbrauch** | Moderation nur nach klaren Regeln, jede Aktion dokumentiert, Beschwerde-Weg |
| **Vendor-Lock-in** | Open Source, Export-Pflicht, self-hostable, Mirror-Hosting |
| **Staatliche Einflussnahme** | Souveräne Stiftung + unabhängige Aufsicht + Code-Audits; Staat ist Nutzer, nicht Operator der Meinungsbildung |

## 22. Offene Fragen

**Hochpriorität (vor Implementierung klären):**

1. **Rate-Limit-Werte:** Sind 100 Nachrichten/Tag sinnvoll? Basierend auf was kalibrieren? (Median-Nutzer braucht <10; Power-User und Kampagnen-Anführer mehr?)
2. **Cluster-Schwelle:** Ab wievielen Beiträgen pro Cluster besteht Antwortpflicht? (Vorschlag: dynamisch, z.B. ab 25 Beiträgen oder wenn Cluster ≥1% der Feedbacks zum Vorhaben)
3. **Verifizierungs-Verfahren:** eID/BundID vs. PostIdent-Äquivalent? Wie ohne Smartphone? Barrierefreiheit?
4. **Datenschutz-Design:** Was genau wird bei der Verifizierung gespeichert, was sofort gelöscht, was gehasht? DSGVO-konforme Architektur ausarbeiten.
5. **Rechtsform/Betreiber:** Öffentlich-rechtliche Stiftung? Wofür haftet wer? Wie ist redaktionelle Unabhängigkeit verankert?
6. **Moderationsregeln:** Konkreter Regelkatalog + Instanzenzug (wer entscheidet bei Beschwerden?)

**Mittlere Priorität (während Pilot klären):**

7. **LLM-Zusammenfassung:** Welches Modell, welche Fehlerquoten, wie wird menschliche Prüfung organisiert (Bürolektoren – wer, wie viele, bezahlt von wem)?
8. **Anonymitäts-Grenzen:** Darf anonym diskutiert werden in hochsensiblen Vorhaben (z.B. interne Sicherheitsgesetze)?
9. **Integration bestehender Petitions-/Beteiligungsportale** (Bundestag-Petitionen, Landesportale) – migrieren oder parallel?
10. **Zugangs-Verbreitung:** Web-UI (responsiv) + wie erreicht man Offline-/Alters-Gruppen ohne Smartphone/PC? (Terminals, VHS)

**Niedrige Priorität (nach Pilot evaluieren):**

11. **Kostenrahmen:** Betrieb, Lektoren, Audits – realistische Schätzung nötig (aktuell grob: 9–17 Mio. €/Jahr)
12. **Teilnahme-Raten:** Welche Quote an Bundesbürgern ist realistisch/erforderlich für Legitimität?
13. **Internationale Nutzung:** Nur deutsche Verifizierung? EU-Bürger wohnhaft in Deutschland?

## 23. Nächste Schritte

**🔴 Hochpriorität (vor Pilot-Phase klären):**
- [ ] Offene Fragen 1–6 (siehe Punkt 22) beantworten
- [ ] Plattform-Spezifikation finalisieren (Basis: GitLab-CE + eID-Anbindung)
- [ ] Pilot-Kommunen identifizieren (3–5, welche?)

**🟡 Mittlere Priorität (während Plattform-Einrichtung):**
- [ ] Security-Audits planen (Wer? Wie oft? Kosten?)
- [ ] Cluster-Algorithmus prototypen (Basis: Pol.is, semantische Embeddings)
- [ ] Lektoren-Konzept ausarbeiten (Anzahl, Qualifikation, Bezahlung)
- [ ] Moderationsregel-Katalog als eigenes Repo (öffentliche Beteiligung)

**🟢 Niedrige Priorität (nach Pilot evaluieren):**
- [ ] Kosten-Validierung mit echten Pilot-Daten
- [ ] Digitale-Spaltung-Maßnahmen (Terminals, Schulungen) ausbauen
- [ ] EU-Rollout-Strategie

**Laufende Aufgaben:**
- [ ] Dieses Dokument diskutieren (simulierte Kritikphase)
- [ ] Feedback einarbeiten
- [ ] Förderung beantragen (Stiftungen: Schöpflin, Mercator, EU-Programme)

---

*Erstellt: 2026-11-11*
*Version: 2.0*
*Status: Zur Diskussion*
