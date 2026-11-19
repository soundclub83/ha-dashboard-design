# Changelog

## 0.1.8

- Native Clock-Weather-Titel verwenden die zentralen Größen, Schriftstärke und Trennlinie.
- Dekoratives Wetter-/Uhr-/Kalendericon abhängig von der Vorhersageart; Titeltext bleibt im GUI-Editor bearbeitbar.
- Keine zusätzliche Karte oder Hülle.


## 0.1.7

- Clock Weather Card erhält den Wetterrahmen direkt statt eines transparenten Inhalts für verschachtelte Hüllen.
- Ermöglicht direkt im Dashboard editierbare Wetterkarten mit nativen Sichtbarkeitsregeln; Warnkartendesign unverändert.


## 0.1.6

- Zentrale Designwerte und gezielte Theme-Regeln für markierte Wetterrahmen und DWD-Warnkarten.
- Clock Weather Card erhält einen gezielten transparenten Inhaltshintergrund und zentrale Text-/Akzentwerte.
- Überschriftenvariablen für Bubble-Separatoren; lokale Bindung bleibt nötig.
- Warnstufenlogik, Wetterfunktionen und individuelle andere Karten bleiben erhalten.
- YAML und neun HA-Template-Fälle erfolgreich geprüft; Live-Sichtprüfung nach Installation ausstehend.

## 0.1.5

- Globale Standardhintergründe für Karten-/Menüflächen nach dem Vorbild eines vollständigen HA-Themes.
- card-background-color und ha-card-background verwenden die gemeinsame Oberfläche statt HA-Schwarz.
- Lokale Kartenhintergründe, Warnfarben und individuelle Layouts bleiben in den Dashboard-Konfigurationen erhalten.
- Keine globalen Vorgaben für Kartenrundungen, Rahmen, Schatten, Größen oder Abstände.
- Gezielter Media-Block bleibt erhalten. Für card-mod-Regeln außerhalb Lovelace muss card-mod als extra_module_url geladen werden.

## 0.1.4

- Korrigiert card-mod-config für den Light-DOM-Router ha-panel-config: Elementselektor statt unwirksamem :host.
- Die begrenzten Oberflächenvariablen können dadurch an Einstellungsunterseiten wie Apps und Speicher vererbt werden.
- Media-Regeln, Dashboard-Karten und native Marketplace-Tabellenvariablen unverändert.
- Marketplace-Detailseiten besitzen einen separaten Panel-Root; deren schwarzen Kartenflächen sind mit dieser Korrektur noch nicht abgedeckt.

## 0.1.3

- Allgemeine Panel-, Suchleisten- und Tabellenhintergründe für Einstellungen und Marketplace.
- Einheitliche Eingabefarben und Dialogoberflächen.
- Kartenoberflächen im Einstellungsbereich ausschließlich über card-mod-config begrenzt.
- Dialog- und More-info-Variablen nur innerhalb der jeweiligen Dialoge.
- Keine globalen ha-card- oder room-control-Variablen; Media-Block bleibt kartentypspezifisch.
- Sicherer Media-Template-Guard für Komponenten ohne config.type.

## 0.1.2

- Gemeinsame Grundwerte für Mini Media Player zentral im Theme.
- Ausschließlich dieser Kartentyp erhält Hintergrund, Rahmen, Rundung, Text- und Akzentfarben über card-mod.
- Eigene Hintergrundfläche des Players wird transparent; andere Kartentypen bleiben unberührt.
- Individuelle zustandsabhängige Farben verbleiben lokal.
- Lokale Duplikate erst nach Installation und Laden von 0.1.2 entfernen.

## 0.1.1

- Trennt allgemeine Oberfläche und individuelles Kartendesign.
- Entfernt globale ha-card- und room-control-Variablen sowie kartenspezifische Designwerte.
- Keine Vorgaben mehr für Kartenhintergründe, Rundungen, Rahmen, Schatten, Kachelabstände und Kartenüberschriften.
- Seitenhintergrund, Toolbar, Seitenleiste und allgemeine Text-/Akzentfarben bleiben zentral.
- Die in 0.1.0 entfernten lokalen Kartenstile müssen aus dem jeweiligen Backup wiederhergestellt werden; ein Theme-Update kann gelöschte Dashboard-Regeln nicht zurückbringen.

## 0.1.0

- Erste Themebasis mit globalen Kartenvariablen. Diese Kopplung wird mit 0.1.1 entfernt.
