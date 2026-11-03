# Anleitung SPK Konzept-Ersteller (Alpha 0.8.0)

Stand 03.11.2026 · Josef Wagner

Der SPK Konzept-Ersteller bemisst eine Sprinkleranlage vor: nach VdS CEA 4001:2024-01, wahlweise NFPA 13/20 oder FM Global – vom Projekt über Netzberechnung und Pumpen-Wahl bis zu Schema, Gruppenplan und Bericht. Alpha-Testversion: nur zum Testen, keine kommerzielle Nutzung, ersetzt keine vollständige hydraulische Berechnung.

## 1 Installation

Alle drei Varianten zeigen dieselbe Oberfläche; Projekte bleiben lokal auf deinem Gerät. Downloads: [SPK-Konzept-Ersteller-Alpha](https://github.com/josefwagner1989-wq/SPK-Konzept-Ersteller-Alpha).

| System | Datei | So geht's |
| --- | --- | --- |
| Windows 10/11 (x64) | `SPK-Konzept-Ersteller-Setup.exe` | Doppelklick. Installiert ohne Admin-Rechte für deinen Benutzer, legt Startmenü- und Desktop-Verknüpfung an und öffnet das Programm in einem eigenen Edge-Fenster. Warnt SmartScreen: „Weitere Informationen“ → „Trotzdem ausführen“ (Datei noch nicht signiert). Deinstallieren über Einstellungen → Apps. |
| Linux | `spk-konzept-ersteller.flatpak` | `flatpak install --user spk-konzept-ersteller.flatpak`, dann im Anwendungsmenü starten. Exporte (DXF, SVG) landen im Ordner Downloads. |
| Browser | Link zur Web-Version | Ohne Installation, in jedem aktuellen Browser. Drucken ist dort gesperrt; für den Bericht als PDF die Desktop-Version nutzen. |

## 2 Die Oberfläche

Oben rechts stellst du drei Dinge um; alles andere passiert in den Registern darunter.

- **Register / Interaktiv:** Register = alle Eingaben frei in Reitern. Interaktiv = geführter Ablauf in 25 Schritten mit Erklärung und Normbezug (Abschnitt 3).
- **Auto / Hell / Dunkel:** Darstellung; Druck und Export sind immer hell.
- **DE / EN:** Sprache der Oberfläche und des Berichts.
- **Anleitung:** öffnet diese Anleitung.

Beim ersten Start erscheint der Alpha-Hinweis. Mit „Verstanden – nur zum Testen“ schließt du ihn; über das Abzeichen **ALPHA · TEST** neben dem Titel holst du ihn jederzeit zurück. Ganz unten stehen Version, Stand und Creator.

Die Reiter sind in drei Zeilen geordnet:

| Zeile | Reiter |
| --- | --- |
| Projekt | Übersicht · Versorgung & Pumpe · SPZ / SPUZ · Konzeptschema · Gruppenpläne · Bericht · Nachweis · Prüfung · Fehlercheck |
| Bereich (der gewählte) | Auslegung · Rohrnetz & Anlagenart · Zweite Ebene · Regalschutz · Netzberechnung · Layoutvergleich |
| Werkzeuge | Anbohrungen · Hydraulik & K-Faktor · Rohr-Abakus |

## 3 Arbeitsablauf und interaktiver Modus

Ein Projekt durchläuft immer dieselben Stationen; die Abschnitte 4 bis 9 folgen dieser Reihenfolge.

1. Projekt anlegen: Regelwerk, SPZ / SPUZ, Bereiche (Abschnitt 4).
2. Je Bereich: Klasse, Auslegung, Sprinkler und Raster, Anlagenart, zweite Ebene, Regal, Netzberechnung (Abschnitt 5).
3. Wasserversorgung nach dem maßgebenden Bereich, Pumpen-Wahl, NPSH (Abschnitt 6).
4. Zentralen und Stationen, Konzeptschema (Abschnitt 7), bei Bedarf Gruppenpläne (Abschnitt 8).
5. Fehlercheck, Nachweis, Bericht (Abschnitt 9).

**Interaktiv** führt genau durch diesen Weg als Flussdiagramm mit 25 Schritten. Links das Diagramm – jeder Kasten zeigt seinen Zustand als Farbpunkt (grün erledigt, orange Achtung, rot offen, grau nicht nötig, blau Information). Rechts der gewählte Schritt:

- ausführliche Erklärung, Formel und aktueller Wert;
- **Normbezug VdS CEA 4001** mit Abschnittsnummer und Titel (Titel sinngemäß – mit eigener Norm prüfen) sowie die Fundstellen der Werte;
- die Eingabefelder dieses Schritts – dieselben Daten wie in den Reitern;
- **Zurück / Weiter** und ein Sprung in den passenden Reiter.

Rauten sind Entscheidungen (z. B. Frostgefahr? Regallager?); „ja“ führt in den Seitenschritt rechts, gestrichelte Pfeile führen bei nicht erfüllter Prüfung zurück. In Schritt 1 legst du die Zahl der Bereiche und Unterzentralen fest.

## 4 Projekt anlegen

Im oberen Kasten legst du Name, Regelwerk, Zentralen und Bereiche fest; diese Struktur gilt für alle Reiter.

1. **Projektname** eintragen.
2. **Regelwerk** wählen: VdS CEA 4001 2024-01 (08), NFPA 13/20 oder FM Global. Klassen, Bemessungswerte und Prüfregeln wechseln mit; NFPA/FM-Werte sind überwiegend aus Sekundärquellen (Status beachten, Abschnitt 11).
3. **Zentralen:** Die **SPZ** (Sprinklerzentrale) ist der Pumpenraum mit Wasservorrat und Pumpe. Mit **+ SPUZ** legst du Unterzentralen an – dort stehen weitere Alarmventilstationen. Die SPUZ hängen nacheinander an einer Hauptzuleitung aus der SPZ (SPZ → SPUZ 1 → SPUZ 2 …); Länge, Nennweite und Höhe jedes Abschnitts trägst du im Reiter SPZ / SPUZ ein.
4. **Bereiche:** Ein Bereich ist ein Gebäudeteil mit einer Nutzung, einer Anlagenart (nass, trocken, Glykol) und einer Zentrale. **+ Bereich** legt einen neuen an, **Duplizieren** kopiert den gewählten, **Löschen** entfernt ihn (mit Rückfrage). Ein Klick auf eine Bereichskarte wählt ihn für die Reiter der Zeile „Bereich“.

„Neues Beispielprojekt“ lädt ein fertiges Beispiel zum Ausprobieren; im Modus Interaktiv beginnt ein Projekt leer.

## 5 Bereich bemessen

Die Reiter der Zeile „Bereich“ gehst du für jeden Bereich von links nach rechts durch; jede Eingabe rechnet sofort neu.

| Reiter | Was du eingibst | Was herauskommt |
| --- | --- | --- |
| Auslegung | Nutzungsart, Brandgefahrenklasse (LH, OH1–OH4, HHP, HHS), Fläche, K-Faktor, Schutzfläche, Raster, Betriebszeit; bei HHS die Werte aus den Lagertabellen | Dichte D, Wirkfläche A, Sprinkler je Wirkfläche, Mindestwasserbedarf D · A |
| Rohrnetz & Anlagenart | nass / trocken / Glykol, Verbindungsart, Rohrlängen je Nennweite (DN 25 … 300) | Rohrnetzvolumen, Grenze je Trockenstation (Tab. 10.02), Füllzeit, Schnellöffner nötig? |
| Zweite Ebene | Hohlraumhöhe, Fläche, ob gleichzeitig wirksam | ob Schutz nötig ist (> 0,8 m oder brennbar), Zusatzwassermenge |
| Regalschutz | Regalmaße, Anzahl, Ebenen, wirksame Sprinkler, Druck | anrechenbare Sprinkler (L × B × N × E / 9 m²), Zusatzwassermenge |
| Netzberechnung | Strang- und Verteilleitung (DN), Abstände, Zuleitung, Höhe, C-Wert, Formstückzuschlag | Durchfluss und Druck am Alarmventil nach Hazen-Williams, Mehrbedarf gegenüber D · A, Fließgeschwindigkeiten |
| Layoutvergleich | Raummaße (rechteckig) | alle zulässigen Raster der Klasse in beiden Richtungen im Vergleich (Wandabstand S/2 bzw. D/2) |

**Geschwindigkeitsgrenze:** Die Netzberechnung prüft die Strangleitung auf höchstens 10 m/s und die Verteilleitung (mit Zonenventil und Strömungsmelder) auf höchstens 6 m/s. Wird eine Grenze überschritten, nennt das Programm die kleinste Nennweite, die sie einhält – diese wählen und neu prüfen. Ein Mehrbedarf über 30 % deutet ebenfalls auf zu kleine Leitungen hin.

## 6 Wasserversorgung und Pumpen-Wahl

Der Reiter **Versorgung & Pumpe** legt Pumpe und Vorrat nach dem maßgebenden Bereich aus – dem mit dem höchsten Bedarf, nicht der Summe aller Bereiche.

**Wasserversorgung:** Antrieb (Elektro / Diesel), Verluste der Armaturen in der SPZ, Pumpenwirkungsgrad und optional Hydranten. Ergebnis: Förderstrom, Druck an der Pumpe, Wellenleistung, Wasservorrat V = Q · t und die Mindestnennweite der Saugleitung.

**Pumpen-Wahl mit Timmy:** Der Wal Timmy fasst das Ergebnis in einem Satz zusammen – „Passt!“, „Knapp bemessen“ oder „Etwas zu groß“.

1. **Kennlinie wählen:** „Typische Kennlinie (Vorauswahl)“ für einen ersten Entwurf, oder „Hersteller: 3 Punkte“ – dann Nullförderdruck, Nennpunkt (Qn, pn) und einen dritten Punkt rechts vom Nennpunkt aus dem Datenblatt eintragen.
2. **Saugseite:** NPSH erforderlich (Hersteller), Wasserspiegel über Pumpenachse, Länge der Saugleitung, Wassertemperatur.
3. **Leistungsabfall (Verschleiß) %** – Standard 5 %. Die Bedarfsseite rechnet mit der gealterten Kennlinie p × (1 − w); die Überlastseite (günstigste Wirkfläche, Nullförderdruck) mit der neuen. Im Diagramm ist die gealterte Kennlinie orange.
4. **Idealbereich Reserve min / max %** – Standard 10 … 40 %. Reserve = wie viel mehr Wasser die gealterte Pumpe beim nötigen Druck noch liefert. Darunter fehlt Freiraum für weitere Systeme, darüber ist die Pumpe überdimensioniert.
5. **Prüfungen lesen:** Bedarf erfüllt, Q ≤ Qn, günstigste Wirkfläche ≤ 1,4 · Qn bei ≥ 0,7 · pn (VdS) bzw. Nullförderdruck und 150-%-Punkt (NFPA 20), stabile Kennlinie, NPSH mit 1 m Reserve, dazu Idealbereich und Leistungsabfall.
6. **Pumpen-Datenbank:** Unter dem Diagramm stehen die Baureihen, die Bedarf plus Reserve abdecken, mit Quelle und Datum. Das passende Modell im Herstellertool wählen und dessen 3 Kennlinienpunkte oben eintragen.

Leistungsabfall und Idealbereich sind eigene Planungsregeln, keine Normwerte; die Normprüfungen bleiben das Kriterium.

## 7 Zentralen, Stationen und Konzeptschema

Im Reiter **SPZ / SPUZ** werden die Bereiche automatisch auf Alarmventilstationen verteilt: nass nach der Zahl der anrechenbaren Sprinkler (Tab. 10.01), trocken nach dem Rohrnetzvolumen (Tab. 10.02).

- Je SPUZ Länge, Nennweite und Höhe der Zuleitung eintragen. Die Verluste aller Abschnitte von der SPZ bis zur SPUZ werden addiert; liegt die Fließgeschwindigkeit eines Abschnitts über 10 m/s, nennt das Programm die nötige Nennweite.
- Hinweise erscheinen z. B. bei mehr als zwei Trockenstationen in einer Zentrale (zwei Kompressoren) oder einer Zentrale ohne Bereich.

Das **Konzeptschema** zeigt die Anlage als Funktionsschema: SPZ mit Behälter, Pumpe, Druckhaltepumpe, Prüfleitung und Feuerwehreinspeisung; die Hauptzuleitung zu SPUZ 1, 2, 3 mit Abschnittsangaben; je Station Alarmventil, Manometer, Alarmglocke, Druckschalter mit Meldung an die BMZ; Zonenkontrolle und Bereiche mit Sprinklerzahl. Trockene Rohrnetze sind gestrichelt. **DXF exportieren** liefert die Zeichnung für CAD (Ebenen SPK-ROHR, -ALARMVENTIL, -SYMBOL, -RAHMEN, -TEXT; 1 Einheit = 1 mm), **SVG** für Dokumente.

## 8 Gruppenpläne aus DXF

Im Reiter **Gruppenpläne** zeichnest du die Sprinklergruppen auf den Grundriss jeder Etage und exportierst Übersichtspläne.

1. **Etage anlegen** und je Etage eine **DXF-Datei** laden (ASCII-DXF R12 bis 2018). DWG vorher mit einem separat installierten Konverter in DXF umwandeln, z. B. ODA File Converter.
2. **Maßstab:** Das Programm erkennt die Zeichnungseinheit automatisch ($INSUNITS, sonst aus der Plangröße) und wählt den kleinsten Normmaßstab, bei dem der Plan auf A1 passt. Einheit, Korrekturfaktor und Plotmaßstab kannst du danach von Hand ändern.
3. **Layer** ein- und ausblenden, mit Mausrad zoomen, mit Ziehen verschieben.
4. **Gruppen zeichnen:** Polygon Punkt für Punkt anklicken und schließen. Fläche (m²), Station und Zone werden beschriftet; die Fläche kann in den Bereich der Berechnung übernommen werden (Summe über alle Etagen).
5. **Export** je Etage als DXF (Originalkoordinaten und -einheiten, Gruppen auf Layer SPK-GRUPPEN) oder SVG.

Geladene Pläne bleiben im Browser gespeichert und müssen nicht jedes Mal neu geladen werden.

## 9 Ergebnisse prüfen und ausgeben

Vier Reiter zeigen, ob das Ergebnis trägt und woher jeder Wert kommt.

| Reiter | Wofür |
| --- | --- |
| Bericht | Zusammenfassung zum Drucken: Projektstruktur, Bereiche, Stationen, Versorgung, Pumpe, Schema, Fehlercheck, Normbezug, Alpha-Hinweis. In der Desktop-Version „Drucken / als PDF speichern“. |
| Nachweis | Jeder Rechenschritt mit Formel, Wert und Fundstelle samt Status (Abschnitt 11). |
| Prüfung | Selbsttest: das Programm rechnet hinterlegte Testfälle (Normbeispiele, Handrechnungen) nach. Alles muss „bestanden“ zeigen. |
| Fehlercheck | 34 häufige Planungs- und Montagefehler, 14 davon automatisch aus deinen Daten geprüft, der Rest als Checkliste – jeweils mit Abschnitt, Seite und Bild/Tabelle der Norm. |

**Bilder der Norm:** Die App enthält keine Normtexte oder -bilder. Trage im Fehlercheck den Pfad oder Link zu deiner eigenen lizenzierten Norm-PDF ein; dann öffnet ein Klick die genannte Seite direkt in deiner PDF.

## 10 Werkzeuge

Die Werkzeuge rechnen unabhängig vom Projekt und ändern es nicht.

- **Anbohrungen:** prüft einen Abgang, der durch Anbohren der Hauptleitung entsteht (Anbohrschelle / mechanisches T-Stück oder Anschweißstutzen), mit den Regeln für saubere Bohrungen.
- **Hydraulik & K-Faktor:** Druckverlust einer Leitung nach Hazen-Williams (Vergleich Darcy-Weisbach) und Umrechnung Q = K · √p in alle Richtungen, mit nächstem Standard-K.
- **Rohr-Abakus:** Rechenschieber für DN 25 … DN 300. Schieber oder rote Haarlinie bewegen: Außendurchmesser, Wandstärke je Verbindung, Innendurchmesser, Inhalt (l/m), **Gewicht leer und gefüllt (kg/m)**, Druckverlust, Geschwindigkeit und Durchfluss an der Geschwindigkeitsgrenze. Darunter das Nomogramm aller Nennweiten. Wandstärken DN 250/300 sind noch nicht gegen die Norm geprüft.

## 11 Status der Werte und Speichern

Jeder Normwert trägt ein Status-Etikett. Orange markierte Werte vor einer Verwendung mit der Norm abgleichen.

| Status | Bedeutung |
| --- | --- |
| Norm | gegen den Normtext geprüft |
| sekundär | aus Sekundärquelle oder Normnotizen – vor Verwendung prüfen |
| ungeprüft | aus anderer Norm oder Erinnerung – ungeprüft |
| Annahme | eigene technische Annahme bzw. Rechenmethode des Programms |
| Eingabe | Planer trägt den Normwert selbst ein |

**Speichern:** Das Projekt wird bei jeder Eingabe automatisch lokal gespeichert (Browser bzw. Profil der Desktop-App) und beim nächsten Start wieder geladen. Es wird nichts an einen Server geschickt. In der Alpha gibt es noch keinen Export des Projekts als Datei; Browserdaten löschen heißt Projekt löschen.

## 12 Grenzen der Alpha und Feedback

Die Alpha ist eine Vorbemessung zum Testen; diese Punkte sind bekannt und offen:

- Nur Baumnetze mit endgespeisten Strängen; keine Ring- oder Gitternetze.
- Viele Normwerte und alle Abschnittstitel im Ablauf sind noch nicht gegen die VdS-Ausgabe geprüft (orange markiert).
- Pumpen-Datenbank: bisher nur Baureihen-Grenzwerte von KSB, noch keine Kennlinien je Modell.
- DWG nur über einen externen Konverter (DXF-Import und -Export sind eingebaut).
- NFPA- und FM-Werte überwiegend aus Sekundärquellen; einige Konzeptfunktionen folgen der VdS-Logik.

**Feedback:** Fehler und Wünsche bitte als [Issue im Alpha-Repository](https://github.com/josefwagner1989-wq/SPK-Konzept-Ersteller-Alpha/issues) – mit Version, Regelwerk, Gefahrenklasse, deinen Eingaben und was du erwartet hast. Ein Screenshot hilft.

## 13 Neu am 03.11.2026

- **Timmy, der Wal:** schwimmt über freie Stellen der Seite und gibt Tipps zum aktuellen Reiter oder Ablaufschritt. Maus drüber oder anklicken → er reagiert (42 Animationen), Klick zeigt den nächsten Tipp. „Ausblenden“ schließt ihn, der kleine Wal-Knopf unten rechts holt ihn zurück.
- **Bauteile anklicken:** Im Konzeptschema (und in seiner Legende) sind Absperrarmatur, Rückflussverhinderer, Nass- und Trockenalarmventil, Sprinklerpumpe, Druckhaltepumpe und Sprinkler klickbar: Erklärung, Funktionsanimation in Schritten („Abspielen“), Kurz-Datenblatt, Fundstellen und Knopf zur eigenen Norm-PDF.
- **Sprinklerbauarten:** zusätzlich ELO (K 160/200), ESFR, Großtropfen (CMSA), erweiterte Schutzfläche, Regal-, Wohnbereichs-, Fenster-/Kühl- und Trockensprinkler. Sonderbauarten werden nach ihrer Zulassung bemessen – das Programm weist darauf hin.
- **Nennöffnungstemperatur:** Tabelle mit Glasfass-Farbe (57 … 260 °C), max. Umgebungstemperatur und Eignung für den Bereich; Zeile anklicken wählt sie aus.
- **Besondere Bereiche:** Oberlichter, Bühnen/Podeste/Galerien, Mezzanine, Fördertechnik, Lithium-Batterien – mit Hinweisen; Sprinkler unter Einbauten zählen für die Stationsgröße.
- **Pumpen-Wahl:** Größe wählen – ideal in der Mitte, kleiner und größer daneben; Diagramm mit Idealbereich und Bedarfspunkt.
- **Projektdatei:** „Projekt speichern (Datei)“ und „Projekt öffnen“ oben im Projektkasten.

## 14 Neu in 0.8.0 (03.11.2026)

- **Objektschutz** (Werkzeuge): Transformator, Maschine/Anlage, Regalstirnseite/Förderer, Kabeltrasse – benetzte Fläche, Wasserbedarf, Düsenzahl, Wasservorrat. Beaufschlagung, Betriebszeit und Düsendaten trägst du aus Norm/Richtlinie und Datenblatt ein.
- **Rippen-/Balkendecken** (Auslegung): Rippenhöhe, lichter Abstand und die Grenzwerte aus Kapitel 11 eintragen – das Programm entscheidet „unter den Rippen“ oder „in jedem Feld“ und zählt die Sprinkler.
- **Frag Timmy**: über 60 Tipps und Tricks zum Durchsuchen, mit Sprung in den passenden Reiter.
- **Feedback**: Knopf in Timmys Sprechblase – dein Kommentar geht an das Team.
- **Timmy** schwimmt jetzt wie ein Wal (Schwanzflosse auf und ab, Bögen, Loopings, Saltos).
