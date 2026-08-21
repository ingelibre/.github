# IngeLibre

**Linux distributions have no software ecosystem for civil engineering and
construction.** CAD, 3D/BIM modeling, construction budgeting — the daily
tools of the profession simply don't exist as free software, so engineers
and builders stay dependent on proprietary systems and the platforms that
run them. It shouldn't be that way.

**IngeLibre exists to build that missing ecosystem** — free (GPL) software
for construction professionals, made by a practicing civil engineer.

> **En las distribuciones Linux no existe un ecosistema de software para
> ingeniería y construcción** — por eso los profesionales dependen de
> sistemas privativos. No debería ser así. IngeLibre existe para construir
> ese ecosistema que falta: software libre (GPL) para la construcción,
> hecho por un ingeniero civil en ejercicio.

| Project | What it is | Status |
|---|---|---|
| [**IngeCAD**](https://github.com/ingelibre/ingecad) · [ingecad.org](https://ingecad.org) | 2D CAD in the spirit of classic AutoCAD — faithful DWG/DXF round-trip, AutoCAD muscle-memory commands, paper space with viewports at exact scale, the full dimension family, plotting to scale. Linux/Wayland first | [![latest release](https://img.shields.io/github/v/release/ingelibre/ingecad?label=&color=brightgreen)](https://github.com/ingelibre/ingecad/releases/latest) · AppImage |
| [**IngeTrazo**](https://github.com/ingelibre/ingetrazo) · [ingetrazo.com](https://ingetrazo.com) | 3D modeling / BIM for civil work — SketchUp files open **and save** natively (every era, 2013–2026), BIM tagging with honest IFC quantities, sheet composer with scaled plans to PDF, georeferenced 3D terrain and drone photogrammetry, Python extensions | [![latest release](https://img.shields.io/github/v/release/ingelibre/ingetrazo?label=&color=brightgreen)](https://github.com/ingelibre/ingetrazo/releases/latest) |
| [**IngePresupuestos**](https://github.com/ingelibre/ingepresupuestos) · [ingepresupuestos.com](https://ingepresupuestos.com) | Construction budgeting: unit-cost analysis (ACU), MS-Project-style schedules, site control, 13 report types; imports S10 / PowerCost / Delphin. IngeTrazo's IFC bridge closes the loop **model → takeoff → budget** *(freemium; current line proprietary since 2.9, the earlier GPL line remains public)* | [![latest release](https://img.shields.io/github/v/release/ingelibre/ingepresupuestos?label=&color=brightgreen)](https://github.com/ingelibre/ingepresupuestos/releases/latest) |

## We fix the ecosystem, not just our apps

The DWG format is the wall every free CAD hits. Instead of working around
it, we patch [GNU LibreDWG](https://github.com/LibreDWG/libredwg) upstream:
**43 pull requests and 7 issues so far**
([all of them](https://github.com/LibreDWG/libredwg/pulls?q=is%3Apr+author%3Atuxiasumari)),
19 merged, several more reimplemented by the maintainer from our reports, the
rest under review — each one reduced to a minimal reproducer.

- **Reading.** With that patch stack applied, measured against the proprietary
  ODA File Converter using the same yardstick on both sides over **1,657 real
  drawings: 96.8% parity** — and the files where LibreDWG wins are old r11/r13
  ones that ODA refuses outright.
- **Writing.** A round-trip fuzz harness (generate → write DWG → read back →
  compare entity by entity) found eight distinct root causes; with them fixed,
  the DWG we write went from **6% to 100% valid** on r2000/r2004. One of those
  bugs made AutoCAD reject *any* file containing blocks with attributes.
- **Other people's bugs too**, not only ours: proposed fixes for issues that
  had been waiting since [2023](https://github.com/LibreDWG/libredwg/issues/767)
  and for [four years](https://github.com/LibreDWG/libredwg/issues/523) with
  several reporters on them — plus bug reports with fixes to
  [ezdxf](https://github.com/mozman/ezdxf).

The SketchUp format gets the same treatment. IngeTrazo's native `.skp`
support is built on [OpenSKP](https://github.com/iamahsanmehmood/openskp),
the free clean-room library for the format — and we build OpenSKP itself:
**[20 pull requests so far](https://github.com/iamahsanmehmood/openskp/pulls?q=is%3Apr+author%3Atuxiasumari),
19 merged**, one under review.

- **Reading.** A complete reader for the classic 2013–2020 legacy format,
  then hardened against a 13-year archive of real engineering projects:
  **186 of 186 corpus files parse fully**, each fix validated with
  byte-identical fingerprints.
- **Writing.** Contributions to the `.skp` writer, including dimensions and
  leader texts — record layouts decoded against ground-truth files generated
  with the official SketchUp SDK, so every written file passes the official
  reader.
- **Both directions.** The collaboration flows back too: OpenSKP's author
  contributed the foundation of IngeTrazo's extension system.

Everything goes upstream so the whole free-software world benefits, not just
our apps.

## Support / Apoyo

Development is funded out of pocket (~$150/month keeps the whole suite
moving). If these tools save you a license fee, consider giving back —
every expense is public and receipted.

- 🌍 International: *Open Collective coming soon*
- 🇵🇪 Desde Perú: Yape (ver las webs de cada app)

---

*Author: Marco Sumari Tellez · GPL-3.0-or-later · Arequipa, Perú*
