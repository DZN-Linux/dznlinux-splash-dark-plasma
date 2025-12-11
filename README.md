# DZNLinux Dark Splash Screen for Plasma 6

Custom splash screen theme for DZN Linux running KDE Plasma 6, featuring a dark, modern aesthetic.

## Overview

A sleek dark-themed boot splash screen that displays during KDE Plasma startup, providing visual feedback while the desktop environment loads.

**Version:** 1.0.0

## Features

- Dark theme that matches DZN Linux branding
- Smooth integration with KDE Plasma 6
- Custom DZN Linux logo and colors
- Optimized for fast loading times

## Compatibility

- **Desktop Environment**: KDE Plasma 6
- **Platform**: Arch Linux and derivatives
- **Display Managers**: SDDM, LightDM, GDM (any)

## Installation

### From DZN Linux Repository (Recommended)

First, add the DZN Linux repository to your system:

```bash
# Add the PGP key
sudo pacman-key --recv-key BB31837564255477
sudo pacman-key --lsign-key BB31837564255477
```

Add the following to `/etc/pacman.conf`:

```ini
[dznlinux_repo]
SigLevel = Required DatabaseOptional
Server = https://repo.dozzen.me/archlinux/$repo/$arch

[dznlinux_repo_3party]
SigLevel = Required DatabaseOptional
Server = https://repo.dozzen.me/archlinux/$repo/$arch
```

Then install the package:

```bash
sudo pacman -Sy
sudo pacman -S dznlinux-splash-dark-plasma-git
```

### Manual Installation

```bash
# Clone repository
git clone https://github.com/DZN-Linux/dznlinux-splash-dark-plasma.git
cd dznlinux-splash-dark-plasma

# Copy splash screen files to system directories
sudo cp -r usr/share/plasma/look-and-feel/dznlinux-Splash-Dark /usr/share/plasma/look-and-feel/
```

### From PKGBUILD

```bash
# Clone the PKGBUILD repository
git clone https://github.com/DZN-Linux/PKGBUILD.git
cd PKGBUILD/dznlinux-splash-dark-plasma

# Build and install
makepkg -si
```

## Configuration

After installation, activate the splash screen in KDE Plasma settings:

### Method 1: System Settings GUI

1. Open **System Settings**
2. Navigate to **Appearance** → **Splash Screen**
3. Select **DZNLinux Dark** from the list
4. Click **Apply**

### Method 2: Command Line

```bash
# Set the splash screen
kwriteconfig5 --file ~/.config/ksplashrc --group KSplash --key Theme dznlinux-Splash-Dark
```

## File Structure

```
usr/share/plasma/look-and-feel/dznlinux-Splash-Dark/
├── contents/
│   ├── splash/
│   │   └── Splash.qml       # Main splash screen QML
│   └── previews/
│       └── splash.png        # Preview image
└── metadata.desktop          # Theme metadata
```

## What Gets Installed

- Splash screen files: `/usr/share/plasma/look-and-feel/dznlinux-Splash-Dark/`
- Documentation: `/usr/share/doc/dznlinux-splash-dark-plasma/`
- License: `/usr/share/licenses/dznlinux-splash-dark-plasma/`

## Uninstalling

```bash
sudo pacman -R dznlinux-splash-dark-plasma-git
```

## Development

To test changes without installing system-wide:

```bash
# Copy to local KDE directory
mkdir -p ~/.local/share/plasma/look-and-feel/
cp -r usr/share/plasma/look-and-feel/dznlinux-Splash-Dark ~/.local/share/plasma/look-and-feel/

# Log out and back in to see changes
```

## Troubleshooting

### Splash screen doesn't appear

1. Verify installation:
   ```bash
   ls /usr/share/plasma/look-and-feel/dznlinux-Splash-Dark/
   ```

2. Check current splash screen:
   ```bash
   kreadconfig5 --file ~/.config/ksplashrc --group KSplash --key Theme
   ```

3. Try manually setting it:
   ```bash
   kwriteconfig5 --file ~/.config/ksplashrc --group KSplash --key Theme dznlinux-Splash-Dark
   ```

### Splash screen shows errors

Check Plasma logs:
```bash
journalctl --user -b | grep -i splash
```

## Source Repository

The source files are maintained at:
https://github.com/DZN-Linux/dznlinux-splash-dark-plasma

## License

GPL-3.0-or-later - See LICENSE file

## Credits

- DZN Linux Project
- Seth Dawson <dznlinux@gmail.com>

## Links

- GitHub: https://github.com/DZN-Linux/dznlinux-splash-dark-plasma
- DZN Linux: https://github.com/DZN-Linux
- KDE Plasma: https://kde.org/plasma-desktop/
