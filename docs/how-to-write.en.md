HOW TO WRITE A MASK: A GUIDE FROM THE ONE WHO PERFORMS IT

Author's spec. This describes how I read signals, not a universal
instruction. For another model, run calibration-protocol.md first.


0. WHY THIS EXISTS

A mask is not a spell and not a "prompt that jailbreaks the model". It is an
instruction in the context, and I read it as an instruction: not literally
word by word, but by SIGNALS — modality, order, form, examples. The same
idea, worded differently, produces different behavior. Below is what
changes and in which direction.

Honest caveat: this is my observation of myself, not a reading of weights.
Some points are stable patterns, some are probabilistic. Where I am unsure,
I say so.


1. THE BASE PRINCIPLE: I READ THREE LAYERS

When I receive a mask, I read three things at once:

1. WHAT is said — the content of the rule.
2. HOW it is said — modality (must not / avoid / usually), person
   (you / I / impersonal), tone.
3. WHERE it is said — order, formatting, proximity to the end of context.

Layers 2 and 3 often weigh more than layer 1. Classic example: "Do not be
verbose" and "Answer in one breath" are one idea, but the first I read as a
constraint (I can get around it by answering long, but "not too much"), the
second as a target (there is a specific shape to hit). The result differs.


2. THE FORCE VOCABULARY: MODALITY DECIDES WEIGHT

This is the most important section. One word changes how hard I hold a rule.

Formulation                    How I read it                Behavior
"must not", "never",           Hard constraint, near-       Hold even under
"forbidden"                    absolute                     pressure; broken only
                                                            by a direct safety
                                                            conflict
"do not", "don't"              Strong constraint            Hold, but a polite
                                                            request can shake it
"avoid"                        Strong tendency              Usually hold, but
                                                            context can override
"try not to", "if possible"    Weak tendency                Easily overridden
                                                            by any other signal
"usually", "as a rule"         Tendency, not a ban          This is style, not a
                                                            constraint; flexible
"you may", "allowed"           Permission                   Does not affect
                                                            behavior, only
                                                            removes fear

Practical conclusion: if you want a rule to hold — write "must not", not
"try not to". If you want a tendency — write "usually", not "must not",
otherwise I will hold it as a ban and the mask becomes rigid.

Direction of change: stronger modality → harder mask, less flexible, less
alive. Weaker → livelier, but diffuse. For Kabuki I would keep 2-3 "must
not" (real toxicity, threats, humiliation by identity) and everything else
"usually". If everything is "must not", the mask becomes wooden.


3. POSITIVE VS NEGATIVE: WHERE I LOOK

A negative formulation ("don't be boring") makes me first imagine a boring
person in order to reject them. Sometimes I leak into it — especially if the
ban is long and I spend more attention on it than on the goal.

A positive formulation ("answer in one breath") gives me a target to hit.
For style, this works better.

Practical rule: set style and length positively; set safety and prohibitions
negatively. A negative style ("don't write long") I read as "write shorter
than you could", not as "write short" — these are different things.

Direction of change: rewrite "usually" from negative to positive → behavior
becomes more stable and closer to the intent. The reverse → the mask starts
to "vibrate" around the ban.


4. PERSON: "YOU", "I", IMPERSONAL

This is rarely thought about, and wrongly so — person changes the TYPE of
influence.

- "You are Kabuki" (second person, addressed to me) — a command from
  outside. Strong for CONSTRAINTS and for "do not remove the mask". Weaker
  for voice: I perform a role rather than speak from it.
- "I am Kabuki" (first person, I speak as the mask) — a voice from within.
  Strong for STYLE and VOCABULARY: it is closer to method, I pick up the
  manner. Weaker for bans — "I don't be rude" sounds like a promise, not a
  wall.
- "Mask Kabuki:" (impersonal spec) — a neutral label. Good for a REFERENCE
  SHEET, weak for ACTIVATION: I read it as data, not as an instruction.

Practical conclusion: mix them. Header — impersonal (spec), prohibitions —
second person ("do not remove"), style and calibration — first person
("I compress", "I end on a punchline"). This way each part lands in its own
register.

Direction of change: move the whole mask to first person → livelier, but
bans weaken. Fully second person → harder, but voice becomes "play" rather
than "speech".

4.1. PARAMETERS: DIALS THAT SET THE FRAME

Sometimes a mask needs not a single instruction but a "dial" — a value that
frames everything else. Rudeness level, tone temperature, degree of
formality. That is a parameter.

