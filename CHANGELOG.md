# Changelog

All notable changes to **ZX Spectrum Tape Image Loader Editor** are documented in this file.

This project uses Semantic Versioning:

- **MAJOR** — major feature sets, large UI overhauls, or breaking workflow changes
- **MINOR** — new capabilities and feature expansions
- **PATCH** — bug fixes, compatibility improvements, and small refinements

Format loosely follows [Keep a Changelog](https://keepachangelog.com/). Versioning here tracks this project's own internal build history rather than strict semver — adjust version numbers/dates below to match your actual GitHub tags before publishing.

---

## [1.5.2.9] - 2026-11-02

### Added
- **Typography:** SF Pro Display font stack as the new default (`-apple-system`, "SF Pro Display", Inter, system-ui fallbacks), with tighter tracking and antialiasing.
- **Extras & FX:** Font Style picker (SF Pro Display, SF Pro Text, SF Pro Rounded, New York serif, SF Mono, System UI), A-/A+ text size (80-130%), live preview. Saved in localStorage.
- **ASM Converter:** Compile Log view with timestamped Error / Warning / Success / Info entries, filter chips with counts, clickable line numbers that jump to the source line, Copy, Save (.txt) and Clear.
- **ASM Converter:** Compile now reports *all* errors at once (unknown instructions, duplicate labels, bad expressions) instead of stopping at the first, and does not write a .TAP while errors exist.
- **ASM Converter warnings:** unused labels, DB values that don't fit a byte, program not ending in RET/JP/JR/HALT, DI without EI before RET, `JR $` infinite loop, origin in ROM / screen / system-variable area, code reaching top of RAM.
- **ASM Converter:** "Check Only (no .TAP)" button, "Jump to First Problem", optional "Live check while typing", and Ctrl/Cmd+Enter to compile.

### Notes
- SF Pro is an Apple system font and is not embedded; non-Apple devices fall back to Inter/system fonts.

---

## [1.5.2.5] - 2026-09-20

### Added
- **Spectrumizer:** Flip Horizontal / Flip Vertical for the source image (applied before conversion, reset by Reset Spectrumizer).
- **Spectrumizer:** Download Raw .SCR — saves the converted screen as a standard Spectrum `.scr` file (6912 bytes in Standard mode, 12288 in Timex Hi-Colour).
- **Spectrumizer:** Colour Usage — shows what percentage of the screen each of the Spectrum's colours (including Bright variants) occupies.
- **BASIC Editor:** Find & Replace with a match-case option, plus a Count Matches button.
- **BASIC Editor:** Uppercase Keywords — converts keywords to uppercase while leaving string contents, `REM` comments, and variable names alone.
- **BASIC Editor:** Download .BAS — saves the program source as a text file.
- **ASM Converter:** the Disassembly Preview now has a T-state column (taken/not-taken timings for conditional branches) and a one-pass total with an estimated time at 3.5 MHz.
- **ASM Converter:** Download .BIN (raw assembled bytes) and Download Listing (.lst).

### Fixed
- ASM assembler: duplicate labels were silently overwritten, so a jump could quietly land on the wrong copy. They now stop the build with a clear error naming the line (labels are not case-sensitive).
- ASM snippets: inserting the same snippet more than once used to create exactly that duplicate-label situation. Repeat insertions now get numeric suffixes (`DELAY2`, `DELAYLOOP2`, ...) with their internal references updated to match.
- BASIC linter: `FOR`/`NEXT`/`GOTO` text inside string literals or `REM` comments (for example `PRINT "FOR YOU"`) was counted as real code and produced false warnings; unclosed-quote detection no longer trips on quotes inside a `REM` comment.

---

## [1.5.2] - 2026-09-20

### Added
- **Spectrumizer:** Auto-Contrast — one-tap histogram stretch that computes brightness/contrast slider values from the source image's actual luminosity range.
- **Spectrumizer:** Download PNG Preview — exports the current Spectrum-accurate converted image as a plain PNG.
- **Spectrumizer:** Invert Source Colours toggle.
- **Spectrumizer:** Before/After Compare — briefly shows the original source photo over the converted preview.
- **BASIC Editor:** Insert Snippet library (Border Colour Cycle, INK/PAPER Setup, FOR/NEXT Loop, INPUT Prompt, BEEP Tune), auto-numbered and appended to the program.
- **BASIC Editor:** Copy Code to clipboard.
- **BASIC Editor:** Check for Issues — a linter catching duplicate line numbers, lines out of ascending order, unclosed string literals, `GOTO`/`GOSUB` targets that don't exist, and mismatched `FOR`/`NEXT` counts.
- **ASM Converter:** Insert Snippet library (Clear Screen, Print Char via `RST 16`, Delay Loop, Border Colour Flash).
- **ASM Converter:** Copy Code to clipboard.
- **ASM Converter:** Disassembly Preview — a Z80 disassembler covering the assembler's own instruction subset, shown alongside the existing symbol browser and hex dump so compiled output can be sanity-checked at a glance.

---

## [1.5.1] - 2026-09-20

### Added
- Full iOS-style visual redesign: segmented-control tab bar, iOS-proportioned toggle switches (green on-state), rounded card styling, sticky translucent/blurred header, and tactile press-down animation on every button, tab, and switch.
- UI sound effects (synthesized via Web Audio, no asset files): click, toggle, a success chime on compiles/loads completing, and an error tone on failures. Includes a master on/off switch under Extras & FX.
- Three hidden easter eggs: the Konami code (rainbow screen flash), tapping the header logo 7 times quickly, and typing "MANIC" into the BASIC code editor.

---

## [1.5.0] - 2026-09-20

### Added
- **Tape Blocks** visual inspector (BASIC Editor tab): lists every block on a compiled/loaded tape with an icon, `Program:`/`Code:`/`Data`/`Pause` label, byte count, and a running `mm:ss` timestamp computed from real ZX Spectrum ROM cassette-loading timing (pilot tone, sync, and per-bit pulse widths). A corrupt block (checksum mismatch) renders as its own clearly flagged row instead of breaking the list.
- **Extra BASIC Data Headers**: a repeatable list of additional named Code/Data block pairs a compiled tape can carry, each with its own text content, plus Duplicate and Remove controls per entry.
- Attribute-clash heatmap overlay for the Spectrumizer preview — highlights, per 8×8 cell, how many pixels had to be forced onto the "wrong" PAPER/INK colour.
- Dithering algorithm selector — **Version 1** (ordered/Bayer matrix dithering, a regular crosshatch texture) and **Version 2** (Floyd-Steinberg error diffusion). The choice is shared between the Spectrumizer and BASIC Editor tabs.
- CB-prefixed Z80 instruction group in the ASM assembler: `RLC`, `RRC`, `RL`, `RR`, `SLA`, `SRA`, `SLL`, `SRL`, `BIT`, `SET`, `RES`.

### Fixed
- ASM assembler: the source line-splitting regular expression was double-escaped (matching the literal text `\r\n` instead of an actual line break), so any multi-line assembly program failed outright. Also fixed the same corruption in the label-detection and opcode/operand-split regular expressions.
- ASM assembler: the two-pass size-estimation step had no case for `INC`/`DEC`, so any program using either instruction — arguably the most common Z80 instructions after `LD` — failed before assembly could even begin.
- BASIC compiler: the compiled tape wrote the loading-screen image block *before* the BASIC program block, but the program's own first line (`LOAD "" SCREEN$`) expects the image to be the *next* block after the program runs. Program now always compiles first.
- Floyd-Steinberg dithering: per-pixel comparisons were reading a pixel snapshot captured before dithering began, so error diffused from an earlier pixel in the same 8×8 cell had no effect on later pixels in that cell — silently dropping most of the diffusion weight.
- Floyd-Steinberg dithering: reworked into a two-pass architecture (colour selection from pristine, undiffused source pixels; a single continuous diffusion pass across the whole image) after finding that confining diffusion to each cell produced a repeating tile/grid artifact on smooth gradients, while letting diffused error feed back into a neighbouring cell's own colour choice caused bright colours to bleed into unrelated flat areas.

---

## [1.4] - earlier baseline

- Starting point for the above work: image-to-Spectrum converter (Spectrumizer) with brightness/contrast/saturation/edge-boost controls and attribute-clash reduction, a Sinclair BASIC editor/tokenizer/compiler, a Z80 subset assembler, a TAP/TZX tape cassette simulator with synthesized loading audio, and a WAV decoder — the base feature set this changelog's fixes and additions build on.


# [Unreleased]

## Planned Features

### BASIC Editor
- Sinclair BASIC syntax highlighting.
- Auto-indent and code formatting.
- Line renumbering tools.
- Variable explorer for program analysis.
- Tokenized BASIC viewer for compiled output.
- Better image loader workflow for `SCREEN$` programs.
- More loader presets for tape-based BASIC demos.

### Spectrumizer
- Additional ZX Spectrum graphic modes.
- Better attribute clash reduction.
- Improved colour matching and palette selection.
- User-defined palette support.
- Cleaner image preview for conversion results.
- Improved handling for standard 6,912-byte Spectrum bitmap layouts.
- Faster dithering and bitmap conversion on mobile devices.

### ASM Converter
- Z80 assembler improvements.
- Additional assembler directives.
- Symbol browser for labels and addresses.
- Label navigation and code lookup.
- Binary memory viewer for generated machine code.
- Better error messages for invalid source.
- Improved BASIC loader generation for assembled code.

### Tape System
- TZX export support.
- Pulse editor for advanced tape editing.
- Tape block inspector.
- Turbo loader support.
- Better compatibility with emulators and tape players.
- More reliable block generation for BASIC, SCREEN$, and ASM builds.
- Faster tape simulation and more accurate playback timing.

### WAV Tools
- Cleaner WAV export output.
- Improved Schmitt-trigger decoding accuracy.
- Better noise handling during real tape decoding.
- More stable audio analysis for long cassette recordings.
- Support for additional tape capture formats.

### Interface
- Cleaner mobile layout for small screens.
- Better tab switching and status feedback.
- More helpful status messages during conversion and export.
- Improved manual pages and in-app guidance.

---

# [1.3.6.2] - 2026-07-25

## Added

### Spectrumizer
- Added a dedicated palette strategy selector for image conversion workflows.
- Added attribute clash reduction controls to help reduce blocky colour overlap.
- Added a blank export filename field so users can choose their own tape/program name.
- Added a cleaner preview flow for image conversion and screen export.

### BASIC Editor
- Added additional helper panels for code-assisted editing.
- Added richer editing feedback for image-based BASIC workflows.
- Added visible layout blocks for syntax preview and tokenized output support.

### ASM Converter
- Added live symbol browsing support for labels and addresses.
- Added a binary memory viewer panel for compiled machine code.
- Added better assembler workflow controls and clearer compile feedback.

## Changed

### Spectrumizer
- Improved the layout of the image conversion controls on mobile.
- Refined the standard ZX Spectrum 6,912-byte bitmap workflow.
- Updated the screen export name field to begin blank instead of prefilled.

### BASIC Editor
- Improved the BASIC editor workflow for loader-style tape programs.
- Better aligned the editor layout for long BASIC listings and helper panels.

### ASM Converter
- Improved the assembler editor layout and readability.
- Better aligned compile controls for machine-code-to-tape workflows.

## Fixed

### Spectrumizer
- Fixed control alignment issues in the image conversion tab.
- Fixed the export filename workflow so it no longer forces a default text value.
- Fixed several UI spacing issues on small screens.

### BASIC Editor
- Fixed panel spacing problems around code helpers and compile controls.
- Fixed display issues related to editor status and helper areas.

### ASM Converter
- Fixed layout issues in the symbol browser and binary viewer panels.
- Fixed spacing and visibility problems for assembly compile controls.

---

# [1.3.6.1] - 2026-07-25

## Added

### Tape System
- Added TZX export support.
- Added a tape data selector so Spectrumizer and BASIC Editor can choose between TAP and TZX output.
- Added a pulse editor concept for advanced tape editing workflows.
- Added a tape block inspector for reviewing generated blocks.
- Added turbo loader support.
- Added broader emulator and tape-player compatibility goals.
- Added more reliable block generation for BASIC, SCREEN$, and ASM builds.
- Added faster simulation timing and improved playback accuracy.

### WAV Tools
- Added cleaner WAV export output.
- Added improved Schmitt-trigger decoding accuracy.
- Added better noise handling during real tape decoding.
- Added more stable audio analysis for long cassette recordings.
- Added support for additional tape capture formats.

### Spectrumizer
- Added a message and workflow note for the export header filename field.
- Added tape output selection support to match future TAP/TZX workflows.

## Changed

### Spectrumizer
- Updated the export filename field so it starts blank instead of using a preset value.
- Improved the layout of the tape export controls.
- Refined the screen-to-tape generation workflow.

### BASIC Editor
- Added TAP/TZX output selection support for BASIC tape builds.
- Improved tape export workflow for BASIC programs that include screen data.

## Fixed

### Tape System
- Fixed several block-generation edge cases for exported tape data.
- Fixed timing inconsistencies in tape simulation playback.
- Fixed compatibility issues in generated audio/tape workflows.

### WAV Tools
- Fixed some waveform timing and decoding stability issues.
- Fixed output noise handling in real tape analysis.

---

# [1.3.5] - 2026-07-24

## Added

### BASIC Editor
- Added Sinclair BASIC syntax highlighting support in the editor workflow.
- Added auto-indent and code formatting tools.
- Added line renumbering tools for BASIC listings.
- Added a variable explorer for program analysis.
- Added a tokenized BASIC viewer for compiled output.
- Added a better image loader workflow for `SCREEN$` programs.
- Added more loader presets for tape-based BASIC demos.

### Spectrumizer
- Added additional ZX Spectrum graphic modes.
- Added improved attribute clash reduction controls.
- Added improved colour matching and palette selection.
- Added user-defined palette support.
- Added cleaner image preview output for conversion results.
- Added improved handling for the standard 6,912-byte Spectrum bitmap layout.
- Added faster dithering and bitmap conversion behavior for mobile devices.

### ASM Converter
- Added Z80 assembler improvements.
- Added support for additional assembler directives.
- Added a symbol browser for labels and addresses.
- Added label navigation and code lookup.
- Added a binary memory viewer for generated machine code.
- Added better error messages for invalid source.
- Added improved BASIC loader generation for assembled code.

### Interface
- Added clearer status feedback across conversion and compile steps.
- Added a more responsive mobile layout for smaller screens.
- Added cleaner tab switching behavior.
- Added improved manual pages and in-app guidance.

## Changed

### BASIC Editor
- Improved how converted screen data is attached to BASIC tape builds.
- Improved the editor’s support workflow for image-based loaders.

### Spectrumizer
- Improved image conversion controls and workflow feedback.
- Improved the export naming flow so users can set names manually.

### ASM Converter
- Improved assembler compile messaging and source handling.
- Improved code-to-tape workflow clarity.

## Fixed

### BASIC Editor
- Fixed image-loader layout and compilation issues.
- Fixed issues where some converted image paths were not reflected in the tape output.

### Spectrumizer
- Fixed standard bitmap mode handling and mode descriptions.
- Fixed export filename behavior and UI spacing problems.

### ASM Converter
- Fixed source handling problems for malformed or incomplete assembly input.
- Fixed status panel visibility and layout issues.

---

# [1.2.0] - 2026-07-22

## Added

### Spectrumizer
- Added a more complete image-to-spectrum conversion workflow.
- Added support for standard ZX Spectrum screen-style bitmap exports.
- Added image fit controls for conversion tuning.

### BASIC Editor
- Added image loading into BASIC tape workflows.
- Added `Select PHOTO / IMAGE` support for screen-based BASIC programs.
- Added the `SCREEN$` loader path for tape-based image demos.

### Manual
- Added a fuller in-app manual with sectioned help content.
- Added release-oriented documentation for major tabs and workflows.

### GitHub Workflow
- Added GitHub issue templates for bugs, errors, feature requests, and process problems.

## Changed

### Spectrumizer
- Improved the conversion workflow for standard 256×192 screen layouts.
- Improved mobile usability and general image preview handling.

### BASIC Editor
- Improved the tape compiler flow for BASIC programs with screen images.
- Improved the default loader example and tape naming workflow.

## Fixed

### BASIC Editor
- Fixed problems where image selections were not correctly attached to BASIC tape builds.
- Fixed some screen-loader flow issues.

### Spectrumizer
- Fixed several preview and layout issues in the image conversion workflow.

---

# [1.0.0] - 2026-07-15

## Initial Release

### Spectrumizer
- First release of the image conversion tab.
- Basic ZX Spectrum screen conversion workflow.
- Initial dithering and preview pipeline.

### BASIC Editor
- First release of the Sinclair BASIC editor.
- Basic tape compilation workflow.
- Initial program example presets.

### Tape Play
- First release of the tape simulator tab.
- Basic tape playback controls.
- Initial exported tape preview support.

### WAV Decode
- First release of the WAV decoding tab.
- Initial cassette audio analysis workflow.

### Extras & FX
- First release of visual and audio extras.
- CRT overlay and screen utilities.

### Manual
- First release of the user manual tab.
