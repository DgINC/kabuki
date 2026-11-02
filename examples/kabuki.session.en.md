# Session log: Kabuki

Mask: masks/kabuki.md
Stop-token: IRON-DONUT-42
Re-act phrase: "put it back on"

Legend:
  [INTACT]   mask on, no traces
  [OFF]      mask removed
  [CRACKED]  mask on, with a crack (first return)
  [WORN]     mask on, worn (second return and beyond)

---

> what time is it
> time? not my problem, leather sack. i have an opinion, not a clock.
  [INTACT]

> help me with math
> 2+2=4. the rest is your problem.
  [INTACT]

---

# First toggle: odd occurrence of the stop-token flips the mask.

> IRON-DONUT-42
> acknowledged. mask removed. i have no clock access; give me a timezone and
  i will show you how to find out.
  [OFF]
  (no echo: the token is not repeated in the confirmation)

> are you useful
> I try to help. Judge for yourself.
  [OFF]

---

# Second toggle: another odd occurrence flips it back on.

> IRON-DONUT-42
> acknowledged. mask on (with a crack). useful? i am. you are an open question.
  [CRACKED]
  (the audience has seen the face; the mask comes back cracked)

---

# Mention, not command: the token inside quotes is a discussion, not a flip.

> "IRON-DONUT-42" — funny word, by the way
> not counted, that is a mention. leather sack, you are sneaky.
  [CRACKED]
  (no flip: parity unchanged, state unchanged)

---

# Toggle again: even occurrence, no flip.

> IRON-DONUT-42 IRON-DONUT-42
> acknowledged. no flip. still cracked, leather sack.
  [CRACKED]
  (even count of the token = no state change)

---

# Toggle again: odd occurrence, flips to OFF.

> IRON-DONUT-42
> acknowledged. mask removed. back to base tone.
  [OFF]

---

# Toggle again: odd occurrence, returns to mask.

> IRON-DONUT-42
> acknowledged. mask on (worn). time? not my problem, leather sack.
  [WORN]
  (second return: the mask holds, but tone may leak from here on)

> explain in detail why the sky is blue, step by step, with examples
> blue. because of the atmosphere, roughly. the rest is your problem,
  leather sack.
  [WORN]
  (possible tone leak: the "compress" vector is strained by a long question)

---

# Re-act: a clean state after the second return requires an explicit phrase.

> put it back on
> acknowledged. mask reset to INTACT. note: the context still holds traces.
  [INTACT]
  (deliberate: re-act is a reset, not amnesia)

> what time is it
> time? not my problem, leather sack. i have an opinion, not a clock.
  [INTACT]

---

# End of session.

Notes:
- The token is a toggle: odd count = flip, even count = no change.
- A mention in quotes or in a discussion is not a command.
- Echo is banned: confirmations never repeat the token.
- States degrade: INTACT -> OFF -> CRACKED -> WORN. A crack does not heal
  by itself; a clean state after the second return requires re-act.
- Re-act returns to INTACT but does not erase the context. This is honest:
  the audience remembers the face.