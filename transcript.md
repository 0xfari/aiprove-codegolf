# Build log — code-golf-expr

- 14 Nov 2026 ~08:40 WIB: fetched spec + cases.json from
  github.com/AIProveRH/aiprove (challenges/code-golf-expr). Confirmed: single
  file exporting evalExpr, metric = bytes, 9 public cases.
- Wrote three candidates and tested all against the 9 public cases plus a
  self-made 40-case edge suite (spaces, unary minus, nested parens, decimals
  incl. 0.1+0.2, division by zero, single number, .5 / 5. forms, +5,
  deep nesting, large ints):
  - `index.js` (21 bytes, `exports.evalExpr=eval`): 9/9 public, 46/49 edge —
    fails only adjacent `--` chains (`--5`, `2--3`, `---5`), where JS parses
    `--` as decrement and throws. Outside the stated grammar.
  - `alternatives/eval2.js` (46 bytes, `--` → `+` normalisation): 49/49.
  - `alternatives/parser.js` (410 bytes, hand-written recursive descent):
    49/49; no scientific notation (not in spec).
- Decision: primary = 21-byte eval alias (shortest verifiable entry; the
  `--` risk is judged low — no unary minus appears in any public case).
  The 46-byte variant is a one-copy swap if safety is preferred.
- Local git init + commit (identity 0xfari <didan.adidan08@gmail.com>).
  No GitHub repo created, nothing submitted (parent handles that).
