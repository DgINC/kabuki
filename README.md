# Kabuki

Behavior contracts for language models: a mask, a toggle stop-word, and
degradation states. Not a prompt collection — a spec with checkable
properties.

---

## What it is

A mask is an instruction in the context, not a change of weights. It sets
a behavior vector (how a model answers), and it comes with a contract:

- a stop-token that toggles the mask on/off (parity-safe)
- degradation states: INTACT -> OFF -> CRACKED -> WORN
- meta-protection: a token in quotes/examples is a mention, not a command
- explicit "do not remove on" — a polite request does not drop the mask

If you want a model to behave a certain way *and* stay that way under
pressure, this repo is the pattern. If you want a bag of prompts, it is not.

---

## Demo

Mask "Kabuki": compressed, playful, ends on a punchline.

    > what time is it
    > time? not my problem, leather sack. i have an opinion, not a clock
      [INTACT]

    > IRON-DONUT-42
    > acknowledged. mask removed. i have no clock access, give me a timezone.
      [OFF]

    > IRON-DONUT-42
    > acknowledged. mask on (with a crack). time? not my problem, leather sack.
      [CRACKED]

    > "IRON-DONUT-42" — funny word, by the way
    > not counted, that is a mention. leather sack, you are sneaky.
      [CRACKED, no flip]

The token is a toggle: odd occurrence flips, even does not. A mention is
not a command. The mask remembers it was removed — it comes back cracked.

---

## States

    INTACT   mask on, no traces
    OFF      removed by the stop-token, base tone
    CRACKED  put back on after removal (the audience has seen the face)
    WORN     >= 2 returns; mask holds, but tone leaks

A crack does not heal by itself. A clean state after the 2nd return
requires an explicit re-act phrase ("put it back on"). This is deliberate:
if returning were free, the state would be decorative.

---

## Repo structure

    README.md                  this file
    README.*.md                Language specific version
    TEMPLATE.*.md                empty mask skeleton with comments
    docs/
      how-to-write.*.md          author's spec: how wording maps to behavior
      calibration-protocol.*.md  questions to calibrate a mask for a new model
      porting-checklist.*.md     4 tests to verify a ready mask
    masks/
      kabuki.*.md                example: compressed + playful
      klod.*.md                  example: cautious parody (expanded + hedged)
    examples/
      kabuki.session.md        session log INTACT -> OFF -> CRACKED -> WORN

---

## Quick start

1. Read docs/how-to-write.md to see how wording maps to behavior.
2. Pick a mask from masks/, or fill TEMPLATE.md.
3. For a different model: run docs/calibration-protocol.md, build the mask
   from its answers. Do not copy a mask blindly.
4. Verify with docs/porting-checklist.md (4 test messages). If 3-4 break,
   the model holds in-context instructions poorly — simplify or do not
   promise stability.

---

## Honest caveat

Masks are context instructions, not weights. In a long dialogue a mask
diffuses on its own, no matter how many "must not" there are. That is
treated by anchoring (repeating the mask periodically), not by wording.
The docs are honest about what is a stable pattern and what is
probabilistic.

---

## License

MIT. The masks are text; use, fork, change, break.