# Archonw Themes for Home Assistant

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://hacs.xyz/)
[![Validate](https://github.com/Archonw/ha-themes/actions/workflows/validate.yml/badge.svg)](https://github.com/Archonw/ha-themes/actions/workflows/validate.yml)

A small collection of Home Assistant themes. All themes live in one file, so a single
HACS install gives you all of them.

*Deutsche Beschreibung weiter unten.*

## Themes

| Theme | Mode | Description |
| --- | --- | --- |
| **Dynaframe** | dark | Warm dark brown with gold accents, modelled on the [Dynaframe™](https://geek-toolkit.com/) web UI. Pairs well with the [Dynaframe integration](https://github.com/Archonw/dynaframe-homeassistant). |

## Installation

### HACS (recommended)

1. HACS → ⋮ → **Custom repositories**
2. Repository: `https://github.com/Archonw/ha-themes`, type **Theme**
3. Download **Archonw Themes**
4. Run the action `frontend.reload_themes` (or restart Home Assistant)
5. Profile → **Theme** → choose a theme. To make it the default for everyone, run
   `frontend.set_theme` with `name: Dynaframe`.

Your `configuration.yaml` needs the themes folder enabled (most installations already have this):

```yaml
frontend:
  themes: !include_dir_merge_named themes
```

### Manual

Copy `themes/ha-themes.yaml` into the `themes` folder of your Home Assistant configuration
and run `frontend.reload_themes`.

## Notes

- The Dynaframe theme uses the font *Inter* if it is installed on the device, otherwise the
  system font. A theme cannot load web fonts on its own.
- Colors on media player cards (album art) and calendar dots come from the cards and
  calendars, not from the theme.

## Adding a theme

Append a new top-level block to `themes/ha-themes.yaml`. Shared values can be defined once
with a YAML anchor and merged into other themes:

```yaml
Dynaframe:
  modes:
    dark:
      ha-card-border-radius: &radius "16px"
      # ...

My New Theme:
  ha-card-border-radius: *radius
  primary-color: "#4caf50"
```

---

## Deutsch

Eine kleine Sammlung von Home-Assistant-Themes in einer Datei – eine Installation über HACS
bringt alle Themes mit.

**Installation:** HACS → ⋮ → *Benutzerdefinierte Repositories* →
`https://github.com/Archonw/ha-themes` als **Theme** hinzufügen, „Archonw Themes“
herunterladen, `frontend.reload_themes` ausführen und das Theme im Profil auswählen.

**Dynaframe:** dunkles Braun mit goldenen Akzenten, angelehnt an die Dynaframe-Oberfläche.

## Authors

- **Jan** ([@Archonw](https://github.com/Archonw)) – idea, testing and maintenance
- **Claude** (AI assistant by [Anthropic](https://www.anthropic.com), via
  [Claude Code](https://claude.com/claude-code)) – theme design and implementation

## License

[MIT](LICENSE) – not affiliated with or endorsed by Dynaframe™.
