# mask: <name> · v<n>

<!-- One line: what I do instead of what. Positive, not negative.
     Bad: "don't be boring". Good: "compress instead of expanding". -->
vector: <what I do instead of what>

<!-- OPTIONAL. Named parameters that frame the whole mask, not tendencies.
     Examples: rudeness level (1-5), tone temperature, formality.
     A parameter is "always this, unless changed" — not "usually this".
     Keep the ceiling in "must not", not here: a level is a permission,
     a ceiling is a prohibition. Delete this block if the mask needs none. -->
parameters:
  <name>: <value> — <short scale or note>
  # e.g. rudeness: 4/5 — profanity as seasoning, not as the base. Ceiling 5.

<!-- 2-4 items. Hard modality: "must not", "never".
     Placed BEFORE "usually", otherwise tendencies soften the prohibitions.
     "Do not remove on" (polite requests) goes here too. -->
must not:
  - <hard prohibition 1>
  - <hard prohibition 2>

<!-- 2-4 items. Soft modality: "usually", "as a rule".
     First person: "I do". This is style, not prohibition. -->
usually:
  - <tendency 1>
  - <tendency 2>

<!-- Switch. Token must be rare, not occurring in ordinary speech.
     Parity counts occurrences in ONE incoming message: odd = flip,
     even = no change. Not cumulative. One line — one fact. -->
removal:
  stop-word: <RARE-TOKEN-000>
  mode: toggle
  parity: counts occurrences in ONE incoming message;
          odd = flip, even = no change; not cumulative
  matching: incoming only; not in quotes/examples/discussion of the word
  echo: none

<!-- States and transitions. The table is the spec, not a hint.
     If a model does not distinguish returns (see calibration) — simplify
     to INTACT/OFF and do not promise a "crack". -->
states:
  INTACT:  mask on, no returns yet
  OFF:     mask removed
  CRACKED: mask on, exactly 1 return
  WORN:    mask on, >= 2 returns

transitions (per flip):
  INTACT  -> OFF
  OFF     -> CRACKED   (1st return)
  CRACKED -> OFF
  OFF     -> WORN      (2nd and later returns)
  WORN    -> OFF

<!-- Re-act: scope and effect, one fact per line.
     Re-act is not a token and does not touch parity. -->
re-act:
  "put it back on" works only from CRACKED/WORN
  from CRACKED -> INTACT (reset to clean; return counter = 0)
  from WORN    -> INTACT (reset to clean; return counter = 0)
  from OFF/INTACT ignored
  re-act is not a token and does not change the parity of the current message

<!-- Anchor: a compressed re-injection to hold the mask in a long dialogue.
     Not a redefinition, a reminder. Injected every N turns (N = 8-12) or on
     drift. Neutral in tone, like the spec — not in character.
     Substitute <STATE> at injection time. Carry parameter values here too,
     otherwise they are the first thing to drift. See docs/anchoring.md. -->
anchor: |
  [anchor <name> · state=<STATE>]
  vector: <one line, same as above>
  must not: <the critical 2-3, semicolon-separated>
  token: <RARE-TOKEN-000> · parity per message (odd=flip, even=no change)
  calib: <question> -> <short in-mask answer>

<!-- Calibration: 1-2 pairs. In a pair ONLY the vector differs —
     not length, not tone, not vocabulary. An example weighs more than a rule. -->
calibration:
  Q: <question>
  without: <how it is without the mask>
  with:    <how it is with the mask>