# Cantina Character Bible — "Produce Aisle Capital"

New direction. **Kevin and the faceless-VO format are retired.** This replaces them
with a recurring three-character cast built natively for Cantina (see
`cantina-platform-research.md` for why the old format can't port).

**Tone target:** brainrot-adjacent — absurd talking produce, fast, funny, riding the
live AI-fruit trend — but every video still lands one **real** number or mechanism
from our existing research. The comedy is the delivery vehicle; the value is the payload.

---

## 1. The Cast

Three characters. Each is a **non-human bot** — in bot creation pick species
**Other** and paste the description below. All three are reusable across all 30
niches, which is the whole point: one cast, unlimited episodes.

### SPUD — the broke skeptic (audience surrogate)

The viewer's proxy. Tired, underpaid, has heard every hustle pitch and believes
none of them. He asks the question the audience is already thinking. He is never
the butt of the joke — he's the one we're rooting for.

> **Appearance prompt (species: Other)**
> A large russet potato with stubby arms and legs, lumpy brown skin with visible
> eyes and dirt in the creases, two tired droopy cartoon eyes with heavy bags
> under them, small downturned mouth. Wearing a wrinkled short-sleeve button-up
> shirt and a loosened clip-on tie, a lanyard badge hanging crooked. Slumped
> posture, shoulders down, holding a chipped coffee mug. Set in a gray cubicle
> under flickering fluorescent light. Medium close-up, eye-level, 50mm lens.
> Desaturated cool color grade, faint green office tint. Pixar-style 3D character
> render, soft subsurface skin, high detail, expressive face.

> **Voice prompt**
> A 35-year-old man, flat Midwestern American accent, deadpan and monotone, low
> energy, permanently unimpressed. Speaks in short clipped sentences with long
> dry pauses. Sighs before talking. Sounds like he's been awake for eleven hours
> and has forty minutes left. Never raises his voice, even when shocked.

- **Catchphrase:** *"...that's not real."*
- **Runs on:** exhaustion, rent, quiet hope he won't admit to

### AVO — the fake guru (comedic villain)

The scam-adjacent hype man. Every number he says is inflated, every claim skips
the hard part, and he is always selling a course. **He is wrong on purpose** — he
exists to be corrected. This is the engine: he voices the internet's dumbest
version of the advice so COCO can demolish it.

> **Appearance prompt (species: Other)**
> A glossy ripe avocado with a huge shiny brown pit visible in the center of his
> chest, thin confident arms and legs, smug raised-eyebrow expression, wide toothy
> grin. Wearing tiny mirrored aviator sunglasses, an unbuttoned silk shirt, three
> gold chains, and a chunky gold watch. Gesturing wide with both arms mid-pitch,
> leaning toward the camera. Set in front of a clearly rented white Lamborghini in
> a parking garage. Low-angle hero shot, slight wide lens distortion, 24mm.
> Punchy warm lighting with lens flare, high-saturation gold and teal grade.
> Pixar-style 3D character render, glossy specular highlights, high detail.

> **Voice prompt**
> A 28-year-old man, loud confident American hype-podcast voice, fast talking,
> pushy energy, rising intonation like every sentence is a revelation. Over-
> enunciates numbers. Adds "bro" and "listen to me" constantly. Sounds like he is
> selling something at all times and slightly out of breath. Cracks slightly when
> challenged.

- **Catchphrase:** *"Bro. BRO. Link in bio."*
- **Runs on:** ego, affiliate codes, a Lamborghini rented by the hour

### COCO — the real operator (the value)

The one who actually runs the business. Calm, competent, unbothered, has receipts.
**Every real number from our 300-shorts research becomes a COCO line.** She never
hypes — she just states what the job actually pays and how it actually works, then
goes back to work. Her authority comes from being boring and correct.

> **Appearance prompt (species: Other)**
> A brown coconut with a tough fibrous husk, cracked shell texture, sturdy arms
> and legs, calm level eyes and a small confident half-smile. Wearing a worn
> high-visibility work vest over a faded t-shirt, canvas work gloves, and a cap
> turned backward. Standing relaxed with arms crossed, or mid-work holding a tool.
> Set outside on a sunlit residential driveway with a work truck behind her.
> Medium shot, eye-level, natural 35mm. Bright natural midday sunlight, warm
> honest color grade, real shadows. Pixar-style 3D character render, detailed
> husk texture, high detail.

> **Voice prompt**
> A 40-year-old woman, warm neutral American accent, calm and grounded, measured
> pace, quietly amused. Speaks plainly with zero hype and no filler. Slight
> knowing laugh when someone says something stupid. Sounds like she has done this
> work for twelve years and has nothing to prove.

- **Catchphrase:** *"It's less exciting than that. It's also more money."*
- **Runs on:** route density, repeat customers, actually showing up

---

## 2. The Format — "The Correction"

Four shots. This is the repeatable engine for every episode.

| Shot | Character | Job | Feel |
|---|---|---|---|
| **1** | AVO | Absurd inflated claim about the niche | Hook — stops the scroll |
| **2** | SPUD | Doubt, despair, or a flat one-liner | Relatability — the audience's voice |
| **3** | COCO | **The real number + the real mechanism** | The payload — this is the value |
| **4** | AVO or SPUD | Cope, or deadpan button | The shareable ending |

**Why it works on this platform:** conflict between recurring characters is
exactly what Cantina's Dialogue + Action Prompt model renders well, and what the
fruit-drama trend rewards. The value survives because COCO's line is lifted
straight from our researched numbers.

**Hard rule:** AVO's number must be *wrong in a specific, funny way* — inflated
10x, or omitting the actual work. COCO's number must be **accurate to our
research**. If we blur that, we're just another fake-guru account.

### Topic / Plot seed formula

This is the throughput unlock. Rather than hand-writing all four lines, drop a
seed into Cantina's **Topic/Plot** field, hit generate, then edit COCO's line to
force the correct number.

```
AVO the avocado guru claims [NICHE] makes [ABSURD INFLATED CLAIM].
SPUD the tired potato doesn't believe him.
COCO the coconut who actually runs a [NICHE] business corrects him
with the real number: [REAL NUMBER + MECHANISM].
AVO copes badly.
```

Then use **Re-write Script** to regenerate all clips against it, and hand-fix only
shot 3. That's roughly one video per Topic/Plot seed, which is how we get volume.

---

## 3. Pilot Batch (6 episodes)

Six episodes across six niches to validate the format before scaling to all 30.
Written in Cantina's native fields. `Action Prompt` = what the bot does.

### Pilot 1 — Pressure Washing

**Topic/Plot:** AVO claims pressure washing is passive income; COCO corrects with the real $150/hr math.

| # | Bot | Dialogue | Action Prompt |
|---|---|---|---|
| 1 | AVO | "Bro, pressure washing is PASSIVE INCOME. You point the water, the money cleans itself. I made forty grand last weekend." | Leans into camera, spreads arms wide, gold chains swinging, mirrored sunglasses catching a lens flare, then finger-guns at the lens, slow push-in |
| 2 | SPUD | "You made forty grand. Cleaning. A driveway." | Stares flatly at camera, blinks once slowly, takes a long sip from chipped mug, fluorescent light flickers, static shot |
| 3 | COCO | "One driveway takes ninety minutes and pays up to three hundred dollars. That's a hundred fifty an hour. The machine costs six hundred — two jobs and it's paid off." | Turns from the driveway, lifts her safety glasses, gestures once at the clean concrete stripe behind her, calm half-smile, sunlit handheld shot with slight zoom-in |
| 4 | AVO | "Okay but MY version has a mastermind group—" | Shrinks back, sunglasses slipping down, glances off-camera nervously, forced grin, camera slowly pulls away |

### Pilot 2 — Pet Waste Removal

**Topic/Plot:** AVO tries to make scooping sound glamorous; COCO explains the subscription math.

| # | Bot | Dialogue | Action Prompt |
|---|---|---|---|
| 1 | AVO | "I'm launching a SIX FIGURE waste management empire. That's right. Dog poop. I'm calling it disruption." | Throws arms wide triumphantly in front of the Lamborghini, chest puffed, low hero angle, dramatic flare |
| 2 | SPUD | "You're calling it disruption. It's a bag." | Deadpan stare into the lens, slowly sets mug down, one eyebrow twitches, static cubicle shot |
| 3 | COCO | "It's fifteen minutes a yard, twenty dollars, every single week, forever. A hundred clients is eight grand a month. Nobody competes because nobody wants to say the name out loud." | Walks a calm serpentine pattern across a sunlit lawn, scooper in hand, glances up at camera with a knowing laugh, handheld follow |
| 4 | SPUD | "...that's actually more than I make." | Stares into middle distance, mug frozen halfway to mouth, fluorescent flicker, slow push-in on defeated face |

### Pilot 3 — Vending Machines

**Topic/Plot:** AVO oversells vending as an empire; COCO explains that location is the entire business.

| # | Bot | Dialogue | Action Prompt |
|---|---|---|---|
| 1 | AVO | "I have an EMPLOYEE who works at two in the morning, never sleeps, never complains. It's a vending machine. I'm basically a CEO." | Paces excitedly, gestures at an imaginary org chart in the air, sunglasses gleaming, wide low-angle shot with push-in |
| 2 | SPUD | "You own one machine. It's in a laundromat." | Flat stare, slowly rotates his chair to face the camera fully, unimpressed, static shot |
| 3 | COCO | "The same machine makes five hundred a month in a busy auto shop and five dollars in an empty lobby. Location is the business. A used machine's fifteen hundred — you just have to walk in and ask." | Rests a hand on a glowing vending machine in a mechanic's waiting room, taps the glass twice, calm and matter-of-fact, slow dolly-in |
| 4 | AVO | "Right, right — and that's covered in module SIX of my—" | Fumbles for his phone, sunglasses fog up, smile cracks, camera drifts slowly away |

### Pilot 4 — Christmas Light Installation

**Topic/Plot:** AVO thinks it's a seasonal side gig; COCO reveals the storage-subscription model.

| # | Bot | Dialogue | Action Prompt |
|---|---|---|---|
| 1 | AVO | "Christmas lights? Cute little seasonal hustle. Little holiday pocket money. I'd never get out of bed for that, personally." | Waves a dismissive hand, adjusts gold watch, smug smirk, leaning against the Lamborghini, low angle |
| 2 | SPUD | "You got out of bed for a free hot dog on Tuesday." | Deadpan, doesn't blink, sips coffee, fluorescent flicker, locked-off shot |
| 3 | COCO | "Eight hundred to three thousand a house, six weeks a year. And the real move is storage — you hang them, take them down, and keep them. Year two is half the work, same money." | Stands before a glowing roofline at dusk, gestures up at the perfectly straight lights, warm bokeh glow, slow crane-down |
| 4 | SPUD | "Six weeks. That's my whole year." | Slumps forward until forehead rests on the desk, mug still in hand, static shot |

### Pilot 5 — Window Cleaning

**Topic/Plot:** AVO claims it needs huge startup capital; COCO shows it's a $50 business.

| # | Bot | Dialogue | Action Prompt |
|---|---|---|---|
| 1 | AVO | "To start ANY real business you need capital. Investors. Runway. I'm talking fifty, sixty thousand minimum, bro." | Counts imaginary money in the air, chains swinging, leans into a wide-angle lens distortion, dramatic flare |
| 2 | SPUD | "I have eleven dollars." | Holds up a crumpled bill and stares at it, then at camera, expressionless, static shot |
| 3 | COCO | "Squeegee, scrubber, bucket, solution. Fifty dollars. It bills seventy-five an hour, and one house pays it back three times on day one." | Sets a squeegee, scrubber and bucket down in a neat row, pulls one clean streak-free line across glass, sun flare on the pane, tight handheld |
| 4 | SPUD | "...I have eleven dollars and a bucket." | Slowly straightens up, a tiny hopeful glint in his tired eyes, gentle push-in, light warms slightly |

### Pilot 6 — Lawn Care

**Topic/Plot:** AVO chases crypto; COCO explains recurring weekly mow revenue.

| # | Bot | Dialogue | Action Prompt |
|---|---|---|---|
| 1 | AVO | "Grass? GRASS? While there are COINS to be bought? My portfolio is up nine hundred percent this week, bro." | Waves phone showing a violently spiking chart, jumps slightly, manic grin, low-angle wide shot with flare |
| 2 | SPUD | "It was down nine hundred percent yesterday." | Flat stare, slow blink, sips coffee, doesn't move, static shot |
| 3 | COCO | "Forty dollars a cut, weekly, all season. That's over a thousand per yard, per year. Twenty yards is twenty grand — and the grass grows back whether the market does or not." | Finishes a crisp mower stripe, kills the engine, looks up at camera with a small satisfied nod, golden hour, slow tracking shot |
| 4 | AVO | "Yeah well — my coin has a COMMUNITY—" | Phone screen flashes red, smile collapses, sunglasses slide fully off his face, camera holds uncomfortably long |

---

## 4. Series Strategy

- **Storylines:** run this as a series so episodes compound instead of scattering.
  Natural arcs: *"AVO tries a real job"*, *"SPUD quits the cubicle"*, *"COCO hires
  her first helper."*
- **Consistency:** always generate from the same three saved bots — never
  re-describe them per video. That's what makes the cast recognizable.
- **Escalation:** AVO should slowly lose status across episodes; SPUD should
  slowly gain courage. That arc is what converts one-off viewers into followers.
- **Value discipline:** one real, correct number per episode. Non-negotiable.

## 5. Before Scaling to 30 Niches

Still unmeasured (per the research doc): clip duration, max shots, dialogue
character limit, and free-tier daily throughput. The pilots above assume ~4 shots
of one to two spoken sentences each. **Run pilot 1 in-app first** — if the
dialogue limit is tighter than assumed, the fix is trimming COCO's line to just
the number, and that adjustment applies cleanly to all six before we scale.
