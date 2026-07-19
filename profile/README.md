# IngeLibre

**Libre engineering software, built by a practicing civil engineer in Peru.**
Software libre de ingeniería, hecho por un ingeniero civil en ejercicio.

No engineer should need proprietary licenses to do professional work.

| Project | What it is | Status |
|---|---|---|
| [**IngeCAD**](https://github.com/ingelibre/ingecad) | 2D CAD in the spirit of classic AutoCAD — faithful DWG/DXF round-trip, AutoCAD muscle-memory commands, Linux/Wayland first | [v0.1.0](https://github.com/ingelibre/ingecad/releases) |
| [**IngeTrazo**](https://github.com/ingelibre/ingetrazo) | 3D modeling / BIM for civil work, SketchUp import | usable beta |
| [**IngePresupuestos**](https://github.com/ingelibre/ingepresupuestos) | Construction budgeting (the S10 workflow, free) | mature |

## We fix the ecosystem, not just our apps

The DWG format is the wall every free CAD hits. Instead of working around
it, we patch [GNU LibreDWG](https://github.com/LibreDWG/libredwg) upstream:
**12 pull requests** ([#1311–#1322](https://github.com/LibreDWG/libredwg/pulls?q=is%3Apr+author%3Atuxiasumari))
that took real-world DWG conversion from 83% to **99%** on a 1,385-file
corpus — plus bug reports with fixes to [ezdxf](https://github.com/mozman/ezdxf).
Everything lands upstream so the whole free-software world benefits.

## Support / Apoyo

Development is funded out of pocket (~$150/month keeps the whole suite
moving). If these tools save you a license fee, consider giving back —
every expense is public and receipted.

- 🌍 International: *Open Collective coming soon*
- 🇵🇪 Desde Perú: Yape (ver las webs de cada app)

---

*Author: Marco Sumari Tellez · GPL-3.0-or-later · Arequipa, Perú*
