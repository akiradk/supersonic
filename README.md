<img src="res/appicon-128.png" alt="Supersonic logo" title="Supersonic" align="left" height="60px"/>
<a href='https://flathub.org/apps/details/io.github.dweymouth.supersonic'><img height="50px" align="right" alt='Download on Flathub' src='https://flathub.org/assets/badges/flathub-badge-en.png'/></a>
<a href='https://ko-fi.com/dweymouth'><img height='40' align='right' src='https://az743702.vo.msecnd.net/cdn/kofi3.png?v=0' border='0' alt='Buy Me a Coffee at ko-fi.com'/></a>

# Supersonic

[![License](https://img.shields.io/github/license/dweymouth/supersonic)](https://github.com/dweymouth/supersonic/blob/main/LICENSE)
[![Last Release](https://img.shields.io/github/v/release/dweymouth/supersonic?logo=github&label=latest&style=flat)](https://github.com/dweymouth/supersonic/releases)
[![Downloads](https://img.shields.io/github/downloads/dweymouth/supersonic/total?logo=github&style=flat)](https://github.com/dweymouth/supersonic/releases/latest)
[![Go Report Card](https://goreportcard.com/badge/github.com/dweymouth/supersonic)](https://goreportcard.com/report/github.com/dweymouth/supersonic)
<a href="https://discord.gg/VqmW48aZMh"><img src="https://dcbadge.vercel.app/api/server/VqmW48aZMh" width="20%"/></a>

A lightweight cross-platform desktop client for Subsonic and Jellyfin music servers.

[Jump to installation instructions](https://github.com/dweymouth/supersonic#installation)

## Screenshots

Screenshots of Supersonic running against the Navidrome demo server, showcasing the builtin dark and light themes.

<a href="https://raw.githubusercontent.com/dweymouth/supersonic/main/res/screenshots/NowPlayingView.png"><img src="https://raw.github.com/dweymouth/supersonic/main/res/screenshots/NowPlayingView.png" width="49.5%"/></a>
<a href="https://raw.githubusercontent.com/dweymouth/supersonic/main/res/screenshots/AlbumsView.png"><img src="https://raw.github.com/dweymouth/supersonic/main/res/screenshots/AlbumsView.png" width="49.5%"/></a>
<a href="https://raw.githubusercontent.com/dweymouth/supersonic/main/res/screenshots/FavoriteSongsView.png"><img src="https://raw.github.com/dweymouth/supersonic/main/res/screenshots/FavoriteSongsView.png" width="49.5%"/></a>
<a href="https://raw.githubusercontent.com/dweymouth/supersonic/main/res/screenshots/ArtistView.png"><img src="https://raw.github.com/dweymouth/supersonic/main/res/screenshots/ArtistView.png" width="49.5%"/></a>

## Supported servers

Supersonic supports any music server with a Subsonic (or OpenSubsonic) API, or Jellyfin. A partial list of supported servers is as follows:

* [Navidrome](https://navidrome.org)
* [Jellyfin](https://jellyfin.org)
* [Gonic](https://github.com/sentriz/gonic)
* [LMS](https://github.com/epoupon/lms)
* [Nextcloud Music](https://apps.nextcloud.com/apps/music)
* [Airsonic-Advanced](https://github.com/airsonic-advanced/airsonic-advanced)
* [Ampache](https://ampache.org)
* [Funkwhale](https://www.funkwhale.audio/)
* [Supysonic](https://github.com/spl0k/supysonic)

## Features
* [x] Fast, lightweight, native UI with infinite scrolling
* [x] Light and Dark themes, with optional auto theme switching
* [x] High-quality gapless audio playback powered by MPV, with optional audio exclusive mode
* [x] ReplayGain support (depends on files being tagged on server)
* [x] [Custom themes](https://github.com/dweymouth/supersonic/wiki/Custom-Themes) 
* [x] MPRIS and Mac OS media center integration for media key and desktop control
* [x] Built-in 15-band graphic equalizer
* [x] Scrobble plays to server, with configurable criteria
* [x] Add and switch between multiple servers
* [x] Primary and alternate server hostnames, e.g. for internal and external URLs
* [x] Set filters in albums browsing view
* [x] Play "artist radio" (mix of songs from given artist and similar artists, depends on your server's support)
* [x] Sort tracklist views by column and configure visible tracklist columns
* [x] Download songs, albums or playlists
* [x] Shuffle and repeat playback modes (partial; shuffle album, playlist, artist radio, random songs; repeat one/all)
* [x] Lyrics support
* [x] Internet radio station support (Subsonic)
* [ ] Server jukebox control (planned)
* [ ] Browse by folders (planned)
* [ ] Cast to uPnP/DLNA devices (likely planned)
* [ ] Offline mode (eventually planned)
* [ ] iOS/Android support (maybe eventually planned)

## Installation

On Linux, Supersonic is [available as a Flatpak](https://flathub.org/apps/details/io.github.dweymouth.supersonic)! (Thank you @anarcat!) If you prefer to directly install the release build, or build from source, read below.

If you are running **Windows**, **Mac OS**, or a **Debian**-based Linux distro, download the [latest release](https://github.com/dweymouth/supersonic/releases) for your operating system. You can also download the latest build from the `main` branch via the [Actions](https://github.com/dweymouth/supersonic/actions) tab to get unreleased features and bug fixes (you must be signed in to Github to do this). If you prefer to build from source, or are not running one of these OSes, then see the build instructions for your platform below.

**Apple Silicon (M1/M2) Macs:** You will have to remove the "quarantine bit" that Mac will automatically set, being an application downloaded from the internet. After copying the .app bundle to your Applications folder, in the terminal run `sudo xattr -r -d com.apple.quarantine /Applications/Supersonic.app`

**If you are on Linux** and using the build from the Releases page, you must have libmpv installed on your system, and choose the correct release build (libmpv2 or libmpv1) based on which is available in your distro's package manager. On apt-based systems, run `sudo apt install libmpv1` (or libmpv2) if it is not already installed. The Windows and Mac release builds bundle the mpv dependencies. To install the Linux release build, after ensuring the required libmpv is installed, extract the .tar.xz bundle and run `make user-install` or `sudo make install`.

## Build instructions (Linux)

### Ubuntu dependencies
* ``sudo snap install --classic go``
* Make sure the Go bin directory is in your `$PATH` (`export PATH=~/go/bin:$PATH`)
* ``sudo apt install libmpv-dev gcc libegl1-mesa-dev xorg-dev``

### Fedora dependencies
* ``sudo dnf install golang mpv-devel libX11-devel libXcursor-devel libXrandr-devel libXinerama-devel libXi-devel libglvnd-devel libXxf86vm-devel``

### Build
* clone the repo, CD into the repo root, and run ``go build``
* (note that the first build will take some time as it will download and build the UI library)

### Generate installable .tar.xz bundle
* install the ``fyne`` packaging tool ``go install fyne.io/fyne/v2/cmd/fyne@latest``
* run ``make package_linux``

## Build instructions (Arch Linux)

Supersonic is available in the AUR and can be built either manually with `makepkg` or with an AUR helper like [yay](https://github.com/Jguer/yay). (Please contact package maintainer @dusnm for any issues with the AUR package.)

### Build manually
* Make sure you have the base-devel package group installed on your system
  - ``sudo pacman -S --needed base-devel``
* Clone the AUR repository and navigate into the cloned directory
  - ``git clone https://aur.archlinux.org/supersonic-desktop.git && cd supersonic-desktop``
* Build the package with makepkg
  - ``makepkg -si``

### Build with an AUR helper
* Invoke your favorite AUR helper to automatically build the package
  - ``yay -S supersonic-desktop``

## Build instructions (Mac OS)

### Install dependencies
* install go, and make sure the Go bin directory is in your `$PATH`
  - ``brew install go``
  - ``export PATH="/Users/<yourname>/go/bin:$PATH"``
* install the ``fyne`` packaging tool ``go install fyne.io/fyne/v2/cmd/fyne@latest``
* install Xcode command-line tools (``xcode-select --install``)

#### Homebrew
* install libmpv (``brew install mpv``)
* install dylibbundler (``brew install dylibbundler``) - needed only the bundledeps step, see below

#### Macports
* install mpv with the libmpv variant (``sudo port install mpv +libmpv``)
* install dylibbundler (``sudo port install dylibbundler``) - needed only the bundledeps step, see below

### Build

#### Homebrew setup
* Make sure header and library include paths include the dir in which homebrew installs headers/dylibs (may differ dep. on OS/Homebrew version)
  - ``export C_INCLUDE_PATH=/opt/homebrew/include:$C_INCLUDE_PATH``
  - ``export LIBRARY_PATH=/opt/homebrew/lib:$LIBRARY_PATH``
 
#### Macports setup
* Make sure header and library include paths include the dir in which macports installs headers/dylibs
  - ``export C_INCLUDE_PATH=/opt/local/include:$C_INCLUDE_PATH``
  - ``export LIBRARY_PATH=/opt/local/lib:$LIBRARY_PATH``

#### Building the application
* clone the repo, CD into the repo root, and run ``go build``
* (note that the first build will take some time as it will download and build the UI library)
* run ``make package_macos`` to generate the .app bundle
* **If** you are on Mac OS **High Sierra** through **Catalina**, run ``make bundledeps_macos_highsierra`` and you are done! Otherwise, continue reaading.
* At this point, the Supersonic.app bundle can be copied to Applications and it will run on your machine, but it depends on the brew installation of mpv
* To copy the dependencies into the app bundle, and make it truly portable, run the appopriate command for your package manager:
  - **Homebrew**: ``make bundledeps_macos_homebrew``
  - **Macports**: ``make bundledeps_macos_macports``

## Build instructions (Windows)

### Install dependencies
* install go (https://go.dev/doc/install)
* install MSYS2 and the required packages for the Fyne toolkit (follow instructions for Windows at https://developer.fyne.io/started/)
* install libmpv (in the MSYS2 terminal, ``pacman -S mingw-w64-x86_64-mpv``)

### Build
* in the MSYS2 terminal: clone the repo, CD into the repo root, and run ``go build``
* (note that the first build will take some time as it will download and build the UI library)
* **Note**: The .exe dynamically links to MSYS2 libmpv dependency dlls and must be started from the MSYS2 terminal, or all dependency DLLS must be copied to the same folder as the .exe
* -> If you obtain a statically built mpv-2.dll (containing all its dependencies), and rename it to libmpv-2.dll, you can place just that DLL in the same directory as the EXE, and it should run
* Improvements to Windows build process will be forthcoming
