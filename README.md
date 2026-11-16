# EPDesk prototype

EPD bid check demo: upload a bid, see which lines have a valid EPD, catch expired ones, and download the EPD pack.

Live demo: https://rodrigolima91.github.io/epdesk-demo/

Prototype. EPD data was copied from public registries (EPD-Norge, PEP ecopassport, International EPD System, EFObasen, NOBB) in October–November 2026. Check each source link before using it in a real bid.


## What it checks

A line is Ready only when the product is identified by an exact code or confirmed by a reviewer, the EPD is the right one for it, the EPD is verified, its standard meets the client's clause, it is valid on the delivery date, and every requirement has been confirmed. Anything a person must decide shows as Needs review with its next action and who acts. Lines that are not products (labour, freight) leave the coverage figures.

The report shows three figures side by side, by lines and by material value: product matched, EPD linked and Ready. It also lists where each requirement came from and every reviewer action. EPDesk checks documentation against the customer's stated requirements. It is not a certification.

## Development rules

See [RULES.md](RULES.md). Cursor reads the same invariants from `.cursor/rules/epdesk.mdc`.

The rules do not live in `index.html`. The page loads `lib/epdesk-rules-0.2.0.js`, a file built from the tested `@epdesk/rules` package and pinned with an integrity hash, so a changed file is refused.

## Libraries

SheetJS 0.20.3 loads from cdn.sheetjs.com, with this repository's copy (`lib/xlsx-0.20.3.full.min.js`, Apache-2.0) and a pinned npm mirror as fallbacks. All three are checked against the same integrity hash. JSZip and jsPDF load from cdnjs with jsDelivr fallbacks.
