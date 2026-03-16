# Waybar Switcher Setup (Omarchy)

This guide installs the Waybar theme switcher from:

`https://github.com/Sadik-Sami/waybar-switcher`

It gives you commands like:
- `omarchy-waybar`
- `omarchy-waybar-list`
- `omarchy-waybar-current`
- `omarchy-waybar-set`

## What It Does

The switcher manages Waybar themes from:

`~/.config/waybar/styles/<theme-name>/`

It uses symlinks so your active files in `~/.config/waybar/` point to the selected theme.

## Prerequisites

1. Omarchy / Hyprland with Waybar installed.
2. `git` installed.
3. `walker` installed (used for the theme menu launcher).

## Install Steps

1. Clone the repository:

```bash
git clone https://github.com/Sadik-Sami/waybar-switcher.git
cd waybar-switcher
```

2. Make installer executable:

```bash
chmod +x install.sh
```

3. Optional safety preview (no changes made):

```bash
./install.sh --dry-run
```

4. Run interactive install (recommended):

```bash
./install.sh
```

5. Optional non-interactive install:

```bash
./install.sh --yes
```

6. Optional: move your current Waybar config into `styles/default` during install:

```bash
./install.sh --move-current
```

## Hyprland Keybind

Add this to `~/.config/hypr/bindings.conf` (or your Hyprland binds file):

```ini
bind = SUPER SHIFT, W, exec, ~/.local/bin/omarchy-waybar
```

Then reload Hyprland config:

```bash
hyprctl reload
```

## Usage

List themes:

```bash
omarchy-waybar-list
```

Show active theme:

```bash
omarchy-waybar-current
```

Set a theme directly:

```bash
omarchy-waybar-set "Catppuccin"
```

Open Walker theme picker:

```bash
omarchy-waybar
```

## Where Theme Files Go

Your themes should be placed in folders like:

```text
~/.config/waybar/styles/catppuccin/
~/.config/waybar/styles/nord/
```

Each theme folder should at least include:

```text
config.jsonc
style.css
```

Optional assets:
- `scripts/`
- `modules/`
- `icons/`

## Verify Installation

1. Confirm scripts were installed:

```bash
ls ~/.local/bin/omarchy-waybar*
```

2. Confirm styles directory exists:

```bash
ls ~/.config/waybar/styles
```

3. Run the launcher:

```bash
omarchy-waybar
```

## Troubleshooting

1. Command not found:
- Ensure `~/.local/bin` is in your `PATH`.
- Or use full command path: `~/.local/bin/omarchy-waybar`.

2. Waybar does not update:

```bash
omarchy-restart-waybar
```

3. No themes visible:
- Check folders exist under `~/.config/waybar/styles/`.
- Keep theme folder names lowercase with no spaces.