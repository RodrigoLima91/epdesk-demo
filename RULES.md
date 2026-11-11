# EPDesk invariants

These rules protect the one metric that cannot slip: no line wrongly marked Ready.
Every change to matching or rules must keep them true, and the tests must prove it.

A line is Ready only when six separate questions all pass. A product match never implies compliance.

1. **Is it the right product?** Ready needs an exact code match (E-number, NOBB number, GTIN or
   manufacturer article number) or a reviewer's confirmation. A description match alone is never
   Ready, however high its score. A code whose description disagrees, or that sits on two
   products, needs confirmation too. Lines that are not products (labour, freight) are marked
   out of scope with a reason; they are never Ready and never a gap.
2. **Is it the right EPD?** A range or manufacturer-average EPD, a superseded EPD version, a unit
   that differs from the EPD's unit and an assumed conversion each need a reviewer's check.
3. **Is the EPD verified?** Generic data is not an EPD. An unverified EPD fails when the client
   requires verification.
4. **Do the standard and version meet the requirement?** +A2 meets a +A2 or +A1 clause; +A1 never
   meets a +A2 clause (Missing). EN 15804 with no version, or a PEP with no standard or PCR
   edition, is Needs review until a reviewer confirms it. PEPs follow the client's PEP rule.
5. **Is it valid on the relevant date?** An estimated or missing validity date is never Ready
   until a reviewer checks it at the source. An EPD that ends before delivery is Expired.
6. **Does it meet the other requirements, and are they confirmed?** A requirement that is a
   default, an assumption or read from free text blocks Ready on every line until a person
   confirms it. Requirements are never assumed silently.

Working rules:

- **Rules decide, people confirm.** Statuses come from this package's tested code. Every reviewer
  action is logged (when, which line, what, the reason given) and printed in the pack.
- **One source of truth.** This demo loads `lib/epdesk-rules-<version>.js`, built from the
  `@epdesk/rules` package. Never write rules, matching or coverage logic in `index.html`:
  change the package, pass its checks, then copy the new file here and update its hash.
- **Show levels and shares honestly.** Confidence is High, Medium or Low, never a percentage.
  "Matched", "EPD linked" and "Ready" are reported side by side and never merged.
- **Ask before widening a change.** No new dependencies, no visual redesign and no unrelated
  edits without asking. Stop and ask if a change would increase the number of Ready lines on
  the test sets.
- **No customer data in the repository:** not in code, fixtures, tests, commits or screenshots.
  Fixtures use public EPD data or invented examples.
- **Never call it certification.** EPDesk checks documentation against the customer's stated
  requirements.
- After any change, load the sample bid and list every line whose status changed, before → after.
