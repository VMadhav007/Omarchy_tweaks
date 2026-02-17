```
# Hyprland Animations Tweaks

## Installation

1. Copy `animations.conf` to your Hyprland config directory:
```bash
cp animations.conf ~/.config/hypr/
```

2. Source this file in your main `hyprland.conf`:
```bash
source = ~/.config/hypr/animations.conf
```

## Usage

This file contains multiple animation presets. **Uncomment only ONE animations block at a time** to use your preferred preset:

- **Gnomeish** - Smooth, GNOME-inspired animations (lines 1-9)
- **Slight bounce at last** - Active by default with subtle bounce effect (lines 31-50)
- **Standard** - Basic Hyprland animations (lines 60-70)
- **Vertical** - Vertical slide animations by Itz-Abhishek-Tiwari (lines 84-107)
- **Dynamic** - Dynamic slide animations by mylinuxforwork (lines 121-137)

### Customizing Active Preset

Within the active animations block, you can also uncomment specific animation lines to enable:
- Window animations (slide, fade, border effects)
- Workspace transitions
- Border angle animations

Comment out the entire current block and uncomment your desired preset, then reload Hyprland.
```