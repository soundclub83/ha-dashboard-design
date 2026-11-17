# HA Dashboard Design

Version **0.1.2**. Native dunkle Themebasis für die allgemeine Home-Assistant-Oberfläche. Das Theme steuert Seitenhintergrund, Toolbar, Seitenleiste sowie allgemeine Text- und Akzentfarben.

## Trennung vom Kartendesign

Kartenhintergründe, Rahmen, Rundungen, Schatten, Innenabstände, Kachelgrößen und Überschriften gehören zur Karte. Das Theme definiert dafür weder globale `ha-card-*` noch `room-control-*`-Variablen. Für Mini Media Player gibt es ab 0.1.2 einen ausdrücklich auf diesen Kartentyp begrenzten Designblock. Vorhandene Karteneinstellungen und card-mod-Stile bleiben bestehen, auch wenn ein Farbwert zufällig dem allgemeinen Theme entspricht.

Allgemeine Text-/Akzentfarben und Oberflächenvariablen können nach den Regeln von Home Assistant auch von Karten geerbt werden. Eine Karte, die ihre Farben unabhängig festlegt, muss diese selbst definieren. Das Theme schreibt keine individuellen Zustands-, Anwesenheits- oder Warnfarben vor.

## Installation und Auswahl

Dieses Repository im **Marketplace als Theme** hinzufügen und installieren. Keine JavaScript-Ressource erforderlich. Die vorhandene Konfiguration `frontend: themes: !include_dir_merge_named themes` genügt.

In der Ansicht oder im Profil **HA Dashboard Design** auswählen. Eine feste Ansichtszuweisung lautet:

```yaml
theme: HA Dashboard Design
```

Das ist eine einzelne Eigenschaft einer vorhandenen Ansicht, keine vollständige Dashboard-Konfiguration. Eine Profilauswahl gilt auch für die allgemeine Oberfläche. Es werden keine Konfigurationen automatisch verändert.

Nach Installation bei Bedarf Themes bewusst selbst neu laden (`frontend.reload_themes`). Kein HA-Neustart bei bereits eingerichteter Theme-Einbindung erforderlich.

## Wechsel von 0.1.0

0.1.0 enthielt globale Kartenvariablen. 0.1.1 entfernt diese Kopplung. Lokale Kartenstile, die während der ersten Umstellung entfernt wurden, müssen zusätzlich aus dem Backup wiederhergestellt werden. Auf der ursprünglichen Installation wurden diese bereits vor dem Update gezielt wiederhergestellt. Das Theme kann keine gelöschten Dashboard-Regeln rekonstruieren.

Der Themewechsel verändert weder Entitäten, Aktionen, Sichtbarkeit noch die Anordnung. Keine Timer, automatischen Reloads, externe Schriftarten oder CSS-Injektion. Der visuelle Test der korrigierten Themeversion folgt nach Installation.

## Quellen

- [Home Assistant: Themes](https://www.home-assistant.io/integrations/frontend/)
- [Theme pro Ansicht](https://www.home-assistant.io/dashboards/views/)
- [Marketplace: Theme-Struktur](https://contributors.home-assistant.io/marketplace/reference/repository-structure/)

## Lizenz

MIT, siehe LICENSE.

## Mini Media Player ab 0.1.2

Voraussetzung: **card-mod** und **Mini Media Player**. Die allgemeine Oberfläche funktioniert ohne diese Erweiterungen; die Player-Gestaltung braucht beide. Die bestehende Installation nutzt diese bereits.

Die `design-media-*`-Werte steuern Hintergrund, Rahmen, Rundung, Text, gedämpften Text und Akzent. Ein `card-mod-card`-Template prüft ausdrücklich `config.type == 'custom:mini-media-player'`. Alle anderen Kartentypen bekommen daraus keine CSS-Regeln. Die unterstützten Variablen `mini-media-player-accent-color` und `mini-media-player-base-color` gelten ausschließlich für Player, die sie auswerten.

Nach Installation **und Laden** von Theme 0.1.2 können die identischen lokalen `ha-card`-Grundwerte, die lokale `.mmp__bg`-Korrektur und die zwei konstanten Player-Farbvariablen entfernt werden. Zustandsabhängige Icon-/Titel-Farben und alle funktionalen Optionen verbleiben an der Karte. Vorher Backup anlegen. Die visuellen Ergebnisse und die Theme-Anbindung auf den eingesetzten Playern sind nach Installation zu prüfen.

[card-mod: Theme-Unterstützung](https://github.com/thomasloven/lovelace-card-mod/wiki/Card-mod-Themes)