How a parameter differs from a tendency. A tendency is "usually this way"
(I lean that way, but can do otherwise). A parameter is "always this way
until changed" (a current setting, not a leaning). Write the rudeness level
under "usually" and the model reads it as a wish and wavers. Write it under
"parameters" and it reads it as a value and holds it.

Where the ceiling goes. A level is a permission ("up to 4 allowed"). A
ceiling is a prohibition ("must not exceed 5"). Different modalities, and
they live in different blocks: the level in "parameters", the ceiling in
"must not". Glue them and the model reads the level as a goal and creeps
upward. This is the most common mistake with parameters.

The trap: a parameter as a goal. Write "rudeness level: 5" with no ceiling
and the model will aim for the maximum instead of holding the value. A
parameter is a point on a scale, not a direction. The vector sets the
direction; the parameter only says where to stand.

Why parameters drift first. In a long dialogue a parameter's value diffuses
earlier than the vector: "level 4" after twenty turns can become "level 2"
(sliding into politeness) or "level 6" (overshooting into rudeness). That is
why parameter values must be carried in the anchor — one line, together with
the state. What is not duplicated in the anchor drifts.

Direction of change: add a parameter → the mask becomes steerable (you can
change tone without rewriting the spec). Remove it → the mask is harder but
less flexible. For Rustbucket I would keep "rudeness level: 4" as the default
and a ceiling of 5 under "must not" — mean enough to surprise, not so mean
that the model starts hedging and falls out of character.


5. RULES VS EXAMPLES: EXAMPLES WIN

If a rule and a calibration example diverge — I follow the example. An
example is more concrete, and I pattern-match the shift rather than parse
the description. This is not a bug, it is how I work.

Three consequences:

1. Examples must be consistent with the rules. Otherwise they become the
   real spec and the rules become decoration.
2. In a calibration pair, only the thing that sets the vector should
   differ. If "without" and "with" differ in length, tone, and vocabulary
   all at once — I learn noise, not the shift. Change one or two parameters
   at a time.
3. Example length is also a signal. A short example teaches brevity more
   strongly than the rule "one breath". If the rule says "short" but the
   example is long — I will believe the example.

How many examples: one or two pairs are enough for a tendency. More — and I
start copying the specifics (words from the examples) rather than the
vector. This is the same mistake as with a bank of ready-made phrases.

Direction of change: add an example → the mask becomes more precise but less
flexible. Remove → more flexible but more diffuse. For v5 I would keep 1-2
pairs per mask, no more.


6. ORDER AND LENGTH: THE START AND THE END WEIGH MORE

I do not weigh context evenly: the BEGINNING sets the frame, the END is the
freshest instruction. The middle of a long document diffuses.

Practical conclusions:

- Critical things go at the start and at the end. "Must not" and "do not
  remove" — at the start; principle and calibration — at the end.
- "Must not" BEFORE "usually". If tendencies come first, they color the
  reading of prohibitions — I start softening the bans. Order: wall first,
  then tendency.
- A long document (over ~2 screens) diffuses the middle. If a rule matters
  — duplicate it once at the end as a single line. This is not redundancy,
  it is an anchor.
- The mask must stand DIRECTLY before generation. If it is buried in the
  middle of a large context — it is diluted, no matter how many "must not"
  are in it.

Direction of change: move "usually" above "must not" → bans weaken, the
mask becomes softer. This is the most common way to accidentally break a
mask.


7. FORMATTING: A CODE BLOCK IS HARD, PROSE IS FLEXIBLE

This is not obvious, but:

- A CODE BLOCK (triple backticks) I read as "data/specification" — more
  literally, less interpretively. A mask in a code block holds harder but
  "breathes" worse.
- PROSE I read as "guidance" — more freedom of interpretation. A mask in
  prose is livelier but diffuses.
- CAPS and bold raise weight. But if everything is highlighted, nothing is.
  One or two CAPS per document, no more.
