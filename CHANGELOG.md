# Changelog

All notable changes to **ZX Spectrum Tape Image Loader** are documented in this file.

This project follows Semantic Versioning:

- **MAJOR** – Significant new functionality or breaking changes.
- **MINOR** – New features and major improvements.
- **PATCH** – Bug fixes, optimizations, and compatibility updates.

---

# [Unreleased, Coming Soon]

## Planned Features

### BASIC Editor
- Sinclair BASIC syntax highlighting.
- Auto-indent and code formatting.
- Line renumbering.
- Variable explorer.
- Tokenized BASIC viewer.

### Spectrumizer
- Additional ZX Spectrum graphic modes.
- Better attribute clash reduction.
- Improved colour matching.
- User-defined palettes.

### ASM Converter
- Z80 assembler improvements.
- Additional assembler directives.
- Symbol browser.
- Label navigation.
- Binary memory viewer.

### Tape System
- TZX export support.
- Pulse editor.
- Tape block inspector.
- Turbo loader support.

---

# Version 1.2.0
Released: 2026-07-22

## New Features

### ASM → TAP Converter

Added a complete Assembly Converter module.

Features include:

- Import `.ASM` source files.
- Edit assembly source.
- Compile source into machine code.
- Generate CODE tape blocks.
- Export `.TAP`.
- Optional BASIC auto-loader.
- Automatic ORG detection.
- Configurable execution address.
- Assembly error reporting.
- Status console.

---

### BASIC Editor

Added image integration.

New capabilities:

- Select PHOTO / IMAGE button.
- Automatic image loading.
- Image preview.
- SCREEN$ generation.
- BASIC loader generation.

Image Fit Modes:

- Crop
- Smart Contain
- Pad
- Stretch

Additional improvements:

- Improved image scaling.
- Better monochrome conversion.
- Better attribute optimisation.

---

### Spectrumizer

New image conversion improvements.

Supported video modes:

- Standard ZX Spectrum
  - 256×192
  - 6144 bitmap bytes
  - 768 attribute bytes
  - 6912 bytes total

- Monochrome Bitmap

- Timex Hi-Color

- Mode 4 (16-colour bitmap)

- Extended Hi-Resolution Bitmap

Added:

- Better Floyd-Steinberg dithering.
- Improved nearest-colour search.
- Faster rendering.
- Improved preview quality.
- Better colour attribute generation.

---

### Tape Simulator

Added improvements:

- Better loading animation.
- Improved border flashing.
- Variable block sizes.
- Better timing accuracy.
- Faster rendering.

---

### WAV Export

Improvements:

- Cleaner generated audio.
- Better pulse timing.
- Improved amplitude stability.
- Better compatibility with emulators.

---

### WAV Decoder

Improvements:

- Better Schmitt Trigger decoding.
- Improved edge detection.
- Better noise handling.
- Improved decoding accuracy.

---

### Manual

Added comprehensive documentation.

Sections include:

- Introduction
- Sinclair BASIC
- BASIC Editor
- Adding Images
- Spectrumizer
- Tape Simulator
- WAV Decoder
- ASM Converter
- Extended Graphic Modes
- Compiler
- FAQ
- Troubleshooting

---

## Improvements

### User Interface

- Better mobile layout.
- Improved touch controls.
- Faster loading.
- Better button grouping.
- Cleaner dialogs.

---

### Performance

- Reduced memory usage.
- Faster image conversion.
- Faster tape generation.
- Better cache management.
- Optimised rendering pipeline.

---

### Compatibility

Tested with:

- Fuse
- Spectaculator
- ZXSpin
- EightyOne
- Unreal Speccy
- ZEsarUX

---

## Bug Fixes

### BASIC Editor

Fixed:

- Image import failures.
- Missing SCREEN$ loader.
- Incorrect image scaling.
- Image preview refresh.
- Tape generation issues.

---

### Spectrumizer

Fixed:

- Bitmap mode selection.
- Colour bitmap rendering.
- Attribute generation.
- Dithering overflow.
- Buffer allocation.
- Preview refresh.
- Colour conversion logic.

---

### Tape Generator

Fixed:

- Incorrect tape block sizes.
- Header generation.
- Data block ordering.
- Loader generation.
- Export validation.

---

### WAV System

Fixed:

- Timing drift.
- Audio clipping.
- Decoder instability.
- Noise detection.
- Playback synchronisation.

---

### ASM Converter

Fixed:

- Empty source handling.
- Invalid ORG detection.
- Execution address validation.
- Unsupported opcode reporting.
- Compiler status updates.

---

# Version 1.1.0
Released: 2026-07-19

## Added

### Extended Graphic Modes

Added support for:

- Standard ZX Spectrum
- Timex Hi-Color
- Mode 4
- Extended Hi-Resolution

---

### Image Processing

Added:

- Floyd-Steinberg dithering.
- Better greyscale conversion.
- Improved colour matching.

---

### Tape System

Added:

- Better WAV export.
- Improved Tape Simulator.
- Improved decoder.

---

## Fixed

- Screen buffer allocation.
- Attribute overflow.
- Image conversion.
- Tape generation.
- WAV decoding.

---

# Version 1.0.0
Released: 2026-07-15

## Initial Release

Initial public version.

Included:

- Spectrumizer
- Sinclair BASIC Editor
- Tape Simulator
- TAP Export
- WAV Export
- WAV Decoder
- Manual
- Mobile interface

---

# Repository Information

## Reporting Bugs

Use the following GitHub Issue templates:

- 🐞 Bug Report
- ⚠ Error Report
- 🔧 Code Problem
- 🔄 Process Problem
- ✨ Feature Request
- 📉 Regression Report
- ❓ Question

## Contributing

Contributions are welcome.

Areas include:

- Sinclair BASIC
- Z80 Assembly
- Tape formats
- Image conversion
- Audio decoding
- Documentation
- UI improvements
- Performance optimisation
- Emulator compatibility