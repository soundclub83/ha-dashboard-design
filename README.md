# HA Dashboard Design

Version **0.1.0**. Gemeinsame dunkle Designbasis für Home-Assistant-Dashboards, als natives Theme. Hintergrund, Oberflächen, Textfarben, Kartenrundungen und Schatten sind zentral definiert. Raumkarten erhalten zusätzlich ihre bereits unterstützten Variablen für Innenabstände, Kachelrundungen, Kachelabstände, Überschrift und Trennlinie.

## Installation und erster Test

1. Dieses Repository im **Marketplace als Theme** hinzufügen und installieren. Es ist keine Dashboard-Karte und benötigt keine JavaScript-Ressource.
2. Themes müssen in Home Assistant geladen sein. Bei einer manuellen Theme-Aktualisierung ist gegebenenfalls `frontend.reload_themes` erforderlich; diese Aktion bewusst selbst ausführen. Ein HA-Neustart ist bei bereits eingerichteter Theme-Einbindung nicht nötig.
3. Zunächst ausschließlich in der Ansicht **Zuhause / Main** das Theme **HA Dashboard Design** auswählen. Die gespeicherte Ansichtsoption lautet:

```yaml
theme: HA Dashboard Design
```

Das ist eine einzelne Eigenschaft der vorhandenen Ansicht, keine vollständige Dashboard-Konfiguration. Beim Bearbeiten ausschließlich die bisherige `theme`-Eigenschaft ersetzen. Nicht im Benutzerprofil oder als globales Standardtheme setzen, solange der Test nur Main betreffen soll.

Das Theme gilt durch die gespeicherte Ansichtsauswahl auch auf weiteren Geräten. Die bestehende Einbindung `frontend: themes: !include_dir_merge_named themes` genügt. Das Repository selbst aktiviert keine Ansicht und verändert keine Konfiguration.

## Gemeinsame Werte

In `themes/ha-dashboard-design.yaml` stehen die zentralen Werte mit dem Präfix `design-`. Native HA-Variablen und die vorhandenen `room-control-*`-Variablen verweisen darauf. Das dunkle Design bleibt farblich gleich, auch wenn das Gerät zwischen hell und dunkel wechselt. Es enthält keine eigene Schriftart und lädt keine externen Dateien.

- Seitenhintergrund: `design-background`
- Toolbar und Oberflächen: `design-surface`
- Text, gedämpfter Text und Akzent: `design-text`, `design-muted`, `design-accent`
- Kartenverlauf, Rundung und Schatten: `design-card-background`, `design-card-radius`, `design-card-shadow`
- Raumkarten: `design-card-padding`, `design-item-gap`, `design-item-radius`, `design-title-size`, `design-header-line`

Native Karten übernehmen die von ihnen unterstützten HA-Themevariablen. Fremde Custom Cards können eigene Variablen brauchen oder feste Werte enthalten; ein Theme kann diese nicht pauschal ersetzen. Die zusätzlichen Raumkartenvariablen werden von **Room Control Card** unterstützt. Diese Trennung hält das Grunddesign unabhängig von einer bestimmten Karte.

## Schrittweise Umstellung

1. Main auswählen, Darstellung und Companion-App prüfen.
2. Danach weitere Seiten einzeln auf dasselbe Theme umstellen.
3. Dort ausschließlich nachweislich gleichwertige manuelle Grunddesign-Regeln entfernen. Harte CSS-Werte und `!important` können das Theme weiterhin übersteuern.
4. Individuelle Kartenregeln erhalten: Anwesenheitsfarben, Sichtbarkeit, Aktionen, Zustandsfarben, Zahlenformate und besondere Layouts bleiben in der jeweiligen Konfiguration.

Dieses Theme enthält keine persönlichen Entitäten und keine Aktionen. Es installiert keinen Beobachter, keine Timer, keine automatischen Reloads und keine globale CSS-Injektion. Der visuelle Praxistest steht nach Installation noch aus.

Zurücksetzen: In Main wieder das bisherige Theme auswählen. Auf der Ausgangsinstallation war dies `whatsapp_theme`. Andere Ansichten bleiben bei einer Umstellung nur von Main unverändert.

## Quellen

- [Home Assistant: Themes](https://www.home-assistant.io/integrations/frontend/)
- [Theme pro Ansicht](https://www.home-assistant.io/dashboards/views/)
- [Marketplace: Repository-Struktur für Themes](https://contributors.home-assistant.io/marketplace/reference/repository-structure/)

## Lizenz

MIT, siehe LICENSE.
