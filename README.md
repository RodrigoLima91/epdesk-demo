# EPDesk prototype

EPD bid check demo: upload a bid, see which lines have a valid EPD, catch expired ones, and download the EPD pack.

Live demo: https://rodrigolima91.github.io/epdesk-demo/

Prototype. EPD data was copied from public registries (EPD-Norge, PEP ecopassport, International EPD System, EFObasen, NOBB) in October–November 2026. Check each source link before using it in a real bid.


## Development rules

See [RULES.md](RULES.md). Cursor reads the same invariants from `.cursor/rules/epdesk.mdc`.

## Libraries

SheetJS 0.20.3 loads from cdn.sheetjs.com, with this repository's copy (`lib/xlsx-0.20.3.full.min.js`, Apache-2.0) and a pinned npm mirror as fallbacks. All three are checked against the same integrity hash, so a changed file is refused. JSZip and jsPDF load from cdnjs with jsDelivr fallbacks.
