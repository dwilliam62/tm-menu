#  tm-menu — Tmux Session Manager

[![Language: Bash / Zsh](https://img.shields.io/badge/Language-Bash%20%2F%20Zsh-4EAA25?logo=gnu-bash&logoColor=white)](#)
[![Tool: tmux](https://img.shields.io/badge/Tool-tmux-1BB954?logo=tmux&logoColor=white)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

> An interactive, beautifully formatted tmux session switcher and manager for **Bash** and **Zsh**, featuring Nerd Font icons, real-time status indicators, and smart tmux client awareness.

[🇪🇸 Leer en Español](README.es.md)

---

## 📋 Table of Contents

- [✨ Features](#-features)
- [🖥️ Sample Output](#️-sample-output)
- [📦 Requirements](#-requirements)
- [🚀 Installation & Setup](#-installation--setup)
  - [1. Clone the Repository](#1-clone-the-repository)
  - [2. Make `tm-menu.sh` Executable](#2-make-tm-menush-executable)
  - [3. Add the `tm-menu()` Function to Your Shell](#3-add-the-tm-menu-function-to-your-shell)
- [🎮 Usage](#-usage)
- [📄 License](#-license)

---

## ✨ Features

-  **Interactive Menu**: Quick numbered selection to attach or switch between running tmux sessions.
- 󰃰 **Accurate Creation Timestamp**: Displays the exact creation date and time (`YYYY-MM-DD HH:MM`).
- 󰖲 **Window Information**: Shows the number of windows open in each session.
- 🟢 **Live Status Indicators**:
  - `● attached`: Highlights currently attached sessions in bright green (including multi-client count).
  - `○ detached`: Shows inactive sessions in yellow.
  - `(current)`: Identifies the active session when running inside tmux.
- 󰐕 **Create New Sessions on the Fly**: Press `[n]` to spawn a new session with an optional custom name.
- 󰅚 **Clean Exit**: Press `[q]` to cancel without running any commands.
- 🔄 **Smart Nesting Detection**:
  - Uses `tmux attach-session -d` when outside tmux (detaching other clients to avoid mirroring).
  - Uses `tmux switch-client` when already inside a tmux session to prevent illegal nesting errors.
- 🐚 **Dual-Shell Compatibility**: Runs seamlessly as a standalone script in Bash or as a shell function in Zsh and Bash.

---

## 🖥️ Sample Output

```text
tm-menu

  ╭──────────────────────────────────────────────────────────────────────────╮
  │                          TMUX SESSION MANAGER                           │
  ╰──────────────────────────────────────────────────────────────────────────╯

  NUM   SESSION            WINDOWS       CREATED             STATUS
  ───   ─────────────────  ────────────  ──────────────────  ──────────
  [1]    1                󰖲 1 Work       󰃰 2026-09-14 18:37  ○ detached
  [2]    2                󰖲 1 Dev        󰃰 2026-09-14 18:41  ○ detached

  [n] 󰐕 New session       [q] 󰅚 Cancel

Select a session [1-2, n, q]: 
```

---

## 📦 Requirements

- **tmux** (version 2.9 or newer recommended)
- **Bash** (>= 4.0) or **Zsh** (>= 5.0)
- A terminal emulator configured with a **[Nerd Font](https://www.nerdfonts.com/)** (e.g., JetBrainsMono Nerd Font, FiraCode Nerd Font, Hack Nerd Font) for icons to render properly.

---

## 🚀 Installation & Setup

### 1. Clone the Repository

Clone this repository to your local machine:

```bash
git clone https://github.com/dwilliam62/tm-menu.git ~/src/tm-menu
cd ~/src/tm-menu
```

*(You can clone it into `~/src/tm-menu`, `~/.local/share/tm-menu`, or any directory of your choice).*

---

### 2. Make `tm-menu.sh` Executable

Ensure the standalone script has execution permissions:

```bash
chmod +x tm-menu.sh
```

To run `tm-menu.sh` directly from anywhere, symlink or copy it to a directory in your `$PATH` (e.g., `~/.local/bin`):

```bash
mkdir -p ~/.local/bin
ln -sf "$(pwd)/tm-menu.sh" ~/.local/bin/tm-menu
```

---

### 3. Add the `tm-menu()` Function to Your Shell

The repository includes `tm-menu.bash-zsh.func`, a self-contained shell function that can be added to your interactive shell configuration.

#### Option A: Source the file directly (Recommended)

Add this line to your `~/.zshrc` (for Zsh) or `~/.bashrc` (for Bash):

```bash
# Source tm-menu function
source ~/src/tm-menu/tm-menu.bash-zsh.func
```

#### Option B: Copy into your personal aliases / configuration file

You can copy the function directly into your `~/.zshrc-personal`, `~/.zshrc`, or `~/.bashrc`:

```bash
cat tm-menu.bash-zsh.func >> ~/.zshrc-personal
```

#### Apply Changes

Reload your shell configuration:

```bash
# For Zsh:
source ~/.zshrc

# For Bash:
source ~/.bashrc
```

---

## 🎮 Usage

Launch the menu by running:

```bash
# If you added the shell function or symlinked to PATH:
tm-menu

# Or execute the standalone script directly:
./tm-menu.sh
```

### Options & Controls

| Key | Action |
| :---: | :--- |
| `1` – `N` | Select and attach to session number `N`. If already inside tmux, it switches to that session. |
| `n` | Create a new session. Prompts for a session name (press `Enter` for auto-generated default). |
| `q` | Cancel and exit the menu cleanly. |

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
