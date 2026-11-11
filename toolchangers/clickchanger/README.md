# ClickChanger

[Catalog row](../../README.md#clickchanger) · [Gallery](../../GALLERY.md)

<img src="0-clickchanger.jpg" width="420" alt="ClickChanger">

| Field | Value |
| --- | --- |
| Section | Tool changers |
| Project page | [https://github.com/viesturz/ClickChanger](https://github.com/viesturz/ClickChanger) |
| Author | viesturz |
| About | Skeletal toolheads with one shared CPAP part-cooling fan in the shuttle, connected through a servo valve. Two variants: 4 mm pins with bushings, or bearings on square rods. |
| Coupling | pins and bushings |
| Lock | magnets |
| Extruder | on the tool |
| Change time | — |
| Tools | 6 |
| Printer | CoreXY, any gantry |
| Firmware | Klipper, klipper-toolchanger |
| Latest version | Bearings<br>[2026-03](https://github.com/viesturz/ClickChanger/commit/06be510) |
| Stars Likes Views | [![GitHub stars](https://img.shields.io/github/stars/viesturz/ClickChanger?style=flat-square&label=&color=d0d7de&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iI2Y1YjMwMSIgZD0iTTEyIDJsMy4wOSA2LjI2TDIyIDkuMjdsLTUgNC44NyAxLjE4IDYuODhMMTIgMTcuNzdsLTYuMTggMy4yNUw3IDE0LjE0IDIgOS4yN2w2LjkxLTEuMDF6Ii8+PC9zdmc+)](https://github.com/viesturz/ClickChanger)<br>[⏯️⁠21.9K](https://www.youtube.com/watch?v=bxkY-NfGOMM) |
| Links | [CAD](https://github.com/viesturz/ClickChanger/tree/main/PinsVariant)<br>[BOM](https://github.com/viesturz/ClickChanger/blob/main/README-pins.md#bom)<br>[Manual](https://github.com/viesturz/ClickChanger/blob/main/CPAP.md)<br>[Config](https://github.com/viesturz/klipper-toolchanger/tree/main/examples/z%20probe/probe%20on%20T0)<br>[Video](https://www.youtube.com/playlist?list=PLqU7kX5nUJDT31KPcYAykZ2nuPKu_lhjn) |
| Groups | [Discord](https://discord.com/invite/xmDWrYGwVJ) EN 2.2K |

## Pictures (9)

<table>
<tr><td align="center" width="33%"><a href="0-clickchanger.jpg"><img src="0-clickchanger.jpg" width="260" alt="ClickChanger picture 0"></a><br><sub>Photo: <a href="https://github.com/viesturz/ClickChanger">viesturz</a></sub></td><td align="center" width="33%"><a href="1-clickchanger.jpg"><img src="1-clickchanger.jpg" width="260" alt="ClickChanger picture 1"></a><br><sub>Photo: <a href="https://github.com/viesturz/ClickChanger">viesturz</a></sub></td><td align="center" width="33%"><a href="2-clickchanger.jpg"><img src="2-clickchanger.jpg" width="260" alt="ClickChanger picture 2"></a><br><sub>Photo: <a href="https://github.com/viesturz/ClickChanger">viesturz</a></sub></td></tr>
<tr><td align="center" width="33%"><a href="3-clickchanger.jpg"><img src="3-clickchanger.jpg" width="260" alt="ClickChanger picture 3"></a><br><sub>Photo: <a href="https://github.com/viesturz/ClickChanger">viesturz</a></sub></td><td align="center" width="33%"><a href="4-clickchanger.jpg"><img src="4-clickchanger.jpg" width="260" alt="ClickChanger picture 4"></a><br><sub>Photo: <a href="https://github.com/viesturz/ClickChanger">viesturz</a></sub></td><td align="center" width="33%"><a href="5-clickchanger.jpg"><img src="5-clickchanger.jpg" width="260" alt="ClickChanger picture 5"></a><br><sub>Photo: <a href="https://github.com/viesturz/ClickChanger">viesturz</a></sub></td></tr>
<tr><td align="center" width="33%"><a href="6-clickchanger.jpg"><img src="6-clickchanger.jpg" width="260" alt="ClickChanger picture 6"></a><br><sub>Photo: <a href="https://github.com/viesturz/ClickChanger">viesturz</a></sub></td><td align="center" width="33%"><a href="7-clickchanger.jpg"><img src="7-clickchanger.jpg" width="260" alt="ClickChanger picture 7"></a><br><sub>Photo: <a href="https://github.com/viesturz/ClickChanger">viesturz</a></sub></td><td align="center" width="33%"><a href="8-clickchanger.jpg"><img src="8-clickchanger.jpg" width="260" alt="ClickChanger picture 8"></a><br><sub>Version: LiteChanger</sub><br><sub>Photo: <a href="https://github.com/viesturz/LiteChanger">viesturz</a></sub></td></tr>
</table>

## Notes

- Tool 0 probes the bed with a hotend nozzle probe (Revo PZ) or with a Beacon or Cartographer, so the dock motion does not need to be smooth. ([source](https://github.com/viesturz/ClickChanger))
- Printers that the author names: Voron 2.4. ([source](https://github.com/viesturz/ClickChanger))
- Version 2.0 requires a CPAP fan, about 1 m of 15 mm tube, and a 2 g micro servo that drives the air valve. ([source](https://github.com/viesturz/ClickChanger/blob/main/README-pins.md))
- Supported hotends are Revo Voron, Dragon or Dragon High Flow, and Rapido HF (not UHF), and a Revo PZ on T0 can act as the bed probe. ([source](https://github.com/viesturz/ClickChanger/blob/main/README-pins.md))

## Ports and variants

- [LiteChanger](https://github.com/viesturz/LiteChanger), *viesturz (Viesturs Zariņš)*. The author's earlier design, dropped for ClickChanger in 2025-01. Pins near the center of mass and 6x3 mm magnets hold the tool, and the shuttle has no wires. STEP files, no published test.
