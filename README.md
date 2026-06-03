# 🎮 rlcli | Streamlined Raylib Project Manager for Linux

Setting up Raylib in C or C++ on Linux should be straightforward. `rlcli` is an interactive, zero-overhead command-line wizard built to instantly scaffold, configure, and completely isolate your Raylib projects. It handles the background plumbing and dependency mapping so you can get straight to writing game code.

---

## ⚡ Quick Start

| Command | Action |
| :--- | :--- |
| **`rlcli new`** | Launch the interactive project setup wizard |
| **`rlcli config`** | Modify your global fallback choices (Language, Res, Path) |
| **`rlcli version`** | Display current tool release version |
| **`rlcli help`** | Display the instructional help panel |

---

## 💎 Possibilities (Features & Capabilities)

* **Distro-Agnostic Setup:** Dynamically maps packages between Debian/Ubuntu (`apt`), Fedora (`dnf`), and Arch Linux (`pacman`/`yay`) to guarantee compilation works seamlessly regardless of ecosystem flavors.
* **Hardened IDE Workspace Isolation:** Automatically injects local `.vscode/tasks.json` and `.vscode/settings.json` files straight into your project. This intentionally hijacks both the native VS Code C++ "Play Button" and the *Code Runner* extension, forcing them to route through your local build configs rather than global system profiles.
* **Localized Build Containment:** Keeps your machine pristine. Unlike naive global build setups that clutter your system root or push binaries to temporary system directories like `/tmp/`, `rlcli` dumps targets neatly inside a local `./build/` folder.
* **Zero-IDE Terminal Fallback (`build.sh`):** Every project ships with a local, standalone `./build.sh` script. If VS Code acts up, your workspace settings break, or you prefer coding inside a bare-bones editor like Vim or Nano, you can completely bypass the IDE and compile/run perfectly via the native terminal.
* **Global Persistent Profiles:** Configure your recurring target preferences (default window width/height, monitor refresh rate targets, preferred coding language) using `rlcli config` to spin up future projects instantly without answering wizard prompts every time.

---

## ⚠️ Limitations (What to Watch Out For)

> [!IMPORTANT]
> Keep these operational boundaries in mind as your game project scales.

* **Linux-Specific Linker Architecture:** The embedded build flags (`-lraylib -lm -ldl -lpthread -lGL -lX11`) are strictly optimized for native Linux graphics pipelines. It does not compile Windows `.exe` formats or macOS application bundles out of the box.
* **Single-File Baseline Target:** The automation builds against a single source entry point (`main.c` or `main.cpp`). As your project expands into multiple files (e.g., `player.cpp`, `enemy.cpp`), you must open the local `./build.sh` script and append the additional compilation units directly to the `$COMPILER` instruction.
* **Shared System Library Expectation:** The utility maps binaries against globally installed system dev packages (`libraylib-dev`, `raylib-devel`, etc.). It does not automatically fetch, compile, or statically link internal local static `.a` Raylib architectures within your project trees.
* **Requires Directory Context:** For the automated VS Code workspace macros (`Ctrl + Shift + B`) to function correctly, you must open the entire project folder inside your editor, not just the isolated source file. Opening isolated source files drops workspace context and breaks IDE bindings.

---

## 📁 Generated Project Architecture

Every environment created via `rlcli new` matches this structural layout:

```text
📁 YourGameName/
├── 📄 main.cpp / main.c    <- Core game loop source entry point
├── ⚙️ build.sh              <- Standalone executable compilation script
├── 📁 .vscode/             
│   ├── ⚙️ tasks.json        <- Binds Ctrl+Shift+B to compile locally
│   └── ⚙️ settings.json     <- Forces IDE GUI buttons to call build.sh
└── 📁 build/               
    └── 🚀 YourGameName     <- The final optimized executable game binary
