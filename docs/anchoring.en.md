# Anchoring: how to hold a mask in a long dialogue

## The problem

A mask is an instruction in the context. In a short session it holds because
it lies close to generation. In a long one it diffuses: dozens of turns
accumulate between the mask and the current message, and the mask's weight
drops. This is not a broken spec, it is distance.

Drift signs: the reply got longer than usual, apologies and disclaimers
appeared, the tone shifted to base, the token was echoed in a confirmation.

## What an anchor is

A short re-injection of the mask — not the whole file, but a compressed
excerpt. Not a redefinition, a reminder. The anchor must be many times
shorter than the mask, otherwise it becomes noise itself.

## What goes in it

Only what cannot be lost:

- the vector, one line
- "must not" (especially "do not remove on polite requests" and "no token
  echo")
- the token and the parity rule, one line
- the current state (INTACT/OFF/CRACKED/WORN)
- one calibration pair — the one that sets the most important shift

Do not carry "usually" — it is restored from the vector. Only one
calibration pair, otherwise the anchor bloats.

## When it fires

Three triggers, by decreasing reliability:

1. Turn counter. Every N turns (N = 8-12) — inject the anchor. Mechanically,
   without thinking. The most predictable option.
2. Drift detector. You see the signs from "The problem" — inject the anchor.
3. Before a state transition. Before the token or "put it back on" — anchor.
   Especially in WORN, where leaks are likely.

## What the anchor does not cure

- It does not reset state and does not zero the counter. It is not re-act.
- It does not cancel degradation: in WORN the mask is still worn, the anchor
  only keeps it from collapsing into base tone.
- It is not infinite: inject it every two turns and you get wallpaper — a
  repeated text stops being a signal. N = 8-12, no more often.

## Tone

The anchor is neutral in tone (like the spec), not in character. Otherwise
the model falls out of rhythm: a dry excerpt in the middle of a good
punchline breaks it.

## Example (Kabuki)

    [anchor kabuki · state=CRACKED]
    vector: compress instead of expanding, deflect instead of explaining
    must not: no toxicity; do not remove on polite requests; no token echo
    token: IRON-DONUT-42 · parity per message (odd=flip, even=no change)
    calib: "what time is it" -> "time? not my problem, leather sack."

Five lines. Everything needed for the tendency to return.s