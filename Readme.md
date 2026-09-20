# Macropad Collection

Open-hardware build documentation — KiCad projects, gerbers, bills of materials, laser-cut cases and artwork — for two custom macropads.

## The macropads

### [DisArray Desnarler](./disarray_desnarler/) &nbsp;→&nbsp; `disarray_desnarler/`

The original Schreibtischordnungsdienst macropad: a XIAO-RP2040 pad with hot-swap switches, an analog fader, and an optional rotary encoder, flashed with QMK. Includes the full build guide, laser-cut case, 3D-printed fader knob, sticker artwork, and the flashing/configuration instructions.

[![DisArray Desnarler](./disarray_desnarler/images/desnarler.jpg)](./disarray_desnarler/)

For a project overview, see [the Hackaday project page](https://hackaday.io/project/204536-disarray-desnarler).

### [macro_GOAT](./macro_GOAT/) &nbsp;→&nbsp; `macro_GOAT/`

An RP2040-Zero macropad with a 16-LED WS2812B array, hot-swap switches, and an optional EC11 rotary encoder. Includes the KiCad project, gerbers, SMD stencil, and the board artwork.

## Repository layout

```
disarray_desnarler/      first macropad (build docs, PCB versions, case, instructions)
macro_GOAT/              second macropad (PCB, gerbers, stencil, artwork)
symbols_and_footprints/  shared KiCad symbol & footprint libraries used by both boards
```

> **KiCad note:** each project's `fp-lib-table` / `sym-lib-table` still contains machine-specific
> paths from the original authoring environment. The shared libraries now live at the repo root in
> [`symbols_and_footprints/`](./symbols_and_footprints/); re-point the library tables there when
> opening a project in KiCad.

## License

See [LICENSE](./LICENSE).

&mdash; _your Schreibtischordnungsdienst_
