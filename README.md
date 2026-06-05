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

Run this clean two-step setup to enable the necessary repositories, install dependencies, and download `rlcli` globally:

```bash
# 1. Install Raylib and compilation tools based on your Linux distribution
if command -v apt-get &> /dev/null; then
    sudo add-apt-repository universe -y && sudo apt update
    sudo apt install -y build-essential libraylib-dev
elif command -v dnf &> /dev/null; then
    sudo dnf install -y gcc gcc-c++ raylib-devel
elif command -v pacman &> /dev/null; then
    sudo pacman -Syu --noconfirm base-devel raylib
fi

# 2. Download and install the rlcli tool globally
sudo curl -sSL [https://raw.githubusercontent.com/The5xcuber/rlcli/main/rlcli](https://raw.githubusercontent.com/The5xcuber/rlcli/main/rlcli) -o /usr/local/bin/rlcli
sudo chmod +x /usr/local/bin/rlcli
