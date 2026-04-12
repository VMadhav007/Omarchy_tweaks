Here you go — clean, ready to **copy-paste directly into a `.md` file**:

````md
# 🗑️ Removing `pokemon-colorscripts`

You’ve got two different “remove” meanings here — pick what applies.

---

## 1. Remove Pokémon from Terminal Startup (Most Likely)

If a Pokémon appears every time you open your terminal, it was added to your shell config.

### Open your shell config

**Bash**
```bash
nano ~/.bashrc
````

**Zsh**

```bash
nano ~/.zshrc
```

### Remove this line

```bash
pokemon-colorscripts -r
```

### Apply changes

```bash
source ~/.bashrc   # Bash
source ~/.zshrc    # Zsh
```

---

## 2. Uninstall the Package

If you installed using `yay`:

```bash
yay -Rns pokemon-colorscripts-git
```

---

## 3. Verify Removal

```bash
which pokemon-colorscripts
```

* No output → fully removed
* Path shown → remove manually

---

## 4. Manual Cleanup (if needed)

```bash
sudo rm -f /usr/local/bin/pokemon-colorscripts
```

---

## ✅ Done

* No more Pokémon on startup
* Tool completely removed

```
```
