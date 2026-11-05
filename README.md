# APT Easily

Small command-line helpers for searching APT package metadata and installing packages from a reusable list. The scripts are intended for Debian, Ubuntu, and other Debian-based distributions that provide APT.

## What’s included

- **`apt-searchengine`** — an interactive front end to `apt-cache search`. Enter a package name or search phrase to see matching packages from your locally available APT metadata.
- **`apt-autoinstall`** — installs packages listed in a text file, one package name per line. Blank lines and comments (lines beginning with `#`, or trailing text after `#`) are ignored. It uses a graphical file picker with Zenity when available in a graphical session, otherwise it asks for a file path in the terminal.

## Requirements

- A Debian-based system with `apt-cache` and/or `apt-get` installed.
- Bash for `apt-autoinstall` and a POSIX-compatible shell for `apt-searchengine`.
- `sudo` access to install packages with `apt-autoinstall`.
- Optional: Zenity for a graphical file picker.

## Usage

Clone or download this repository, then run either script from a terminal:

```sh
chmod +x apt-searchengine apt-autoinstall
./apt-searchengine
./apt-autoinstall
```

### Search for packages

Choose **1. Search** and enter a package name or search term. Results come from the APT package lists already present on your system. If results are missing or outdated, refresh those lists using your usual package-management workflow (for example, `sudo apt update`) and search again.

### Install packages from a file

Create a plain text file with one package name on each line, for example:

```text
# My usual utilities
curl
git
htop # optional comment
```

Run `./apt-autoinstall` and select that file (or enter its path when prompted). The script validates package-name syntax, displays the packages it found, and then runs `sudo apt-get install` for them. APT may ask you to confirm the installation and will handle dependency resolution.

Only use package lists you trust: installing packages changes your system and may require administrator privileges. Review the displayed package list and APT’s confirmation prompt before proceeding.

## What to expect

These are lightweight shell scripts, not a package manager or a graphical application. They do not automatically refresh APT package lists. Search results depend on your configured repositories and the metadata currently on your system. Installation requires a working internet/repository setup as needed by APT.

## License

This project is licensed under the **MIT License**. See [`LICENSE`](LICENSE) for the full text. Copyright (c) 2026 BLACKREAPER38.
