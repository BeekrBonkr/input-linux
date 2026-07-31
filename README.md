# Input - Linux Version

Unofficial community builds of the Work Louder **Input** app for Linux, distributed as AppImages.

This repository is used to publish Linux releases of Input. The app itself is **closed source** — no source code is hosted here. It is a **community build**, maintained on a best-effort basis with **no support promised**.

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

Download the latest `.AppImage` from the [Releases Page](https://github.com/worklouder/input-linux/releases).

Make it executable and run it:

```bash
chmod +x Input-*.AppImage
./Input-*.AppImage
```

For desktop integration (menu entries, updates), we recommend a tool like [Gear Lever](https://flathub.org/apps/it.mijorus.gearlever).

You may need FUSE for the AppImage to run:

```bash
# Ubuntu/Debian
sudo apt install libfuse2
```

---

## Device Access (udev rules)

Input should automatically set up the udev rules needed to access your Work Louder device on first launch. If your device isn't detected, **unplug and replug it** after launching the app once.

---

## Support

**No official support is provided** — not by Work Louder, and none is promised by the maintainer.

For community help, questions, and discussion, join the Discord server:

👉 **[https://discord.gg/yD9ay7sEdt](https://discord.gg/yD9ay7sEdt)**

Issues opened on this repository may be addressed on a best-effort basis, but there is no guarantee of a response or fix.

---

## About the Legacy Build Script

Earlier versions of this repository provided a script (`input4linux-*.sh`) that downloaded the official Windows installer and patched it to run on Linux. That approach is **deprecated and no longer maintained** — use the AppImages from the Releases page instead.

---

## License

This project does not claim ownership of Input. Input is a product of Work Louder Inc. This port is provided under an unofficial and permissive approach intended to help Linux users make use of their devices. Refer to the individual license files, if applicable.
