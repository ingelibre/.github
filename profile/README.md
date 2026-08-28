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

<table>
<tr>
<td width="33%" align="center">
<a href="https://ingecad.org"><img src="https://raw.githubusercontent.com/ingelibre/.github/main/profile/images/ingecad.jpg" alt="IngeCAD: a roof truss drawn to scale with dimensions, layers and the command line"></a><br>
<b>IngeCAD</b> — 2D drafting, DWG in and out
</td>
<td width="33%" align="center">
<a href="https://ingetrazo.com"><img src="https://raw.githubusercontent.com/ingelibre/.github/main/profile/images/ingetrazo.jpg" alt="IngeTrazo: a bullring modelled in 3D with terracing, arches and terrain"></a><br>
<b>IngeTrazo</b> — 3D modelling and BIM, SketchUp in and out
</td>
<td width="33%" align="center">
<a href="https://ingepresupuestos.com"><img src="https://raw.githubusercontent.com/ingelibre/.github/main/profile/images/ingepresupuestos.jpg" alt="IngePresupuestos: a construction budget with unit-cost analysis"></a><br>
<b>IngePresupuestos</b> — budgets and site control
</td>
</tr>
</table>

*Real projects, not demos: a truss detail, a bullring with its terracing, and
the budget for a town plaza — all drawn or costed with these tools in actual
work.*

| Project | What it is | Status |
|---|---|---|
| [**IngeCAD**](https://github.com/ingelibre/ingecad) · [ingecad.org](https://ingecad.org) | 2D CAD in the spirit of classic AutoCAD — faithful DWG/DXF round-trip, AutoCAD muscle-memory commands, paper space with viewports at exact scale, the full dimension family, plotting to scale. Linux/Wayland first | [![latest release](https://img.shields.io/github/v/release/ingelibre/ingecad?label=&color=brightgreen)](https://github.com/ingelibre/ingecad/releases/latest) |
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

## Help wanted / Se busca ayuda

**One person writes all three.** A practicing civil engineer, in the hours
left over from actual site work. The tools have grown past what that can
keep up with — and the bottleneck is not ideas, it is hands.

**You do not need to know the codebase to help.** These are real open
issues, ordered by how little context they need:

| If you can… | Start here |
|---|---|
| **Spare five seconds** | ⭐ Star the repos. It is how the next engineer finds out these exist at all |
| **Run Linux on hardware we don't have** | [ingetrazo#6](https://github.com/ingelibre/ingetrazo/issues/6) — the packaged builds failed on an NVIDIA + X11 machine. A stranger reporting that is why it got fixed. Our CI runs software Mesa; it was never going to catch it |
| **Speak a language that isn't Spanish or English** | [ingecad#8](https://github.com/ingelibre/ingecad/issues/8) — *a language is one folder*. No code |
| **Use AutoCAD in Spanish** | [ingecad#5](https://github.com/ingelibre/ingecad/issues/5) — check our command names against the real thing. No code, and only someone who uses it daily can do it |
| **Draw an icon** | [ingecad#6](https://github.com/ingelibre/ingecad/issues/6) — four layer tools are missing theirs |
| **Write Python** | PySide6 + OpenGL. [ingecad#7](https://github.com/ingelibre/ingecad/issues/7) (an object snap that is listed but not implemented) and [ingecad#9](https://github.com/ingelibre/ingecad/issues/9) are self-contained places to land |
| **Open a file that breaks** | Send it. A `.dwg` or `.skp` that imports wrong is worth more than a bug report — most of the upstream fixes below started as one file that would not open |

> **Una sola persona escribe los tres.** Un ingeniero civil en ejercicio, en
> las horas que deja la obra. Las herramientas han crecido más de lo que eso
> puede sostener, y lo que falta no son ideas: son manos. **No hace falta
> conocer el código**: una estrella, probarlo en un equipo distinto al
> nuestro, traducirlo, revisar los nombres de los comandos en español, o
> mandarnos el archivo que no abre — todo eso ayuda, y la tabla de arriba
> son issues abiertos de verdad.

## Support / Apoyo

Any support is welcome — it is what lets this free alternative keep
growing. Code, a translation, a bug report or a file that will not open
all count; and if you would rather help financially, that is welcome too.

> Cualquier apoyo es bienvenido — es lo que permite que esta alternativa
> libre siga creciendo. Código, una traducción, un informe de fallo o un
> archivo que no abre cuentan igual; y si prefieres apoyar
> económicamente, también es bienvenido.

- 🇵🇪 Desde Perú: Yape (ver las webs de cada app)

---

*Author: Marco Sumari Tellez · GPL-3.0-or-later · Arequipa, Perú*
