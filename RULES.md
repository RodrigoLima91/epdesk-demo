# EPDesk invariants

These rules protect the one metric that cannot slip: no line wrongly marked Ready.
Every change to matching or rules must keep them true, and the tests must prove it.

1. **Ready needs proof of the product.** A line is Ready only after an exact code match
   (E-number, NOBB number, GTIN or manufacturer article number) or a reviewer's confirmation.
   A description match alone is never Ready, however high its score.
2. **No guessed dates.** An estimated or missing validity date is never Ready.
   The reviewer must check validity at the source first.
3. **The standard must meet the clause.** The EPD's standard must meet the client's
   required standard (`R.std`).
   - +A2 meets a +A2 or +A1 clause; +A1 never meets a +A2 clause (Missing).
   - An EN 15804 record with no version stated is Needs review until a reviewer confirms it.
   - PEP ecopassports follow the client's PEP rule.
4. **Ask before widening a change.** Do not add dependencies, change the visual design
   or touch unrelated code without asking.
5. **No customer data in the repository.** No customer files, bids or customer data in
   code, fixtures, tests or commits. Fixtures use public EPD data or invented examples.

Also:

- Confidence is shown as High, Medium or Low with its method, never as a percentage.
- The rules in `index.html` mirror the tested `@epdesk/rules` package. Change them there
  first, pass its `npm run check`, then copy the change here.
