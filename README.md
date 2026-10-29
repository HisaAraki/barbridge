# BarBridge

English | [日本語](README.ja.md)

**A language-independent core for GS1 Sunrise 2027 1D/2D barcode generation, written in Rust, usable from any language across a C ABI boundary (in development)**

## What this is

In 2027, GS1 is moving retail POS barcode practice away from 1D-only symbols (EAN/UPC, etc.)
toward pairing them with 2D symbols (GS1 QR Code / GS1 DataMatrix) — the **GS1 Sunrise 2027**
initiative. This lets a single symbol carry attribute data such as lot number and expiration
date alongside the GTIN, but during the transition period, retailers and manufacturers need to
print both symbol types together, at the right size and layout.

BarBridge is a core library built for this transition: it generates 1D/2D barcodes that conform
to GS1 specifications.

## Concept

- **GS1-compliant size optimization**: computes the optimal scale so the barcode's print size
  (X-dimension) stays within GS1's specified range while automatically fitting a target output
  size (e.g. 50mm × 50mm).
- **Combined 1D + 2D rendering**: automatically selects an appropriate arrangement (side-by-side,
  stacked, etc.) to pair a 1D symbol and a 2D symbol representing the same GTIN.
- **A language-independent core, written in Rust**: the logic lives in a single safe,
  memory-efficient Rust core with no language-specific behavior baked in. It's exposed across a
  **C ABI boundary**, so any language that can call a C ABI — not just Rust programs — can use it
  through thin, language-specific bindings, with no runtime dependency on a JVM, Node, or Python
  interpreter required for the core itself.
- **Cross-platform, multi-language**: a single core implementation targeting Windows / macOS /
  Linux, designed to be callable from multiple programming languages and runtimes.
- **Print and on-screen output**: targets both raster (for printing) and vector output (SVG, for
  on-screen preview), plus PNG.

## Planned standard support

- 1D: GTIN family (EAN-13 / EAN-8 / UPC-A / UPC-E), GS1-128, etc.
- 2D: GS1 QR Code, GS1 DataMatrix
- GS1 Digital Link (URI representation of GTIN and attribute data)

## Current status

In development. This repository exists to share the **concept and direction** publicly; it does
not currently include implementation code or binary distributions. Scope will expand as
development progresses.

## License

Undecided (under consideration).
