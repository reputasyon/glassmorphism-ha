# Glassmorphism Theme for Home Assistant

[![hacs_badge](https://img.shields.io/badge/HACS-Default-41BDF5.svg)](https://github.com/hacs/integration)
[![License](https://img.shields.io/github/license/abdullahcadirci/glassmorphism-ha)](LICENSE)

A modern **glassmorphism** UI theme for Home Assistant with frosted glass effects, blur backgrounds, and translucent cards.

![Glassmorphism Theme Preview](screenshots/preview.png)

## Features

- Frosted glass card effects with `backdrop-filter: blur()`
- Dark and Light variants
- Auto-applied card styles via `card-mod` — no manual styling per card needed
- Hover animations on cards
- Optimized for [Mushroom Cards](https://github.com/piitaya/lovelace-mushroom)
- Custom Mushroom state colors
- Translucent header and sidebar

## Screenshots

| Dark Mode | Light Mode |
|-----------|------------|
| ![Dark](screenshots/dark.png) | ![Light](screenshots/light.png) |

## Requirements

- [card-mod](https://github.com/thomasloven/lovelace-card-mod) (required for auto glass effects)
- [Mushroom Cards](https://github.com/piitaya/lovelace-mushroom) (recommended)
- [layout-card](https://github.com/thomasloven/lovelace-layout-card) (optional, for custom layouts)

## Installation

### HACS (Recommended)

1. Open HACS in Home Assistant
2. Go to **Frontend** > **3 dots menu** > **Custom repositories**
3. Add `https://github.com/abdullahcadirci/glassmorphism-ha` as **Theme**
4. Search for **Glassmorphism** and install
5. Restart Home Assistant
6. Go to **Profile** > **Theme** > Select **Glassmorphism** or **Glassmorphism Light**

### Manual Installation

1. Download `glassmorphism.yaml` from the [latest release](https://github.com/abdullahcadirci/glassmorphism-ha/releases)
2. Copy to `config/themes/glassmorphism.yaml`
3. Restart Home Assistant
4. Select the theme in your profile

## Usage

Once the theme is active, **all cards automatically get the glassmorphism effect** via `card-mod`. No need to add custom styles to each card.

### With Background Image (Recommended)

For the best glass effect, use a background image on your dashboard:

```yaml
views:
  - title: Home
    type: custom:vertical-layout
    background:
      image: /local/backgrounds/your-bg.jpg
    cards:
      - type: custom:mushroom-entity-card
        entity: switch.living_room_light
        name: Living Room
        icon: mdi:lightbulb
        tap_action:
          action: toggle
```

### Dashboard Example

```yaml
type: custom:mushroom-entity-card
entity: switch.office_led
name: Office LED
icon: mdi:led-strip-variant
icon_color: amber
tap_action:
  action: toggle
```

That's it! The theme handles the glassmorphism styling automatically.

### Manual Card Styling (Optional)

If you want to customize individual cards beyond the theme defaults:

```yaml
card_mod:
  style: |
    ha-card {
      background: rgba(255, 255, 255, 0.08) !important;
      backdrop-filter: blur(20px) saturate(180%) !important;
      -webkit-backdrop-filter: blur(20px) saturate(180%) !important;
      border: 1px solid rgba(255, 255, 255, 0.12) !important;
      border-radius: 16px !important;
      box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2) !important;
    }
```

## Customization

You can override theme variables in your `configuration.yaml`:

```yaml
frontend:
  themes: !include_dir_merge_named themes
```

## Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

## License

MIT License — see [LICENSE](LICENSE) for details.

## Credits

- Inspired by the glassmorphism design trend
- Built for the Home Assistant community
- [Mushroom Cards](https://github.com/piitaya/lovelace-mushroom) by piitaya
- [card-mod](https://github.com/thomasloven/lovelace-card-mod) by thomasloven
