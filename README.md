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

Run this single command in your terminal to automatically check dependencies, install Raylib development packages, and deploy `rlcli` globally to your system:

```bash
curl -sSL [https://raw.githubusercontent.com/The5xcuber/rlcli/main/rlcli](https://raw.githubusercontent.com/The5xcuber/rlcli/main/rlcli) | sudo bash -c '
    if command -v apt-get &> /dev/null; then
        apt-get update && apt-get install -y build-essential libraylib-dev
    elif command -v dnf &> /dev/null; then
        dnf install -y gcc gcc-c++ raylib-devel
    elif command -v pacman &> /dev/null; then
        pacman -Syu --noconfirm base-devel raylib
    else
        echo "⚠️ Distro package manager not recognized. Please install Raylib manually."
    fi
    cat > /usr/local/bin/rlcli
    chmod +x /usr/local/bin/rlcli
    echo "✓ rlcli installed successfully into /usr/local/bin/rlcli!"
'
