# PhotonWorks

A Windows astrophotography application: stack your subs and process the result, in one program.

PhotonWorks wraps the [Siril](https://siril.org) engine for calibration, registration and stacking, and adds a full image editor on top of it — 41 processing tools, a multi-image workspace, masks, and a live preview on everything.

![Version](https://img.shields.io/badge/version-1.0.9-blue) ![Licence](https://img.shields.io/badge/licence-GPL--3.0-green) ![Platform](https://img.shields.io/badge/platform-Windows-lightgrey)

---

## What it does

**Stacking.** Every option Siril's `stack` command accepts — five methods, eight rejection types, frame filtering by FWHM, roundness, background or star count, drizzle on the registration step, and a timing summary at the end of every run.

**Editing.** Several images open at once, each in its own window with its own undo history, screen stretch, zoom and pan. Tile and cascade them, or minimise them to icons on the workspace.

**Tools.** 41 of them, grouped by what they do:

| Group | Tools |
|---|---|
| Masking | Shape Mask, RangeSelection Mask |
| Image Prep | View FITS Header, Bin/Downscale, Set Preview Region, Crop Tool, Blemish Blaster |
| Calibration & Astrometry | Image Solver, SPCC, LinearFit |
| Background | Manual Background Extraction, GraXpert, Background Extraction, Background Neutralization |
| Noise & Sharpening | Xterminator Tools |
| Star Tools | RGB Stars to NB, Star Reduction, Screen Stars, Star Stretch, NB to RGB Stars |
| Stretch | Simple Stretch, Histogram Transformation, GHS, Curves, VeraLux HyperMetric Stretch |
| Tone | Camera RAW Editor |
| Structure & Detail | Dust Lane Enhancer, Dark Structure Enhance, Multiscale Local Contrast |
| Colour | Astro Color Mixer, Color Masks, Color Saturation, SCNR, Correct Magenta Stars |
| Channels & Palettes | Split Channels, PixelMath, Combine LRGB / Narrowband, Continuum Subtraction, Add Narrowband to RGB, Narrowband Normalization, Dual-Band to SHO |

**Formats.** FITS, XISF, TIFF, PNG, JPEG, and camera raw (CR2, NEF, ARW). XISF headers are read and written the same way FITS ones are.

---

## Installing

1. Download the latest release `.zip` from the [Releases](../../releases) page.
2. Unzip it anywhere — the Desktop is fine.
3. Run `PhotonWorks.exe`.

No installer, no dependencies to fetch, nothing written outside the program folder and your own settings. Siril is bundled, so you do not need to install it separately.

Settings, stacking profiles and processing history live in `%APPDATA%\PhotonWorks\` and survive updates.

### Windows SmartScreen

The .exe is not code-signed, so Windows may warn on first run. Choose **More info → Run anyway**. The source is in the release zip if you would rather build it yourself.

---

## Optional extras

PhotonWorks works fully without these. Point it at them in **Advanced Settings** if you have them:

- **[GraXpert](https://graxpert.com)** — an alternative background extraction engine
- **[RC-Astro CLI](https://www.rc-astro.com)** — BlurXTerminator, StarXTerminator and NoiseXTerminator. Licensed separately by RC-Astro; PhotonWorks never stores your licence details, it only calls the CLI.

---

## Building from source

The full source is included in every release. To build it yourself:

```
py -m pip install pyinstaller customtkinter numpy opencv-python astropy pillow matplotlib xisf tkinterdnd2 psutil
py -m PyInstaller --onedir --noconsole -n PhotonWorks --icon PhotonWorks_icon.ico "PhotonWorks v1.0.9.py"
```

Keep `PhotonWorks_icon.ico` and `PhotonWorks_watermark.png` beside the source — the app looks for both there.

There is a built-in engine self-test, which opens no window:

```
py "PhotonWorks v1.0.9.py" --selftest
```

---

## Licence

PhotonWorks is free software under the **GNU General Public License v3**. See [LICENSE](LICENSE). The full source is included in every release download.

**Siril** is bundled unmodified as its official portable build and is also GPL v3. Its licence and AUTHORS file ship with it in the `Siril` folder inside the program folder; its source is at [gitlab.com/free-astro/siril](https://gitlab.com/free-astro/siril).

### Credits

Tools in PhotonWorks are ports of, or built from, published work by:

- **Bill Blanshan** — Color Masks, Star Reduction PixelMath methods
- **Bill Blanshan & Mike Cranfield** — Narrowband Normalization, Screen Stars
- **Dave Payne & Mike Cranfield** — Generalized Hyperbolic Stretch (GHS)
- **Franklin Marek / Seti Astro** — Blemish Blaster, Continuum Subtraction, NB to RGB Stars, Star Stretch
- **Riccardo Paterniti** — VeraLux HyperMetric Stretch
- **RC-Astro (Russell Croman)** — the Xterminator tools, called through their own CLI
- **PixInsight / Pleiades Astrophoto** — RangeSelection reference behaviour
- **Siril Gaia DR3 Astrometry Catalogue** — Richard, Melis, Knagg-Baugh & Cass (CC BY 4.0)

Full credits are in the app under **Help → About / Credits**.
