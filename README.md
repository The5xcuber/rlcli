# rlcli

Interactive Raylib Project builder that does (almost) everything like:
- The sample code for bare-minimum raylib compilation.
- Includes a tasks.json for VSCode.
- Allows you to configure different default settings for each time you make a new project, which can be configured by typing `rlcli config` in the terminal.
   - You can configure The Default Project Location for each new project.
   - You can configure The Default Dimensions for each new project.
   - You can configure The Default FPS for each new project.
- Has a `build.sh` for users not using VSCode, which builds the project by typing `./build.sh` in the terminal of the current working directory.

---

## 🚀 Installation

Follow this clean two-step setup to install the core system dependencies and deploy `rlcli` globally:

### 1. Install System Dependencies
Run the command matching your Linux distribution to install the required development graphics and audio libraries:

### Ubuntu / Debian / Linux Mint / Pop!_OS
```bash

sudo add-apt-repository universe -y && sudo apt update && sudo apt install -y build-essential git libasound2-dev libx11-dev libxrandr-dev libxi-dev libgl1-mesa-dev libglu1-mesa-dev libxcursor-dev libxinerama-dev libwayland-dev libxkbcommon-dev
```
### Fedora
```bash
sudo dnf install -y gcc gcc-c++ git alsa-lib-devel mesa-libGL-devel libX11-devel libXrandr-devel libXi-devel libXcursor-devel libXinerama-devel libatomic
```
### Arch Linux / SteamOS
```bash
sudo pacman -Syu --noconfirm base-devel git alsa-lib mesa libx11 libxrandr libxi libxcursor libxinerama
```
### Void Linux
```bash
sudo xbps-install -y make git alsa-lib-devel libglvnd-devel libX11-devel libXrandr-devel libXi-devel libXcursor-devel libXinerama-devel mesa MesaLib-devel
```
### 2. Download and Deploy rlcli
```bash
sudo curl -sSL https://raw.githubusercontent.com/The5xcuber/rlcli/main/rlcli -o /usr/local/bin/rlcli && sudo chmod +x /usr/local/bin/rlcli
echo '✓ rlcli successfully installed into /usr/local/bin/rlcli!'
```
