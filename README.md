# theme-sync

Pull the colors from your KDE wallpaper into the apps that ignore them —
alacritty, opencode, obsidian, btop, fastfetch, vicinae, qbittorrent & VSCodium.

Run it after every wallpaper change.

## One-shot

    curl -fsSL https://raw.githubusercontent.com/actuallyaryaman/kde-material-you-theme-sync/main/scripts/theme-sync | python3 -

Or install it once:

    curl -fsSL https://raw.githubusercontent.com/actuallyaryaman/kde-material-you-theme-sync/main/scripts/theme-sync -o ~/.local/bin/theme-sync
    chmod +x ~/.local/bin/theme-sync

## Requirements

[**kde-material-you-colors**](https://github.com/luisbocanegra/kde-material-you-colors)
must be installed and its daemon running — it's what derives
`MaterialYouDark.colors` / `MaterialYouLight.colors` from your wallpaper.
Without it `theme-sync` refuses to run.

Install: read the repo's [install page](https://software.opensuse.org//download.html?project=home%3Aluisbocanegra&package=kde-material-you-colors),
then add the **KDE Material You Colors** Plasma 6 widget from the KDE Store.

## Where things go

| App            | Target                                                        |
|----------------|---------------------------------------------------------------|
| alacritty      | `~/.config/alacritty/material-you.toml`                       |
| opencode       | `~/.config/opencode/themes/material-you.json`                 |
| obsidian       | `~/.obsidian/…/themes/MaterialYou/theme.css`                  |
| btop           | `~/.config/btop/themes/material-you.theme`                    |
| fastfetch      | `~/.config/fastfetch/config.jsonc`                            |
| vicinae        | `~/.local/share/vicinae/themes/material-you.toml`             |
| qbittorrent    | `~/.config/qBittorrent/themes/material-you/config.json`       |
| VSCodium       | `~/.vscode-oss/extensions/theme-sync.material-you-theme-…`    |

The titlebar frame = WM active background darkened to `scale` (default `0.59`).
If the frame looks off, override it in `config/knobs.conf`.

## Palette

Swatches generated from the active wallpaper by `kde-material-you-colors`:

| Surface | Accent | Semantic |
|---|---|---|
| <span style="display:inline-block;width:1em;height:1em;background:#070c0c">　</span> bg `#070c0c` | <span style="display:inline-block;width:1em;height:1em;background:#98cdcc">　</span> accent `#98cdcc` | <span style="display:inline-block;width:1em;height:1em;background:#FF7352">　</span> red `#FF7352` |
| <span style="display:inline-block;width:1em;height:1em;background:#131b1b">　</span> surface0 `#131b1b` | <span style="display:inline-block;width:1em;height:1em;background:#b0cccb">　</span> accent_hover `#b0cccb` | <span style="display:inline-block;width:1em;height:1em;background:#31C193">　</span> green `#31C193` |
| <span style="display:inline-block;width:1em;height:1em;background:#1d2827">　</span> surface1 `#1d2827` | <span style="display:inline-block;width:1em;height:1em;background:#0c4848">　</span> accent_fg `#0c4848` | <span style="display:inline-block;width:1em;height:1em;background:#FA9A24">　</span> yellow `#FA9A24` |
| <span style="display:inline-block;width:1em;height:1em;background:#336767">　</span> hover `#336767` | <span style="display:inline-block;width:1em;height:1em;background:#3bb4b2">　</span> cyan `#3bb4b2` | <span style="display:inline-block;width:1em;height:1em;background:#45A8D2">　</span> blue `#45A8D2` |
| <span style="display:inline-block;width:1em;height:1em;background:#111817">　</span> frame `#111817` | | <span style="display:inline-block;width:1em;height:1em;background:#B489F3">　</span> magenta `#B489F3` |