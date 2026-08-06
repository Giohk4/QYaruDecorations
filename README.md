# QYaruDecorations

A Qt decoration plugin implementing Yaru-like client-side decorations.

![Screenshot](screenshots.png)
<details>
<summary>Screenshot details</summary>

- **Theme used:** KvYaru-blue-Dark
- **Wallpaper:** [Ubuntu 21.10 Wallpaper compettion Winner](https://ubuntu.com/blog/winners-of-the-21-10-wallpaper-competition)
- **Icon theme:** Yaru-blue-dark
- **Font:** Noto Sans Medium (11pt)

</details>

## Table of Contents

- [How to Install](#how-to-install)
- [Usage](#usage)
- [How to Compile](#how-to-compile)
- [License and Copyright](#license-and-copyright)

## How to Install

Currently there are no prebuilt packages — you'll need to compile from source. See [How to Compile](#how-to-compile)

## Usage

It can be used by setting the QT_WAYLAND_DECORATION environment variable:

```bash
export QT_WAYLAND_DECORATION=yaru
```

### Persisting the setting

Per-user (recommended):

```bash
mkdir -p ~/.config/environment.d
echo "QT_WAYLAND_DECORATION=yaru" > ~/.config/environment.d/10-qt-yaru-decorations.conf
```

System-wide (Not recommended, all users, needs root):

```bash
sudo mkdir -p /etc/environment.d
echo "QT_WAYLAND_DECORATION=yaru" | sudo tee /etc/environment.d/10-qt-yaru-decorations.conf
```

Either way, logout and log back in for it to take effect.

To undo, delete the file you created and log out/in again.

## How to Compile

This Plugin uses private Qt headers and is therefore tied to specific Qt
versions. It may break after Qt updates and will (likely) require rebuilding
against the installed Qt version.

While it's _possible_ to build using Qt 5, that requires
additional backported patches from Qt 6 (You can get these [here](https://src.fedoraproject.org/rpms/qt5-qtwayland/blob/rawhide/f/qtwayland-decoration-support-backports-from-qt6.patch) )
Without said patch Qt5 may have issues and incomplete support.

Build Requirements:

- Ubuntu 26.04/24.04

```bash
sudo apt install cmake make pkg-config xcb libx11-dev libx11-xcb-dev libxkbcommon-dev libwayland-bin libwayland-dev wayland-protocols qt6-positioning-private-dev qt6-positioning-dev qt6-base-private-dev qt6-wayland-private-dev qt6-wayland-dev qt6-base-dev qt6-svg-dev qt6-tools-dev
```

- OpenSUSE Tumbleweed/Slowroll

```bash
sudo zypper install cmake make pkg-config gcc libxkbcommon-devel qt6-base-common-devel qt6-base-devel qt6-wayland-devel qt6-waylandclient-devel qt6-waylandclient-private-devel qt6-svg-devel qt6-base-private-devel
```

Build instructions:

```bash
mkdir build
cd build
cmake [OPTIONS] [-DUSE_QT6=true] ..
cmake --build . && sudo cmake --install .
```

## License and Copyright

This project is a modified fork of the Original [FedoraQt/QAdwaitaDecorations](https://github.com/FedoraQt/QAdwaitaDecorations) Project that includes miscalinous fixes and changes to fit with the Yaru style.

The code is under [LGPL 2.1](https://www.gnu.org/licenses/old-licenses/lgpl-2.1.en.html) with the "or any later version" clause.
