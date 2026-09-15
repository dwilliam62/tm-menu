#  tm-menu — Gestor de Sesiones de Tmux

[![Lenguaje: Bash / Zsh](https://img.shields.io/badge/Lenguaje-Bash%20%2F%20Zsh-4EAA25?logo=gnu-bash&logoColor=white)](#)
[![Herramienta: tmux](https://img.shields.io/badge/Herramienta-tmux-1BB954?logo=tmux&logoColor=white)](#)
[![Licencia: MIT](https://img.shields.io/badge/Licencia-MIT-blue.svg)](LICENSE)

> Un selector y gestor interactivo de sesiones de tmux para **Bash** y **Zsh**, con diseño visual enriquecido, iconos Nerd Font, indicadores de estado en tiempo real y detección inteligente de clientes tmux.

[🇺🇸 Read in English](README.md)

---

## 📋 Tabla de Contenidos

- [✨ Características](#-características)
- [🖥️ Salida de Ejemplo](#️-salida-de-ejemplo)
- [📦 Requisitos](#-requisitos)
- [🚀 Instalación y Configuración](#-instalación-y-configuración)
  - [1. Clonar el Repositorio](#1-clonar-el-repositorio)
  - [2. Hacer Ejecutable `tm-menu.sh`](#2-hacer-ejecutable-tm-menush)
  - [3. Añadir la Función `tm-menu()` a tu Shell](#3-añadir-la-función-tm-menu-a-tu-shell)
- [🎮 Modo de Uso](#-modo-de-uso)
- [📄 Licencia](#-licencia)

---

## ✨ Características

-  **Menú Interactivo**: Selección numérica rápida para conectarse o cambiar entre sesiones de tmux activas.
- 󰃰 **Fecha y Hora Exactas**: Muestra la fecha y hora de creación de la sesión (`AAAA-MM-DD HH:MM`).
- 󰖲 **Información de Ventanas**: Indica el número de ventanas abiertas en cada sesión.
- 🟢 **Indicadores de Estado en Vivo**:
  - `● attached`: Resalta las sesiones conectadas en color verde brillante (con conteo de clientes activos si hay varios).
  - `○ detached`: Muestra las sesiones desconectadas en color amarillo.
  - `(current)`: Identifica visualmente la sesión actual si se ejecuta dentro de tmux.
- 󰐕 **Crear Nuevas Sesiones al Instante**: Presiona `[n]` para crear una nueva sesión con nombre personalizado opcional.
- 󰅚 **Salida Limpia**: Presiona `[q]` para cancelar y salir sin ejecutar ningún comando.
- 🔄 **Detección Inteligente de Anidamiento**:
  - Usa `tmux attach-session -d` si estás fuera de tmux (desconectando otros clientes para evitar duplicación de pantalla).
  - Usa `tmux switch-client` si ya estás dentro de una sesión de tmux, evitando errores de anidamiento ilegal.
- 🐚 **Compatibilidad Multi-Shell**: Funciona de forma idéntica como script independiente en Bash o como función de shell en Zsh y Bash.

---

## 🖥️ Salida de Ejemplo

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

## 📦 Requisitos

- **tmux** (se recomienda versión 2.9 o superior)
- **Bash** (>= 4.0) o **Zsh** (>= 5.0)
- Un emulador de terminal con una **[Nerd Font](https://www.nerdfonts.com/)** instalada y configurada (por ejemplo, JetBrainsMono Nerd Font, FiraCode Nerd Font o Hack Nerd Font) para visualizar correctamente los iconos.

---

## 🚀 Instalación y Configuración

### 1. Clonar el Repositorio

Clona este repositorio en tu equipo:

```bash
git clone https://github.com/dwilliam62/tm-menu.git ~/src/tm-menu
cd ~/src/tm-menu
```

*(Puedes clonarlo en `~/src/tm-menu`, `~/.local/share/tm-menu` o cualquier otro directorio de tu preferencia).*

---

### 2. Hacer Ejecutable `tm-menu.sh`

Asegúrate de que el script independiente tenga permisos de ejecución:

```bash
chmod +x tm-menu.sh
```

Para poder ejecutar `tm-menu.sh` directamente desde cualquier lugar, puedes crear un enlace simbólico o copiarlo a un directorio incluido en tu `$PATH` (como `~/.local/bin`):

```bash
mkdir -p ~/.local/bin
ln -sf "$(pwd)/tm-menu.sh" ~/.local/bin/tm-menu
```

---

### 3. Añadir la Función `tm-menu()` a tu Shell

El repositorio incluye el archivo `tm-menu.bash-zsh.func`, una función autónoma lista para ser incorporada a tu configuración de terminal.

#### Opción A: Cargar el archivo directamente con `source` (Recomendado)

Añade la siguiente línea a tu `~/.zshrc` (para Zsh) o `~/.bashrc` (para Bash):

```bash
# Cargar la función tm-menu
source ~/src/tm-menu/tm-menu.bash-zsh.func
```

#### Opción B: Copiar el contenido en tu archivo de configuración o alias

Puedes anexar la función directamente en tu `~/.zshrc-personal`, `~/.zshrc` o `~/.bashrc`:

```bash
cat tm-menu.bash-zsh.func >> ~/.zshrc-personal
```

#### Aplicar los Cambios

Recarga la configuración de tu shell:

```bash
# Para Zsh:
source ~/.zshrc

# Para Bash:
source ~/.bashrc
```

---

## 🎮 Modo de Uso

Inicia el menú ejecutando:

```bash
# Si añadiste la función a tu shell o creaste el enlace simbólico en PATH:
tm-menu

# O ejecuta directamente el script independiente:
./tm-menu.sh
```

### Opciones y Controles

| Tecla | Acción |
| :---: | :--- |
| `1` – `N` | Selecciona y se conecta a la sesión número `N`. Si ya estás dentro de tmux, cambia a dicha sesión inmediatamente. |
| `n` | Crea una nueva sesión. Solicita un nombre (presiona `Enter` para usar el nombre predeterminado). |
| `q` | Cancela la operación y sale del menú de forma limpia. |

---

## 📄 Licencia

Este proyecto está bajo la [Licencia MIT](LICENSE).
