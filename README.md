# Portmaster band72 Build

Unofficial Windows and Linux build of the open-source [Portmaster](https://github.com/safing/portmaster) application firewall, with extra tools for seeing what your programs do.

> **Not made or supported by Safing.** This is a modified version made by band72. For the official Portmaster, go to [safing.io/download](https://safing.io/download/).

## Download

- **[⬇ Windows (64-bit installer)](https://github.com/band72/portmaster-releases/releases/latest/download/Portmaster-band72-windows-x64-setup.exe)**
- **[⬇ Linux .deb (Debian, Ubuntu, Mint)](https://github.com/band72/portmaster-releases/releases/latest/download/Portmaster-band72-linux-amd64.deb)** · `sudo apt install ./Portmaster-band72-linux-amd64.deb`
- **[⬇ Linux .rpm (Fedora, openSUSE, RHEL)](https://github.com/band72/portmaster-releases/releases/latest/download/Portmaster-band72-linux-x86_64.rpm)** · `sudo dnf install ./Portmaster-band72-linux-x86_64.rpm`

Download page: https://band72.github.io/portmaster-releases/ · [All releases](https://github.com/band72/portmaster-releases/releases)

The installer is not code-signed, so Windows SmartScreen shows "Windows protected your PC". Choose **More info**, then **Run anyway**. Each release lists the SHA-256 of its files to check the download:

```powershell
Get-FileHash .\Portmaster-band72-windows-x64-setup.exe
```

On Linux, check with `sha256sum Portmaster-band72-linux-*`, install the package, then restart the computer.

## What this build adds

- **System Monitor**: total and per-process CPU, memory, user and Windows service, plus temperatures where the computer reports them.
- **Process Intelligence Report**: for any running program, its digital signature, privileges, open sensitive files, camera and microphone use, injected code, network destinations and listening ports, with a risk rating.
- **Force block per app**: block or unblock internet access for a program straight from its report.
- **Firewall Profiles**: apply a ready-made set of firewall settings, preview the changes first, and undo them later.
- **Quick block buttons**: block all internet or local network connections with one click.

## Updates

Automatic software updates are off in this build, because Portmaster's updates come from Safing's official channel and would replace this build with the official version. Get new versions from the [download page](https://band72.github.io/portmaster-releases/). Filter lists and other intelligence data still update automatically.

Do not use *Check for updates* in the Portmaster settings: it installs the official version. If you installed over an official Portmaster where you had turned automatic updates on yourself, turn them off under Settings › Updates.

## The new features don't show up

If Portmaster looks like the official version after installing, the old version is usually still running. Try these in order:

1. **Restart the computer.** The installer stops the old Portmaster service but doesn't start the new one, and the old window, tray icon or network driver can keep running until you restart. Then open Portmaster from the Start menu.
2. **Check that the installer finished.** If it showed "service could not be stopped" or "service creation failed", the old files were left in place. Restart, then run the installer again.
3. **Don't use *Check for updates* or *Upgrade*** in the Portmaster settings. They install the official version over this build. If you did, download this build again and reinstall it.

To check which build is installed, run this in PowerShell as administrator. `True` means this build is installed; `False` means it isn't, so restart and run the installer again.

```powershell
Select-String -Path "C:\Program Files\Portmaster\portmaster-core.exe" -Pattern "band72" -Quiet
```

On Linux, `grep -c band72 /usr/lib/portmaster/portmaster-core` prints a number above 0 for this build. Restart after installing there too.

## Source code and license

Portmaster is free software under the [GNU General Public License v3.0](LICENSE). Every release includes `portmaster-<version>-source.zip`, the complete source code of exactly that build.
