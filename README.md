# HA Dashboard Design

Version **0.1.6**. Gemeinsame dunkle Designbasis für die gesamte Home-Assistant-Oberfläche und globale Standardflächen. Individuelle Karten bleiben separat konfiguriert.

## Globale Standards und individuelle Karten

Das Theme definiert Seitenhintergrund, allgemeine Oberflächen, Toolbar, Seitenleiste, Texte, Akzentfarben, Tabellen, Eingaben und Dialoge. `card-background-color` und `ha-card-background` verweisen global auf `design-surface` (#1f2c34). Dadurch übernehmen auch HA-Einstellungen, Apps, Speicher und Marketplace-Detailkarten die gemeinsame Oberfläche, sofern sie diese üblichen Variablen verwenden.

**Lokale Kartenregeln bleiben erhalten.** Explizite Hintergründe in `styles` oder card-mod, Warnfarben, Anwesenheitsfarben, Größen, Abstände, Rahmen, Rundungen, Schatten, Sichtbarkeit und Funktionen werden nicht aus dem Dashboard entfernt. CSS-Vererbung liefert Standardwerte; eine Karte kann diese lokal überschreiben. Es gibt keine globalen `!important`-Regeln für alle Karten und keine globalen Vorgaben für Kartenrundungen, Rahmen oder Abstände. Karten, die bewusst Themevariablen verwenden, folgen den neuen Standards.

## Installation

Dieses Repository im **Marketplace als Theme** installieren. Themes müssen bereits in Home Assistant eingebunden sein, beispielsweise unter `frontend` mit `themes: !include_dir_merge_named themes`.

Das Theme **HA Dashboard Design** im Profil auswählen, wenn es auf die allgemeine Oberfläche wirken soll. Alternativ oder zusätzlich eine Ansicht fest darauf einstellen:

```yaml
theme: HA Dashboard Design
```

Diese einzelne Eigenschaft ergänzt die bestehende Ansicht und ist keine vollständige Dashboard-Konfiguration. Das Repository verändert keine Dashboard-Dateien und führt keinen Neustart oder Reload automatisch aus.

## card-mod richtig laden

Globale Standardfarben funktionieren ohne card-mod. Die gezielten Media- und Verwaltungsregeln benötigen die bereits installierte Erweiterung **card-mod**. Für Regeln außerhalb von Lovelace reicht eine Dashboard-Ressource nicht: card-mod muss zusätzlich unter `frontend.extra_module_url` eingebunden werden.

Dabei **exakt die vorhandene Ressourcen-URL einschließlich Versionsparameter** übernehmen. Die von Marketplace verwaltete Ressourcenliste bleibt erhalten. Abweichende URLs können dieselbe Erweiterung doppelt laden. Nach Änderungen an `extra_module_url` ist ein bewusst freigegebener HA-Core-Neustart nötig; nach einem card-mod-Update müssen beide URLs weiterhin übereinstimmen.

[Offizielle card-mod-Anleitung](https://github.com/thomasloven/lovelace-card-mod#performance-improvements)

## Zentrale Werte

- `design-background`: Seitenhintergrund.
- `design-surface`: allgemeine Karten- und Oberflächenfarbe.
- `design-text`, `design-muted`, `design-accent`: Text- und Akzentfarben.
- `design-admin-surface`, `design-admin-border`, `design-admin-radius`: gezielte Verwaltungs-/Dialogwerte.
- `design-input-background`, `design-menu-background`: Eingaben und Menüs.
- `design-media-*`: gezieltes Mini-Media-Player-Design.

## Mini Media Player

Der `card-mod-card`-Block prüft den Kartentyp und gestaltet ausschließlich **Mini Media Player**. Er steuert Player-Hintergrund, Rahmen, Rundung, Grundfarben und die transparente interne Hintergrundfläche. Individuelle zustandsabhängige Icon-/Titel-Farben und Bedienoptionen verbleiben lokal.

Die lokalen Duplikate der fünf Player auf der ursprünglichen Media-Seite wurden nach Laden von 0.1.2 entfernt. Die übrigen Kartenstile bleiben erhalten. Voraussetzung für dieses Player-Design sind card-mod und Mini Media Player.

## Einstellungen und weitere HA-Komponenten

Die nativen HA-Variablen für Panels, Suchleisten, Tabellen, Eingaben und Dialoge wirken unabhängig vom card-mod-Konfigurationshook. Der zusätzliche `card-mod-config`-Block verwendet `ha-panel-config` statt `:host`, da dieser HA-Router im Light DOM rendert. Die darin definierten Form-/Rahmenwerte bleiben auf den Einstellungsbaum beschränkt.

Komponenten mit festen eigenen Farben können weitere gezielte Regeln benötigen. Keine automatische Änderung an Entitäten, Aktionen, Sichtbarkeit, Daten oder Layouts. Keine externen Schriftarten, keine eigenen Timer und keine JavaScript-Injektion durch dieses Repository.

## Prüfung und Wechsel von älteren Versionen

0.1.0 koppelte auch Kartenrundungen und weitere Kartendetails global. Diese Kopplung wurde entfernt; die damals gelöschten lokalen Kartenstile auf der ursprünglichen Installation wurden aus Backups wiederhergestellt. Ab 0.1.5 werden ausschließlich allgemeine Hintergrundstandards wieder global gesetzt, bei erhaltener lokaler Gestaltung.

Geprüft: YAML, Variablenverweise und unveränderte gezielte Player-Regeln. Eine visuelle Prüfung von 0.1.5 erfolgt nach Marketplace-Installation. Nicht alle HA-Unterseiten sind allein durch diese Prüfung abgedeckt.

## Quellen

- [Home Assistant: Themes und globale Oberflächenvariablen](https://www.home-assistant.io/integrations/frontend/)
- [Theme pro Ansicht](https://www.home-assistant.io/dashboards/views/)
- [card-mod-Themes](https://github.com/thomasloven/lovelace-card-mod/wiki/Card-mod-Themes)
- [Vergleich: WhatsApp Theme](https://github.com/robinwittebol/whatsapp-theme)

## Lizenz

MIT, siehe LICENSE.


## Wetter und DWD-Warnkarte ab 0.1.6

Die `design-weather-*`-Werte bestimmen Rahmenfläche, Verlauf, Rand, Rundung, Schatten, Innenabstand, Text-/Akzentfarben sowie die Überschrift mit Trennlinie. Der `card-mod-card`-Block gestaltet gezielt `custom:clock-weather-card` transparent innerhalb des Rahmens. Dessen Wetterdaten, Optionen und funktionale Balkenkorrekturen bleiben lokal.

Eine äußere `custom:button-card` erhält `design_role: weather-frame`. Nur ausdrücklich markierte Wetterrahmen werden durch diesen Block gestaltet; andere Button-Karten bleiben unverändert. Die Bubble-Überschrift verwendet weiterhin einen kurzen lokalen Stilblock, der die zentralen `design-weather-header-*`-Variablen bindet. Layout und Abstände zwischen den Elementen bleiben Teil der Kartenanordnung.

Eine DWD-Markdownkarte erhält `design_role: dwd-warning`. Das Theme übernimmt Rundung, Innenabstand, Typografie und die fünf Warnfarben (`design-warning-level-0-rgb` bis `design-warning-level-4-rgb`) samt Hintergrund-/Rahmendeckkraft. Die bestehende lokale Warnstufenlogik setzt ausschließlich `--design-warning-rgb` auf eine dieser Variablen. Warntexte, Zeitangaben, Entitäten, Vorwarnung und Zustandsauswertung bleiben unverändert. Das Theme fragt selbst keine persönlichen DWD-Entitäten ab.

Die vorhandenen lokalen Regeln erst nach Installation und bewusst freigegebenem Laden von 0.1.6 auf die zentralen Werte umstellen. Das Repository verändert keine Dashboards und löst keinen Reload aus. Andere Markdownkarten bekommen keine Warnfarben. Der bisherige Mini-Media-Player-Block bleibt erhalten.

Prüfung: YAML und Variablen, neun HA-Template-Fälle einschließlich fehlender Konfiguration und unveränderter anderer Kartentypen. Visuelle Prüfung folgt nach Installation und Umstellung der markierten Karten.
