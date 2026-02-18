# Hyprland Monitor Toggle (eDP-1 ↔ External Monitor)

This repository provides a simple script to toggle the laptop display (eDP-1) on and off while keeping an external monitor (e.g. HDMI-A-1) always enabled.

Useful for Omarchy / Hyprland users who dock and undock frequently.

## What This Does

**Super + M** → Toggle eDP-1

- Enabled → Disabled
- Disabled → Enabled
- HDMI-A-1 stays enabled at all times

Uses `hyprctl`, no `nwg-displays`, no GUI state corruption.

## Target Setup

```conf
monitor = eDP-1, preferred, auto, 1
monitor = HDMI-A-1, preferred, auto, 1
```

Toggle behavior:

- Dual monitor → external only
- External only → dual monitor

## Requirements

- Hyprland
- `hyprctl` available in `$PATH`
- Any shell (bash, zsh, etc.)
- No GUI tools required

## Installation

### 1. Create the script directory

```bash
mkdir -p ~/.local/bin
```

### 2. Create the toggle script

If you don't have nano, this works everywhere:

```bash
cat << 'EOF' > ~/.local/bin/toggle-edp.sh
#!/usr/bin/env bash

if hyprctl monitors | grep -q "eDP-1"; then
    hyprctl keyword monitor "eDP-1,disable"
    hyprctl keyword monitor "HDMI-A-1,preferred,auto,1"
else
    hyprctl keyword monitor "eDP-1,preferred,auto,1"
    hyprctl keyword monitor "HDMI-A-1,preferred,auto,1"
fi
EOF
```

Make it executable:

```bash
chmod +x ~/.local/bin/toggle-edp.sh
```

### 3. Bind the script to Super + M

Edit your Hyprland config:

```bash
vi ~/.config/hypr/hyprland.conf
```

Add:

```conf
bind = SUPER, M, exec, ~/.local/bin/toggle-edp.sh
```

Reload Hyprland:

```bash
hyprctl reload
```

## Usage

Press **Super + M** to toggle the laptop display.

- HDMI monitor remains active
- No restart required

You can also run it manually:

```bash
~/.local/bin/toggle-edp.sh
```

## Troubleshooting

### Laptop screen does not toggle correctly

Check monitor names:

```bash
hyprctl monitors
```

If your external monitor is not `HDMI-A-1`, update the script accordingly.

### nano: command not found

Omarchy does not install nano by default.

Options:

- Use `vi`
- Or install nano manually:

```bash
sudo pacman -S nano
```

### nwg-displays broke my setup

Remove its config to avoid overrides:

```bash
rm -rf ~/.config/nwg-displays
```

Then reload or reboot.
