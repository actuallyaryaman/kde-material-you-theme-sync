# theme-sync

Regenerate Material You themes from the active KDE color scheme for apps that
ignore KDE dynamic colors. Rerun after changing your wallpaper.

## Dependencies

**Hard dependency:** [luisbocanegra/kde-material-you-colors](https://github.com/luisbocanegra/kde-material-you-colors) — the KDE Plasma widget + daemon that derives `MaterialYouDark.colors` / `MaterialYouLight.colors` from your wallpaper. Without it the source schemes never get regenerated, so `theme-sync` refuses to run (`check_deps` guard). The script also requires the widget's daemon to be running.

Install: OBS/Fedora package (see [install page](https://software.opensuse.org//download.html?project=home%3Aluisbocanegra&package=kde-material-you-colors)) or `pipx install kde-material-you-colors`; then add the **KDE Material You Colors** Plasma 6 widget from the KDE Store to your panel/desktop.

## Usage

    theme-sync               regenerate all themes (uses active scheme)
    theme-sync --check       verify generated themes match current scheme
    theme-sync <scheme.colors>

The script writes generated themes into their live locations:

| App            | Output                                                        |
|----------------|---------------------------------------------------------------|
| alacritty      | `~/.config/alacritty/material-you.toml`                       |
| opencode       | `~/.config/opencode/themes/material-you.json`                 |
| obsidian       | `~/.config/.../.obsidian/themes/MaterialYou/theme.css`        |
| btop           | `~/.config/btop/themes/material-you.theme`                    |
| fastfetch      | `~/.config/fastfetch/config.jsonc`                            |
| vicinae        | `~/.local/share/vicinae/themes/material-you.toml`             |
| qbittorrent    | `~/.config/qBittorrent/themes/material-you/config.json`       |
| vscodium       | `~/.vscode-oss/extensions/theme-sync.material-you-theme-1.0.0`|

## One-shot

Run `theme-sync` directly from the repo, nothing to install:

    curl -fsSL https://raw.githubusercontent.com/actuallyaryaman/kde-material-you-theme-sync/main/scripts/theme-sync | python3 -

…or save it as a command:

    curl -fsSL https://raw.githubusercontent.com/actuallyaryaman/kde-material-you-theme-sync/main/scripts/theme-sync -o ~/.local/bin/theme-sync
    chmod +x ~/.local/bin/theme-sync

Example output (colors render as blocks in a truecolor terminal):

    frame (titlebar): #111817
    palette: ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██
    synced from MaterialYouDark:
      alacritty → /home/logic/.config/alacritty/material-you.toml
      opencode  → /home/logic/.config/opencode/themes/material-you.json
      obsidian  → /home/logic/windows/Users/logic/Desktop/Obsidian/.obsidian/themes/MaterialYou/theme.css
      btop      → /home/logic/.config/btop/themes/material-you.theme
      fastfetch → /home/logic/.config/fastfetch/config.jsonc
      vicinae   → /home/logic/.local/share/vicinae/themes/material-you.toml
      qbittorrent → /home/logic/.config/qBittorrent/themes/material-you/config.json
      vscodium    → /home/logic/.vscode-oss/extensions/theme-sync.material-you-theme-1.0.0/themes/material-you-color-theme.json
    check ok: all 8 themes match MaterialYouDark (#98cdcc); shared bg #111817
    restarted vicinae daemon

## Layout

    scripts/       theme-sync script
    config/        titlebar calibration knobs (scale / override)
    schemes/       source KDE MaterialYou color schemes (dark + light)
    apps/          generated themes, one directory per app

## Calibration

The titlebar frame color is derived from the WM active background darkened to
`scale` (default 0.59). See `config/knobs.conf`. A real clock drifts — if the
frame looks off, run theme-sync after a wallpaper change or override it there.