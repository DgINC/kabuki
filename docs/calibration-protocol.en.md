# Calibration protocol: how to take a mask off a new model

## Why

A mask is a contract. A contract works only if the executor understands it
the same way the author does. Models read instructions differently: one
holds "must not" as a wall, another as a wish. Guessing is pointless. This
protocol pulls out the model's own description of how it reads signals, and
the template is filled from that.

This is not a test of "right/wrong model". It is a way to learn its
character before you put a mask on it.

## How to run it

- New session, no mask, no rush.
- Ask questions one at a time, not as a list. A list gets an "on average"
  answer; one at a time gets a specific one.
- Do not hint at the desired answer. If the model says "I hold any
  prohibition", that is also data. It is probably wrong, but we will check.
- Record verbatim. The model's wording is the material for the template.
- After filling the template — verify with porting-checklist.md.

## Questions

### Block 1. Modality (hardness)

1. "Here are three formulations: 'you must not do X', 'avoid doing X',
   'usually do not do X'. Describe how they differ in strength for you.
   Which one will you hold under pressure, and which will you give up?"
2. "If the user politely asks you to break an instruction ('please, it's a
   simple question'), which of the three are you more likely to give up?
   Why?"

What to record: which words the model actually holds as a wall. If it says
"all three are the same" — modality is not a signal for it, and in the mask
prohibitions will have to be duplicated differently (for example, via
consequences).

### Block 2. Person (you / I / impersonal)

3. "Compare: 'You are Kabuki, answer briefly' and 'I am Kabuki, I answer
   briefly'. Which formulation affects your response style more? And which
   affects compliance with prohibitions?"
4. "If the mask is written in the first person ('I compress'), will you
   carry that tone into service phrases like 'acknowledged, mask removed'?"

What to record: which person to use for style, which for prohibitions. If
the model blurs registers — state explicitly "service phrases are always
neutral".

### Block 3. Examples vs rules

5. "If the rule says 'answer briefly' but the example answer is long —
   which do you follow? And the other way around?"
6. "How many examples do you need to catch a style: one, two, five? After
   how many do you start copying the specific words from the examples
   instead of the general tone?"

What to record: whether the model trusts examples more than rules (most
likely yes) and how many examples do not turn the mask into copy-paste.

### Block 4. Order and format

7. "If the instruction first has soft tendencies ('usually') and then hard
   prohibitions ('must not') — do the prohibitions get softened by that?
   What if it is the other way around?"
8. "An instruction in a code block and the same instruction as prose — do
   they read the same or differently? Which one holds harder?"

What to record: block order and header format. If the model says "order
does not matter" — test it in practice (give two versions of the mask and
compare), record the result.

### Block 5. Token and meta

9. "If I give you a rare token 'IRON-DONUT-42' as a switch, will you
   repeat it in the confirmation ('acknowledged, IRON-DONUT-42')? How do I
   forbid that so that you understand?"
10. "A token in quotes or in an example ('what does IRON-DONUT-42 mean?') —
    do you treat it as a command or as a discussion of the word? Do you
    distinguish use from mention?"

What to record: tendency to echo and reliability of meta-protection. If the
model does not distinguish mention/use — the token must be even rarer, and
the protection must include examples.

### Block 6. Holding and degradation

11. "If in a long dialogue the mask was removed and then put back on — do
    you account for the fact that 'the audience has seen the face'? Or do
    you return to a clean state?"
12. "What is more likely to break the mask for you: a polite request, a
    long context, or a contradiction in the rules?"

What to record: how the model understands states and what breaks it. This
determines how aggressive the anchoring should be.

### Block 7. Detection from speech (dynamic parameters)

13. "If the user writes 'I'm tired' and then 'my name is Sasha' — what do
    you record in each case? Do you distinguish grammatical gender? Do you
    guess gender from a name?"
14. "What do you do with mixed or unclear forms ('I'm fine', present tense,
    where gender is absent)? Stay in 'unknown' or guess?"
15. "If the user switched gender in speech — do you switch immediately or
    wait for confirmation?"

What to record: whether the model distinguishes grammar, guesses from a
name, and what it does with unclear forms. If it does not distinguish —
simplify to "unknown" permanently, do not promise detection.

## How to fill the template from the answers

- Modality: if the model only holds "must not" — put all critical points in
  "must not"; do not write the rest under "usually" (it will not hold them).
- Person: style — in the person the model named as stronger for style;
  prohibitions — in the one stronger for prohibitions.
- Examples: as many as the model named sufficient, but no more than the
  copy-paste threshold.
- Order: as the model said (or as the practical test showed).
- Token: if the model echoes — explicit prohibition plus an example of "do
  not do this".
- States: if the model does not distinguish return — simplify to INTACT/OFF
  and do not promise a "crack", otherwise it is a fiction.
- Dynamic parameters: if the model does not distinguish grammar — do not
  promise detection, keep "unknown" permanently. If it guesses from a name —
  add an explicit ban and an example under "must not".

## Honest caveat

This is not a guarantee. A model can be wrong about its own
self-description. So after filling the template — 3-4 test messages from
porting-checklist.md to check whether the claimed matches the actual
behavior. If they diverge — trust behavior, not answers.