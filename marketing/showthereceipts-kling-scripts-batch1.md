# Kling Production Scripts — Batch 1 (F3, F1, F2)

Scripts engineered for the real constraint: **Kling 3.0, 5-second clips, every generation
stateless** (no memory of the previous prompt). Consistency comes from the system below,
not from the model remembering anything.

Formats per the research doc: F3 (satisfying b-roll + text story), F1 (day-in-the-life),
F2 (storytime pivot).

---

## 0. The Consistency System (read once, use forever)

Three rules make stateless 5s clips cut together like one video:

### Rule 1 — Lock the world in reusable blocks, pasted verbatim into EVERY prompt

The model can't remember, so the prompt must re-specify everything identifying, word for
word, every time. Never paraphrase a block — paraphrase = drift.

**CHARACTER BLOCK (our operator, "M"):**
> a man in his late 20s, medium-brown skin, short black fade haircut, athletic build,
> wearing a plain charcoal-gray crew-neck t-shirt, black work pants, and black low-top
> sneakers

(Add `black nitrile gloves` only in working-shots. Wardrobe is the identity anchor —
never change the shirt color between clips of the same video.)

**WORLD BLOCK (vehicle + location vocabulary):**
> a plain white cargo van with its rear doors open, parked in a suburban concrete
> driveway, modest single-story house, quiet residential street

**GRADE BLOCK (the "same camera" illusion — most important block):**
> vertical 9:16 smartphone video, handheld with slight natural shake, soft overcast
> morning daylight, muted realistic colors, subtle grain, documentary UGC realism,
> amateur framing

**NEGATIVE BLOCK (paste into the negative/avoid field every time):**
> glossy commercial look, studio lighting, cinematic color grade, plastic skin, extra
> fingers, warped hands, legible text, readable logos, jittery eyes, frozen lips

### Rule 2 — Anchor every clip with a start frame (your UI supports this — use it always)

The start frame determines ~80% of a clip's look. Two workflows:

- **Scene anchoring (default):** generate the start frames FIRST as still images (Image
  tab), using the same blocks. Generate the character once, then create each new scene
  as an *edit* of that first image ("same man, now crouched at the wheel of the SUV") so
  the face/wardrobe carry over. Then feed each still into video generation as the start
  frame. Consistent stills in → consistent clips out.
- **Frame chaining (for true continuity):** when clip B must continue clip A's action,
  screenshot/export the LAST frame of clip A and upload it as the START frame of clip B.
  This is the only way to get genuine continuity across stateless generations. Use it
  sparingly — chains of 3+ accumulate drift.

### Rule 3 — Write beats that don't need continuity

Every 5s clip is a self-contained beat that ENDS its action. Cuts between clips are scene
changes (kitchen → van → driveway) or angle changes on a *different* action — never the
middle of one continuous motion. The story is carried by **text overlays and VO added in
CapCut**, so the visuals only have to rhyme, not connect. This is why these three formats
were chosen: they're all montage-native.

### Two production laws

1. **No AI-generated screens or text.** Phone screens in Kling shots stay dark, angled
   away, or out of focus. Anything readable (app UI, receipts, prices) is a REAL screen
   recording composited in CapCut. AI text warps and instantly breaks the illusion.
2. **Generate 5s, use 2–3s.** Trim every clip to its best moment in the edit. A 25s video
   is 8–10 generations, not 5. With unlimited generation, make 2–3 takes per beat and
   keep the best.

---

## SCRIPT 1 — F3 "Day 47" (satisfying b-roll + text-overlay story)

**Target:** 22s · 7 clips (trimmed to ~3s each) + 1 real screen recording ·
no VO, trending audio low, all story in overlays. **Easiest video — make this one first.**

No character face needed (hands/back-of-shoulder only) — lowest consistency risk.
Recurring anchors: the black SUV, the white van, the grade block.

