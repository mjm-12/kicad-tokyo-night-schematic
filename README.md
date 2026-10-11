# Tokyo Night (Schematic)

A dark KiCad color theme for the schematic editor, built on the [Tokyo Night](https://github.com/enkia/tokyo-night-vscode-theme) palette (night variant, background `#1a1b26`).

**Scope:** the theme covers the schematic editor only. The PCB editor, 3D viewer and GerbView sections keep near-default KiCad colors. Each editor in KiCad picks its theme on its own, so you can pair this with any PCB theme.

## Screenshots

Tokyo Night (Schematic):

![Tokyo Night (Schematic)](screenshots/tokyo-night.png)

KiCad default, same sheet and framing:

![KiCad default](screenshots/kicad-default.png)

The sheet is the top board of [Anthracite](https://github.com/trope-oshw/anthracite), exported with `kicad-cli sch export svg --theme`. The orange, teal and pink wires in both images come from net class colors in that project, and KiCad draws them over the theme's wire color. See [Net class colors](#net-class-colors) for the values.

## Net class colors

![Net class colors on the Anthracite bottom board](screenshots/netclass-example.png)

The Anthracite bottom board (MCU section above, Tokyo Night theme) assigns these wire colors through net classes:

| Net class | Nets | Wire color |
| --- | --- | --- |
| `Default` | Everything not assigned elsewhere | none, `rgba(0, 0, 0, 0.000)`; wires use the theme color |
| `power` | Supply rails (patterns `+*`, `-*`) and supply-side nodes | `#f7768e`, `rgb(247, 118, 142)` |
| `GND` | `GNDPWR` (pattern) | `#848484`, `rgb(132, 132, 132)` |
| `GPIO_Input` | MCU input pins: switch positions, `PA*`/`PB*`/`PF*` inputs | `#73daca`, `rgb(115, 218, 202)` |
| `GPIO_Output` | MCU outputs: mode and control lines to the level shifters, LED drives | `#ff9e64`, `rgb(255, 158, 100)` |
| `USART` | UART TX/RX between the MCU, debug connector and expansion header | `#bb9af7`, `rgb(187, 154, 247)` |
| `TIM` | Timer output from `PA7` through a buffer to the expansion header | `#e0af68`, `rgb(224, 175, 104)` |

The five colored classes use colors from the Tokyo Night palette: red, orange, teal, purple and yellow. The `GND` gray does not appear in the palette. The top board uses the same colors under the names `Input` (teal) and `Control` (orange).

The project file (`.kicad_pro`) stores these colors, and the theme file does not, so installing this theme leaves your wires unchanged. To reuse the palette, open **File > Schematic Setup > Project > Net Classes**, set the **Color** column for each class, and assign nets with the pattern table on the same page or with net class directive labels.

## Install

### Plugin and Content Manager

1. Download `kicad-tokyo-night-schematic-1.0.0.zip` from the [latest release](https://github.com/Mjm-12/kicad-tokyo-night-schematic/releases/latest).
2. In KiCad, open the Plugin and Content Manager and click **Install from File...**.
3. Select the zip.

### Manual

Copy `colors/tokyo-night-schematic.json` into the KiCad colors folder for your OS:

| OS | Folder |
| --- | --- |
| Windows | `%APPDATA%\kicad\10.0\colors\` |
| macOS | `~/Library/Preferences/kicad/10.0/colors/` |
| Linux | `~/.config/kicad/10.0/colors/` |

If KiCad is running, restart it.

### Select the theme

Open **Preferences > Schematic Editor > Colors** and choose **Tokyo Night (Schematic)**.

## Compatibility

Tested on KiCad 10.0.1. The theme file uses the KiCad 10 color settings format (`meta.version` 5).

## Credits

Colors come from the Tokyo Night theme by enkia: <https://github.com/enkia/tokyo-night-vscode-theme> (MIT).

## License

MIT. See [LICENSE](LICENSE).
