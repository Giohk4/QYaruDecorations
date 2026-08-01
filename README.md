# QYaruDecorations

A Qt decoration plugin implementing Yaru-like client-side decorations.

## How to compile
This Plugin uses private Qt headers and is therefore tied to specific Qt
versions. It may break after Qt updates and will (likely) require rebuilding
against the installed Qt version.

While it's *possible* to build using Qt 5, that requires
additional backported patches from Qt 6 (You can get these [here](https://src.fedoraproject.org/rpms/qt5-qtwayland/blob/rawhide/f/qtwayland-decoration-support-backports-from-qt6.patch) )
Qt5 may have issues and incomplete support.

Build instructions:

```
mkdir build
cd build
cmake [OPTIONS] [-DUSE_QT6=true] ..
cmake --build . && sudo cmake --install .
```

## Usage

It can be used by setting the QT_WAYLAND_DECORATION environment variable:

```
export QT_WAYLAND_DECORATION=yaru
```

### NOTE:

if you want this to persist and apply to all system Qt applications, use /etc/environment.d
if that directory doesn't already exist create it with

```
sudo mkdir -p /etc/environment.d
```

then create a generic numbered file there containing the environment variable

```
echo "QT_WAYLAND_DECORATION=yaru" | sudo tee /etc/environment.d/10-qt-yaru-decorations
```

after that you WILL need to log out and log back in for it to apply

## License

The code is under [LGPL 2.1](https://www.gnu.org/licenses/old-licenses/lgpl-2.1.en.html) with the "or any later version" clause.