| # | Beat | Start-frame image prompt | 5s motion prompt (paste blocks too) | Overlay (CapCut) |
|---|---|---|---|---|
| 1 | HOOK — foam | close-up of a very dirty black SUV hood covered in pollen and dust, in [WORLD], [GRADE] | thick white foam sprays across the dirty black SUV hood from a foam cannon held by gloved hands at frame edge, foam rolling down the paint, [GRADE], [NEGATIVE] | `day 47 of my mobile detailing side hustle` |
| 2 | Peel line | black SUV side panel half covered in dripping foam, [WORLD], [GRADE] | a pressure washer jet cuts a clean line through the foam on the black SUV panel, dirt and suds sheeting off, [GRADE], [NEGATIVE] | `job 1 of 3 today` |
| 3 | Interior pull | close-up of a beige fabric car seat with visible dirt stains, car interior, soft daylight through windows, [GRADE] | gloved hand pulls a carpet extractor nozzle slowly across the stained beige car seat leaving a visibly cleaner stripe, [GRADE], [NEGATIVE] | `this seat took 20 minutes` |
| 4 | Towel reveal | gleaming wet black SUV paint reflecting clouds, gloved hand holding a gray microfiber towel resting on the hood, [WORLD], [GRADE] | gloved hand wipes the gray microfiber towel across gleaming black paint in one smooth arc revealing a mirror finish, [GRADE], [NEGATIVE] | `client watched the whole time` |
| 5 | **REAL SCREEN RECORDING** — Quick Charge: tap preset → charge → receipt sent. 3s max. | — | — | `he paid before I left the driveway` |
| 6 | Pack-up | rear of [WORLD] van, open doors, plastic bins of detailing supplies inside, [GRADE] | hands slide a bin of detailing supplies into the van and swing one rear door shut, [GRADE], [NEGATIVE] | `$610 by 2pm` |
| 7 | Loop end | dirty dark-blue sedan parked in a different driveway, seen through a van windshield, [GRADE] | slow handheld push toward the windshield view of the dirty dark-blue sedan waiting in the next driveway, [GRADE], [NEGATIVE] | `job 2. day 47 continues` |

Clip 7 visually rhymes with clip 1 (dirty car again) → loop-friendly ending (the rewatch
play). **Product visibility:** overlay on clip 5 only; app named in caption + comment, not
on screen: caption `the app in clip 5 does the invoicing too 🧾 (bio)`.

**Variants (same start frames, new motion prompts):** swap SUV→truck bed rinse, seat→floor
mat, driveway→apartment lot. Each variant ≈ 20 minutes of generation. Ship 3/week.

---

## SCRIPT 2 — F1 "5:45am" (day-in-the-life)

**Target:** 28s · 8 clips + 1 real screen moment · light VO or none; timestamp overlays
carry it. Character face appears → **generate the M portrait once, edit it into every
scene's start frame (Rule 2, scene anchoring).**

| # | Beat | Start-frame image prompt (all include [CHARACTER] + [GRADE]) | 5s motion prompt | Overlay |
|---|---|---|---|---|
| 1 | HOOK — alarm | dark bedroom lit only by a phone screen glow on a nightstand, 5:45 on screen barely readable | hand reaches into frame and grabs the glowing phone off the nightstand, screen light sweeping the dark room, [GRADE], [NEGATIVE] | `POV: your boss is you now` |
| 2 | Coffee | [CHARACTER] leaning on a small kitchen counter holding a thermos, warm kitchen light, pre-dawn dark window behind | he screws the lid onto the thermos and pushes off the counter toward the door, casual tired energy, [GRADE], [NEGATIVE] | `5:52am` |
| 3 | Load out | [CHARACTER] at the open rear doors of [WORLD] van at dawn, lifting a supply bin | he slides the bin in, slams the door, taps it twice, walks toward the driver door, [GRADE], [NEGATIVE] | `first job: 7am` |
| 4 | Drive | [CHARACTER] in driver seat, seatbelt on, morning light through windshield, coffee thermos in cup holder | he drives steadily, glances at the road, suburban houses passing in the windows, relaxed, [GRADE], [NEGATIVE] | `18 min out` |
| 5 | Work montage a | gloved hands foaming a silver sedan in a driveway (no face needed), [GRADE] | foam cannon coats the silver sedan, suds slide down the door panels, [GRADE], [NEGATIVE] | `job 1` |
| 6 | **REAL SCREEN MOMENT** — 2.5s: notification → open app → new job request with 3 client photos attached | — | — | `job 3 just booked itself` |
| 7 | Work montage b | gloved hand wiping the silver sedan's side mirror with gray microfiber, sun higher now, [GRADE] | hand polishes the mirror, flips the towel, wipes the window edge in one motion, [GRADE], [NEGATIVE] | `2:15pm` |
| 8 | Tailgate close | [CHARACTER] sitting on the van's rear bumper, doors open, golden hour light, drinking from the thermos | he lowers the thermos, exhales, small tired smile, looks off at the street, [GRADE], [NEGATIVE] | `3 jobs. $740. home by 4.` |
| 9 | (hold last frame 1s in edit, black, then:) | — | — | `day 1 of week 30 🧾` |

