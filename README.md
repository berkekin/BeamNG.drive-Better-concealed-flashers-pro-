# Better Concealed Flashers PRO 3

**Concealed police lights for any vehicle in BeamNG.drive, placed automatically where the vehicle's own author would put them.**

[Türkçe](README.tr.md) · BeamNG.drive 0.40+ · English and Turkish UI

![Placement tab](docs/img/ui_en_placement.png)

Hiding LED heads behind a windshield, inside a grille or along a bumper usually means nudging offsets for an hour
per car. This mod does the fitting for you. Open the app, click a zone on the vehicle map, and the flashers sit
where they belong: tucked under the top edge of the glass, flush with the grille, inside the lamp housings, next to
the plate. It works on vanilla vehicles and on mod vehicles, including cars exported from Automation.

## Highlights

- **One click per zone.** 16 zones plus a free position: windshield, dash, grille, front and rear bumper, hood,
  headlights and tail lights (hideaway), mirrors, front fenders, side skirts, rear side windows, rear window,
  rear deck, trunk and roof.
- **Factory positions first.** If the vehicle, or a part made for it, already has concealed flashers, the mod reuses
  their exact positions and spacing. You get the same layout the vehicle's author chose.
- **Real surfaces everywhere else.** The vehicle's 3D model is scanned and every head is seated on the actual
  surface: glass, grille, bumper or lamp.
- **Mounted like a factory part.** Heads are attached to the body parts they sit on and go dark when the glass in
  front of them breaks. They don't wobble and they don't add extra physics nodes.
- **Kits to start fast:** Undercover, Full package, Front only, Rear only, Interior lightbar (slicktop), Hideaway and
  Traffic advisor, with 10 color schemes. You can also have a kit applied to every vehicle you get into.
- **Realistic light.** Six head types with real dimensions. Brightness comes from presets or exact candela, lumen,
  or lux at a distance, on the same scale as the game's own light parts. Six LED colors with three tones each
  (for example red 625 nm, police blue 470 nm, white 6000 K), and an optional second color per zone for takedown,
  scene, alternating, traffic arrow or cruise.
- **Patterns.** 31 modes, 21 per-zone patterns, A/B phase groups, phase offset, per-zone level and a sequential
  traffic advisor.
- **Fast editing.** Color, tone, brightness and pattern changes apply instantly, without reloading the vehicle.
  Position and count changes show wire-box previews on the car first, then the vehicle reloads once.
- **Extras:** a multicolor speaker LED bar (116 / 139 / 161 cm), copies of any lightbar from the vehicle or other
  mods, a Light Studio for every warning light on the vehicle, per-vehicle and global profiles, an option to hide
  overlapping factory flashers, a radial menu entry and key bindings.

| Zone editor | Turkish interface |
|---|---|
| ![](docs/img/ui_en_zone.png) | ![](docs/img/ui_tr_zone.png) |

![Light and Profiles tabs](docs/img/ui_en_light_profiles.png)

Automatic placement on a mod vehicle exported from Automation:

![Placement on a mod vehicle](docs/img/placement_mod_vehicle.jpg)

## Install

1. Download `better_concealed_flashers_pro.zip` from **Releases**.
2. Put the zip, **without extracting it**, into `%LOCALAPPDATA%\BeamNG\BeamNG.drive\current\mods\`.
3. Start the game and add the UI app **Concealed Flashers PRO · Gizli Çakar PRO** (UI Apps → Add app).

## Quick start

1. Get into any car or truck.
2. Pick a **kit** and a **color scheme** in the Placement tab, or click a single zone on the map.
3. Click a lit zone to fine-tune it: count, spacing, head type, colors, brightness, pattern and position.
4. Turn the lights on with **LIGHTS** / **SIREN** in the app header, or with the game's lightbar key. Browse
   modes with ◀ ▶.
5. Save the vehicle configuration in Vehicle Config to keep the setup. It is stored in the configuration itself.

Switch the language with **TR / EN** in the app header. The default follows the game language.

Demo configurations: *Lansdale* and *Fullsize* → "Undercover — Concealed Flashers PRO", *Fullsize* → "LED bar —
Concealed Flashers PRO".

Upgrading from version 2: old settings are converted automatically. Fine-tuning offsets are reset because heads
are now placed on the real surface.

## Compatibility

- BeamNG.drive 0.40 or newer.
- Checked on all 39 vanilla vehicles (584 zones placed, no errors) and on several mod vehicles, including
  Automation exports.
- A zone that does not exist on a vehicle, like a rear window on an ATV, is greyed out on the map instead of being
  placed somewhere wrong.

## For developers

```
python3 tools/build.py          # builds dist/better_concealed_flashers_pro.zip
python3 tools/gen_assets.py     # regenerates the head meshes and materials in vehicles/common/bcfp_pro
```

`tools/bench/eng.py` runs the game's own jbeam loader in LuaJIT (through `lupa`) outside the game, with the mod
injected, so the whole pipeline can be tested without starting BeamNG:

```
pip install lupa
export BEAMNG_GAME="/path/to/BeamNG.drive"
python3 tools/bench/eng.py tests/t_full.lua lansdale:25_base_A    # one vehicle, all zones
python3 tools/bench/eng.py tests/t_ui.lua lansdale                # UI layer: kits, live edits, profiles, language
python3 tools/bench/eng.py tests/t_batch.lua $(cat tools/bench/cars.txt)
```

```
mod/                                   contents of the mod zip
  lua/ge/extensions/bcfpPro.lua        game-engine extension (loader hooks, UI bridge)
  lua/ge/extensions/bcfp/              scan (3D surface model), place (zone solvers), hints (factory positions),
                                       env (per-vehicle cache, body binding), gen and inject (generated parts),
                                       ui (state, commands, kits, live edits) ...
  lua/vehicle/controller/bcfp_flasher.lua   modes, patterns, traffic advisor
  ui/modules/apps/BcfpStudio/          UI app (English and Turkish texts in app.js)
  vehicles/common/bcfp_pro/            head meshes, LED bar, materials
tools/                                 build, asset generator, renderer, offline test bench
tests/                                 bench scripts
```

Code comments are mostly in Turkish.
