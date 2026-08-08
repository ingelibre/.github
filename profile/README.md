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
| [**IngeCAD**](https://github.com/ingelibre/ingecad) | 2D CAD in the spirit of classic AutoCAD — faithful DWG/DXF round-trip, AutoCAD muscle-memory commands, Linux/Wayland first | [v0.1.0](https://github.com/ingelibre/ingecad/releases) |
| [**IngeTrazo**](https://github.com/ingelibre/ingetrazo) | 3D modeling / BIM for civil work, SketchUp import | usable beta |

## Related / Relacionado

[**IngePresupuestos**](https://ingepresupuestos.com) — construction budgeting
(the S10 workflow) by the same author. Since v2.9.0 it is an independent,
proprietary product with a free tier; its earlier releases (≤2.8.8) were
published under GPL-3.0 and remain so. Its revenue helps fund the free
projects above. / *Presupuestos de obra del mismo autor; desde la 2.9.0 es un
producto independiente (propietario, con versión gratuita) cuyos ingresos
ayudan a sostener los proyectos libres de esta organización.*

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