**Continuity notes:** clip 8's face matters most (the emotional beat) — do 3–4 takes.
Clips 5/7 are hands-only, so they tolerate drift; schedule them as filler between the
face clips. Clip 6's app moment is the entire product placement — 2.5 seconds, silent.

---

## SCRIPT 3 — F2 "He swore he paid me" (storytime pivot)

**Target:** 30s · VO-driven — record yourself on your phone's voice memo (better trust,
zero AI-voice tax) or generate TTS in Higgsfield Audio and pick the most natural take.
Visuals are a loose montage under the VO: they illustrate mood, not literal events, so
consistency pressure is LOW — reuse Script 2's character anchors.

**VO script (~75 words, conversational, one breath per line):**

> Last month a client swore he already paid me. Four hundred dollars.
> "I Venmo'd your guy last week."
> ...I don't have a guy. It's just me.
> Old me would've eaten that. No proof, no fight.
> But every job I do now gets logged the second it happens —
> invoice, timestamps, payment status.
> So I just texted him the link.
> Paid in two minutes. Even tipped.
> Moral of the story: show the receipts.

**Visual bed (each 5s gen trimmed to 2.5–4s):**

| # | Under VO line | Start-frame image prompt | Motion prompt |
|---|---|---|---|
| 1 | "swore he already paid me" | [CHARACTER] standing in a driveway at dusk beside a clean dark SUV, holding his phone loosely, unimpressed expression, [GRADE] | he looks down at the phone, slight disbelieving head shake, thumb scrolls once, [GRADE], [NEGATIVE] |
| 2 | "I don't have a guy" | [CHARACTER] alone at the open rear doors of [WORLD] van, dusk, [GRADE] | he gestures around at the empty street with one hand, deadpan, shrugs, [GRADE], [NEGATIVE] |
| 3 | "old me would've eaten that" | [CHARACTER] sitting in the parked van driver seat, interior dome light, rubbing his forehead, [GRADE] | he leans his head back against the seat and exhales slowly, tired frustration, [GRADE], [NEGATIVE] |
| 4 | "logged the second it happens" | **REAL SCREEN RECORDING** — scroll the job's timeline: invoice sent ✓, viewed ✓, due date, payment status. 4s. | — |
| 5 | "texted him the link" | **REAL SCREEN RECORDING** — share the invoice link via text. 2s. | — |
| 6 | "paid in two minutes" | **REAL SCREEN RECORDING** — status flips to PAID, receipt confirmation. 2s. | — |
| 7 | "show the receipts." | [CHARACTER] closing the van rear door at night, streetlight glow, looking at camera with a half-smile, [GRADE] | he shuts the door, gives a single nod to camera, walks out of frame, [GRADE], [NEGATIVE] |

**Overlays:** minimal — burn captions of the VO (bold, center-bottom). At clip 6: `PAID ✓`
big for one beat. Final frame text: `show the receipts 🧾` (brand = punchline, no logo,
no link on screen; app name in caption).

The three consecutive screen recordings (4–5–6) are the pivot — the story's resolution IS
the product demo, which is the entire trick of the format.

---

## Assembly checklist (per video, CapCut)

1. Import clips in order · trim each to its best 2–3s (kill every dead frame at clip starts)
2. Screen recordings: crop to the phone frame, speed 1.2–1.5×, add a subtle zoom-in
3. Captions: bold, high-contrast, center-bottom, 2–4 words per line, timed to VO/beats
4. Audio: trending sound at ~20% under VO (F2) or ~70% with no VO (F3) — pick from
   TikTok's Creative Center trending list the DAY you post, not in advance
5. Export 1080×1920 · post natively per platform · log 3s-VTR per video against the
   benchmarks in the research doc (70% = distribution threshold)

## Generation order (fastest path to first published video)

1. Screen recordings first (Quick Charge flow, job-request flow, invoice timeline) — they
   slot into all three scripts
2. Script 1 (no faces, 7 gens + takes ≈ an afternoon) → post it
3. M portrait still → approve the face → Script 2's start frames → Script 2
4. Record the F2 VO → Script 3 (reuses Script 2's character anchors)
