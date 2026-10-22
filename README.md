# Dotfiles

My personal configuration for an Arch Linux laptop running the Hyprland window manager. Everything here is versioned with Git and linked into place with symbolic links, so the whole environment can be rebuilt from this repository.

## What's inside

| Directory | Purpose |
|---|---|
| `hypr` | Hyprland window manager, plus `hypridle` (idle actions) and `hyprlock` (lock screen) |
| `waybar` | Status bar, one per monitor |
| `wofi` | Application launcher |
| `kitty` | Terminal emulator |
| `mpv` | Video player, tuned for hardware decoding of H.264 with VA-API |
| `btop` | Resource monitor |
| `zsh` | Zsh configuration and aliases, on top of Oh My Zsh |
| `git` | Git configuration |

My Neovim configuration lives in its own repository: [eddybolivia/nvim-config](https://github.com/eddybolivia/nvim-config).

## Requirements

- Arch Linux with Hyprland, Waybar, Wofi and kitty
- Zsh with Oh My Zsh and Starship
- Command-line tools: `eza`, `bat`, `fzf`, `zoxide`, `ripgrep` and `fd`
- `mpv` and `yt-dlp` for video

## Installation

```bash
git clone git@github.com:eddybolivia/dotfiles.git ~/dev/config/dotfiles
cd ~/dev/config/dotfiles
./install.sh
```

The `install.sh` script creates the symbolic links from `~/.config` and `~/.zshrc` to this repository. Any existing configuration it replaces is first saved in `~/.dotfiles_backup`.

## Hardware notes

This setup runs on an HP Pavilion with an AMD A10 APU, which uses the `r600` graphics driver. Two decisions come from that hardware:

- **Video:** the integrated GPU can decode H.264 but not VP9 or AV1, so `mpv` requests H.264 streams up to 720p. This keeps the CPU around 62 °C instead of 81 °C while playing video.
- **Terminal:** GPU-accelerated terminals that need shader storage blocks, such as Ghostty, do not run on this driver. Kitty works well.

## Credits

This repository started as a copy of [Luis Mendoza's dotfiles](https://github.com/luismendozamx/dotfiles), and its structure and install script come from his work. It has since been adapted to my own hardware, tools and workflow.
