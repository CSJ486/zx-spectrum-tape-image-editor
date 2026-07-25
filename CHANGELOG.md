# Changelog

All notable changes to **ZX Spectrum Tape Image Loader Editor** are documented in this file.

This project uses Semantic Versioning:

- **MAJOR** — major feature sets, large UI overhauls, or breaking workflow changes
- **MINOR** — new capabilities and feature expansions
- **PATCH** — bug fixes, compatibility improvements, and small refinements

---

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
