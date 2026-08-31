# Input - Linux Version

Unofficial community builds of the Work Louder **Input** app for Linux, distributed as AppImages.

This repository is used to publish Linux releases of Input. The app itself is **closed source**, so no source code is hosted here. It is a **community build**, maintained on a best-effort basis with **no support promised**.

## ⚠️ Disclaimer

This project is an **unofficial community-developed** port of the Input application, intended for use on Linux systems.

While this project has been acknowledged and welcomed by Work Louder Inc., it is **not officially supported** or maintained by them. As such, functionality and stability are not guaranteed.

### Important Notes

- This software is provided **"as is"**, without any warranties, express or implied.
- Use at your own risk.
- **Work Louder does not guarantee the safety, integrity, or reliability of any files downloaded from this repository or related sources.** Users are responsible for reviewing and validating the software before installation.
- Work Louder cannot be held liable for any damages or legal claims resulting from the use or distribution of this software.

By using, copying, modifying, or distributing this software, **you agree to these terms**.

---

## Installation

Grab the latest `.AppImage` from the [Releases page](https://github.com/worklouder/input-linux/releases).

The recommended way to install it is with [Gear Lever](https://flathub.org/apps/it.mijorus.gearlever), which integrates AppImages into your app menu and keeps them organized. Input does not create its own desktop file when the AppImage is run by hand, though it will install one for autostart once launched.

```bash
flatpak install flathub it.mijorus.gearlever
```

To run it standalone instead:

```bash
chmod +x Input-*.AppImage
./Input-*.AppImage
```

Recent builds use a FUSE 3 AppImage runtime, which nearly all current distros ship out of the box. If the AppImage refuses to start with a FUSE error, install it per the table below.

### Distro-specific setup

| Distro | FUSE (if needed) | Optional extras |
| --- | --- | --- |
| **Ubuntu / Debian / Mint** | `sudo apt install fuse3` (older builds: `libfuse2` / `libfuse2t64`) | `sudo apt install xdotool` for the insert-text smart action |
| **Fedora / Nobara** | preinstalled (`fuse3`) | `sudo dnf install xdotool` |
| **Arch / Manjaro / EndeavourOS** | `sudo pacman -S fuse3` | `sudo pacman -S xdotool`; `kdotool` (AUR) for KDE Wayland focus detection |
| **openSUSE** | preinstalled (`fuse3`) | `sudo zypper install xdotool` |

A polkit agent must be running for the first-launch udev prompt (every mainstream desktop ships one).

### Desktop environment notes

Most differences between setups come from the desktop environment and display server, not the distro:

- **GNOME (Wayland)**: install the [AppIndicator extension](https://extensions.gnome.org/extension/615/appindicator-support/) for the tray icon. For reliable focused-app detection (app-linked profiles), install the [Focused Window D-Bus extension](https://extensions.gnome.org/extension/5592/focused-window-d-bus/); the app will hint at this when needed.
- **GNOME (X11)**: AppIndicator extension for the tray; focus detection works out of the box.
- **KDE Plasma**: tray works out of the box. On Wayland, install `kdotool` for focus detection; on X11 it works without it.
- **Hyprland / Sway**: focus detection uses the compositor's own IPC and works out of the box. You'll need a tray-capable bar (waybar etc.) and a polkit agent running.
- **XFCE / Cinnamon / MATE (X11)**: everything works out of the box.

### Automatic compatibility detection

You generally don't need to work the tables above out by hand. Input inspects your
distro, desktop environment and display server at runtime, figures out which features
your setup can support, and prompts you when a third-party tool or extension would
unlock one. On first launch it offers to install the udev rules it needs for device
access, and when a feature such as focused-app detection needs extra help (for example
a GNOME extension or `kdotool` on KDE Wayland), the app points you at the right tool
at the moment you try to use it. The sections above are there as a reference if you
prefer to set things up ahead of time or something goes wrong.

---

## Feature parity with Windows / macOS

The Linux build targets full parity with the official app. Current status:

| Feature | Status on Linux | Notes |
| --- | --- | --- |
| Device configuration (keymaps, layers, profiles, lighting, widgets, wallpapers) | ✅ Full | Talks to the device directly, platform-independent |
| Firmware updates and flashing (DFU) | ✅ Full |     |
| USB connection | ✅ Full | udev rules installed on first launch |
| Bluetooth connection | ✅ Full | A fix for mixed USB + Bluetooth setups is on its way upstream |
| App auto-updates | ✅ Full | AppImage only; updates come from this repository |
| Media player widget | ✅ Full | Uses MPRIS, so it works with virtually every Linux media player and browser |
| Radial menu and cheat sheet overlays | ✅ Full |     |
| Smart actions: open app, open URL, run command | ✅ Full | App list includes Flatpak and Snap apps |
| Smart action: insert text | ⚠️ Partial | Requires `xdotool`; on Wayland it can only type into XWayland windows |
| Focused-app detection (app-linked profiles) | ⚠️ Varies by desktop | Solid on X11, GNOME, Hyprland and Sway; see desktop notes above |
| Tray icon | ✅ Full | GNOME needs the AppIndicator extension |
| Autostart | ✅ Full | XDG autostart entry, managed by the app |
| Notifications and alerts | ✅ Full |     |

Distro choice barely matters: Ubuntu, Fedora, Arch, Debian and derivatives all behave the same once the dependencies above are in place. The desktop environment and X11-vs-Wayland are what determine the ⚠️ rows.

---

## Device Access (udev rules)

Input should automatically prompt you to set up the udev rules needed to access your Work Louder device on first launch. If your device isn't detected, **unplug and replug it** after launching the app once.

---

## Support

**No official support is provided**, not by Work Louder, and none is promised by the maintainer.

For community help, questions, and discussion, join the Discord server:

👉 **[https://discord.gg/yD9ay7sEdt](https://discord.gg/yD9ay7sEdt)**

Issues opened on this repository may be addressed on a best-effort basis, but there is no guarantee of a response or fix.

---

## About the Legacy Build Script

Earlier versions of this repository provided a script (`input4linux-*.sh`) that downloaded the official Windows installer and patched it to run on Linux. That approach is **deprecated and no longer maintained**. Use the AppImages from the Releases page instead.

---

## License

This project does not claim ownership of Input. Input is a product of Work Louder Inc. This port is provided under an unofficial and permissive approach intended to help Linux users make use of their devices. Refer to the individual license files, if applicable.
