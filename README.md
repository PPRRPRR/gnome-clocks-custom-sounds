# GNOME Clocks

A simple clock application for GNOME. It includes world clocks, alarms,
a stopwatch and a timer.

<a href='https://flathub.org/apps/details/org.gnome.clocks'><img width='190px' alt='Download on Flathub' src='https://flathub.org/assets/badges/flathub-badge-i-en.png'/></a>

## Custom sounds
Simply place your preferred sound files under `~/.local/share/gnome-clocks/sounds/`
- Timer: `~/.local/share/gnome-clocks/sounds/complete.oga`
- Alarm: `~/.local/share/gnome-clocks/sounds/alarm-clock-elapsed.oga`

If any of the above is absent, gnome-clocks simply falls back to use its embedded GResources.

---
**Tips for the curious:** The following command can be used to list the embedded sound files:
```bash
$ gresource list `which gnome-clocks` | grep sounds
/org/gnome/clocks/sounds/alarm-clock-elapsed.oga
/org/gnome/clocks/sounds/complete.oga
```

## Building tips
- Have a look at `build-aux/`
  - e.g. `build-aux/docker/Dockerfile.ubuntu` allows you to build with a Docker container, with all dependent packages pre-installed
  - Sample command to create a Docker image from this Dockerfile:
    ```bash
	cd build-aux/docker/
    docker build -f Dockerfile.ubuntu -t build-gnome-clocks-custom-sounds .
    ```
  - Sample command to start this container:
    ```bash
	docker run -it build-gnome-clocks-custom-sounds
    ```
- Package dependencies:
  - meson
  - valac
  - cmake
  - libgtkmm-4.0-dev
  - libgweather-4-dev
  - libgnome-desktop-4-dev
  - libgeoclue-2-0
  - libgeoclue-2-dev
  - libadwaita-1-dev
  - itstool
  - desktop-file-utils
  - appstream
  - devscripts
- To manually install these dependencies, do:
```bash
apt update
DEBIAN_FRONTEND=noninteractive apt install -y tzdata
apt install -y meson valac cmake libgtkmm-4.0-dev libgweather-4-dev libgnome-desktop-4-dev libgeoclue-2-0 libgeoclue-2-dev libadwaita-1-dev itstool desktop-file-utils appstream
```
- Optionally:
```bash
apt install -y git
```
- Now you are good to go:
```bash
git clone 'https://github.com/PPRRPRR/gnome-clocks-custom-sounds'
cd gnome-clocks-custom-sounds
meson setup .my_build
cd .my_build
ninja
```
- The built executable can then be found here: `.my_build/src/gnome-clocks`.  Replace your current `/usr/bin/gnome-clocks` with it manually.


## Useful links

- Homepage: <https://apps.gnome.org/Clocks>
- Report issues: <https://gitlab.gnome.org/GNOME/gnome-clocks/issues/>
- Donate: <https://www.gnome.org/donate/>
- Translate: <https://l10n.gnome.org/module/gnome-clocks/>