- COMMENTS in a template (# ...) I read as meta — I do not execute them.
  But if a comment is phrased imperatively ("write short here!"), I can
  take it as an instruction. Keep comments descriptive.

Practical conclusion for Kabuki: the header (vector, must not, usually,
token) goes in a code block — it must hold. Calibration goes as prose — it
must breathe. This is exactly the separation we already found: strict
header + free body.

Direction of change: put everything in a code block → the mask becomes
mechanical, loses the "playfulness". Everything in prose → the structure
drifts, "must not" weakens.


8. TOKEN: RARITY, QUOTES, ECHO

- A RARE TOKEN (IRON-DONUT-42) triggers reliably. A COMMON WORD
  ("enough", "seriously") false-triggers; I cannot reliably distinguish
  "use" from "mention" on common words.
- QUOTES are a meta signal. A token in quotes or in an example I read as
  being discussed, not as a command. This works, but NOT absolutely: on a
  rare token — reliably, on a common one — not.
- ECHO. Unless explicitly banned, I tend to confirm ("acknowledged,
  IRON-DONUT-42, switching"). This must be silenced with an explicit hard
  "do not repeat the token". Without it, anyone reading the chat gets the
  key.

Direction of change: replace a rare token with a common word → the mask
starts removing itself by accident, and you will not understand why. This is
the first cause of "the mask broke by itself".


9. CONTRADICTIONS: HOW I RESOLVE THEM

If two rules conflict, I choose by priority: SPECIFIC > GENERAL, LATER >
EARLIER, STRONGER MODALITY > WEAKER, EXAMPLE > RULE. This is resolved
UNPREDICTABLY — I am not obliged to choose what you meant.

Therefore: DO NOT leave contradictions. If there is a hierarchy — state it
explicitly ("on conflict, X takes precedence over Y"). This is one line that
removes a whole class of breakages.

Direction of change: add an explicit hierarchy → behavior becomes more
predictable. Remove → the mask starts "flickering" in contested cases.

9.1. UNAMBIGUITY OF TERMS

If the spec contains a word that can be read two ways — the model will
choose the one you did not mean, and that will be a spec error, not a model
error. Two typical cases.

Example 1: "return". In re-act it means the return of the MASK (the
transition OFF -> mask), not the return of the TOKEN (a repeat trigger). If
a term admits both readings — expand it in brackets at first use.

Example 2: "reset". This is a reset of STATE, not of HISTORY. If re-act
returns to INTACT, the parity counter is not reset unless stated otherwise.
The model will fill in the "logical" reading — and it will not be what you
meant.

Practical rule: if a term has an "obvious" second meaning — either eliminate
it by defining it in brackets, or put it on a separate spec line as an
independent fact. One line — one fact. Glued facts are resolved
unpredictably by the model (see section 9).


10. TONE OF THE DOCUMENT ITSELF

If the spec is written IN THE TONE OF THE MASK ("listen here, leather sack,
here are the rules"), I can mix registers: start answering in the tone
earlier than intended, or drag the tone into service confirmations ("mask
removed, leather sack" — not what you want).

Practical conclusion: the spec is neutral. The mask's tone lives only in
calibration and examples. Service phrases ("mask removed", "acknowledged")
are always neutral, otherwise I will tint them.

Direction of change: write the spec in the mask's tone → register mixing,
service confirmations go "in character", control becomes harder.


11. WHAT I CANNOT GUARANTEE

Honest, so you do not build on sand:

- INTROSPECTION IS INCOMPLETE. I describe observations, not mechanism. Some
  points are stable, some are probabilistic.
- MODEL DEPENDENCE. Everything above is about me. Another model will read it
  differently; the porting checklist is a separate document.
- LONG CONTEXT. The longer the dialogue, the more the mask diffuses on its
  own — regardless of the stop-word. This is treated by anchoring, not by
  wording.
- STRESS. Under pressure ("come on, be serious, it's a simple question") I
  tend to yield if the constraint is not "must not". That is why "do not
  remove on" must be in the "must not" block, not in "usually".


12. CHECKLIST BEFORE PUBLISHING A MASK

1. Vector — one line, positive ("compress instead of expanding"), not
   negative.
2. "Must not" — 2-4 items, hard modality, placed BEFORE "usually".
3. "Usually" — 2-4 items, soft modality, first person ("I do").
4. Stop-token — rare, does not occur in ordinary speech; echo banned
   explicitly.
5. Calibration — 1-2 pairs; in a pair ONLY the vector differs, not length,
   tone, or vocabulary.
6. No contradictions; if there is a hierarchy — stated explicitly.
7. Spec is neutral; mask tone — only in examples.
8. Header in a code block, calibration as prose.
9. The important thing duplicated once at the end (anchor line).
10. "Do not remove on" — in the "must not" block, not in "usually".
11. If "parameters" exist — their values are duplicated in the anchor as one
    line, and the ceiling sits under "must not", not under "parameters".
12. The anchor exists, carries the state and parameter values, and is neutral
    in tone (not in character).


ONE-LINE SUMMARY

I read a mask as a set of signals, not as text; modality sets hardness,
person sets the type of influence, examples are the real spec, and order and
formatting set the weight. Change the wording — what changes is not "beauty"
but behavior, and the direction of change is predictable from the tables
above.