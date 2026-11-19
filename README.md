# Project Status: Ended (November 25, 2026)

**ZX Spectrum Mobile Tape & Image Loader / ASM Converter** reaches its end on **25 November 2026**.

From that date the project is **archived**. There will be no further releases, bug fixes, or feature updates, and issues and pull requests will no longer be reviewed.

---

## Final release

| | |
|---|---|
| **Final version** | v1.5.2.9-RELEASE |
| **File** | `zx_spectrum_mobile_tape_image_loader.html` |
| **Type** | Single-file HTML/JS/CSS app, no install and no server needed |
| **History** | See [`CHANGELOG.md`](CHANGELOG.md) |

Open the HTML file in any modern browser, on desktop or mobile. It keeps working offline.

## What the project does

- **Spectrumizer:** converts images to ZX Spectrum screens, with Bayer and Floyd-Steinberg dithering and attribute handling.
- **BASIC Editor:** Sinclair BASIC tokenizer, linter, and a `.TAP` export with an optional loading screen.
- **ASM Converter:** Z80 assembler with a disassembly listing, symbol browser, compile log (errors, warnings, success), and `.TAP` export.
- **Tape Play and WAV Decode:** play `.TAP` files as audio and decode tape audio back to data.
- **Extras & FX:** CRT filter, UI sound effects, easter eggs, and font style options.

## Known limitations at end of life

- Light, Dark and System themes and colour schemes were planned but never shipped.
- The disassembler cannot tell data (`DB`/`DEFM`) from code.
- SF Pro Display only shows on Apple devices. Other devices fall back to Inter or the system font.
- The app is tested against a mocked browser environment, not on every real device.

## Using it after the end date

The app is self-contained, so it will keep working as long as browsers run HTML. You are welcome to:

- keep using the final release as it is;
- fork the repository and continue development under your own name;
- reuse any part of the code for your own retro-computing projects.

Forks should keep the original licence terms and give credit to this project.

## Thank you

Thanks to everyone who tested builds, reported bugs, and suggested features. Happy loading, and may your tapes never need a second pass.

---

*Archived on 25 November 2026.*


# 📼 ZX Spectrum Tape & Image Loader Editor

A completely client-side retro-computing tool optimized for modern browsers. This single-file web application allows you to convert images, write native Sinclair BASIC, compile `.TAP` files, and synthesize real-time cassette loading audio directly in your browser.

See the [Changelog](CHANGELOG.md) for version history.

## ✨ Features

 * **🖼️ Image Spectrumizer (Convert to SCR):** Convert modern PNG/JPG photos into authentic ZX Spectrum screen memory dumps. Features multiple fit modes, pixel chunk sizes, brightness/contrast controls, and Floyd-Steinberg dithering.

 * **⌨️ Sinclair BASIC Editor:** Write native ZX Sinclair BASIC. The compiler tokenizes keywords automatically and builds real native bytecode block payloads. Supports 48K, 128K, and Timex Sinclair 2068 target machines.

 * **⚙️ ASM to TAP Converter:** Write Z80 Assembly machine code right in the browser. Supports labels, standard directives (ORG, DB, DW, DS), and compiles directly into executable .TAP blocks with optional automatic BASIC loaders.

 * **▶️ Tape Playback Simulator:** Upload a .TAP file and play it back with synthetic, real-time edge sounds. Border flashing synchronizes perfectly with the data blocks. Includes Standard, Fast, and Turbo speed options.
 * **🔊 Real WAV Audio Decoder:** Upload genuine audio cassette frequencies (.WAV) and decode them back into data using offline analysis and Schmitt-trigger edge evaluation.
 * **💾 Exporting:** Export your creations directly to .TAP or synthesize them into .WAV audio files.
 * **🕹️ Extras:** Includes a CRT Tube Overlay filter, screen scramblers (TV Static), and a 1-Bit "Beeper" soundboard.

## 🚀 How to Use
Since this is a completely client-side application built into a single HTML file, there is no installation or server required!
 1. Download the [zx_spectrum_mobile_tape_image_loader.html](zx_spectrum_mobile_tape_image_loader.html) or latest .html release file from this repository.
 2. Open it in any modern web browser (Chrome, Safari, Firefox, Edge).
 3. The app is fully responsive and optimized for mobile devices, so you can code on the go!

## 🐛 Issues & Bug Reports
Did you find a bug, graphical glitch, or tape compilation error? Or maybe you have a great idea for a new retro feature? We want to hear about it!
Please use the GitHub Issue to report problems or request features:

 * **Report a Bug:** Open a Bug Report

 * **Request a Feature:** Open a Feature Request

*When reporting a bug, please include as much detail as possible, including your device, browser, and the steps to reproduce the error. (But, this issues will be build and how really are bug is just happen with AI made.)*

## 🛠️ Tech Stack
Made by: Google Gemini Flash, Pro, & ChatGPT.
Built entirely with Vanilla HTML5, CSS3, and JavaScript. **Zero external libraries.** * **Canvas API:** Used for pixel-perfect attribute clash rendering and extended video modes (Mode 4, Timex Hi-Color).

*   **Canvas API:** Used for pixel-perfect attribute clash rendering and image scaling.
*   **Web Audio API:** Used for highly accurate cassette tape synthesis and Schmitt-trigger edge-detection decoding.

## 👤 Creator & Credits

Created and developed by **RiziqMaulana** *(AKA CSJArchive, CSJA, and CSJ486 Alternative names)*.

**Follow me on Social Media:**
*   📺 **YouTube:** [m.youtube.com/@csjarchive](https://www.youtube.com/@csjarchive)
*   💬 **Discord:** [discord.gg/zBqHAFyj2n](https://discord.gg/zBqHAFyj2n)
*   🎨 **DeviantArt:** [deviantart.com/riziqmaulana](https://www.deviantart.com/riziqmaulana)
*   🏛️ **Internet Archive:** [archive.org/details/@riziq_maulana](https://archive.org/details/@riziq_maulana)
*   ✖️ **X (Twitter):** [x.com/RMaulana52881](https://x.com/RMaulana52881)
*   🖥️ **GitHub:**
*It's already you're view it.*

## ⚖️ Trademarks & Legal
"ZX Spectrum" and "Sinclair" are registered trademarks of Amstrad / Sinclair Research Ltd. This application is an independent fan-made tribute and educational tool, and is not affiliated with, authorized, or endorsed by the trademark owners.
