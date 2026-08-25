# Production Strategy — Bright Side Shorts

Decisions that are settled. Read this before planning production or spending credits.

## Budget (the binding constraint)

Higgsfield **Plus: 1200 credits/month.** Verified costs via `get_cost` preflight
(preflighting is free — always preflight before generating):

| Config — 10s, 9:16 | Credits | Per Short (2 blocks) |
|---|---|---|
| **Kling 3.0 std, sound on** | **20** | **40** |
| Kling 3.0 std, no audio | 15 | 30 |
| Seedance 2.0 Mini 720p | 25 | 50 |

At 40 credits/Short (2 blocks x 20), **ceiling is 30 Shorts/month** (1200/40). Growth is production-capped, not idea-capped —
300 scripts is ~10 months of supply, so credits are the constraint, never ideas.

## Posting cadence

**1 Short per day.** At 40 credits/Short, 1200 credits = 30 Shorts/month =
exactly one per day with no slack. Any re-roll eats into the month, so keep
prompts tight and preflight. If re-rolls become frequent, the real cadence is
~26-28/day-equivalent — plan around 30 max, not a comfortable 30.

Do **not** post 2/day — the budget cannot sustain it (60 blocks/day would need
2400 credits/month).

**Rotate niches; never the same niche twice in a row.** With 30 niches and no
performance data yet, one Short/day gives each video a clean 24-hour read.
Two same-day uploads compete for the same impressions and make it impossible to
tell whether the niche, the hook, or surfacing order drove the result.

After ~4 weeks, weight production toward the niches that pop instead of
spreading evenly.

Rationale: current guidance is that consistency beats raw volume — regular
schedules earn higher initial test audiences. Shorts recommendations run
independently from long-form, so there is no cannibalization risk.

## Generation settings

**Each Short = two separate 10s clips (block 1 HOOK, block 2 PAYOFF),
generated individually. The two clips are combined into the final 20s Short
in an external video editor — NOT stitched inside Higgsfield.** This is the
settled pipeline: Higgsfield only produces the two raw blocks; assembly,
captions, and any music happen in the editor.

Per block:
- **Model: Kling 3.0**, `mode: std`, `duration: 10`, `aspect_ratio: 9:16`
- **`sound: on`** — narration is generated together with the video in the same
  Kling call (pass the block's narration line inside the prompt). One file per
  block, audio baked in, nothing to layer. Cost: 20 credits/block = 40/Short.
- **720p equivalent is fine for Shorts.** Spec is 1080x1920 but lower is within
  spec and not penalized. Motion and legible captions matter more than pixels.

Do NOT request a single 20s clip from Kling 3.0 — it silently clamps to 15s
(hard max). The 2x10s split avoids that ceiling entirely.

### Captions — burned in Higgsfield, not CapCut

Use Higgsfield's **`subtitles` workflow** (get_workflow_instructions with
`{workflow: "subtitles"}`) to burn on-screen captions. It Whisper-times the
clip's own baked-in narration, burns the text into the pixels, and returns a new
mp4. This replaces CapCut auto-captions (which are paywalled behind Pro).

- **Font: Anton** — `bold --font-key anton`. This is exactly the "burned Anton
  captions" the script spec calls for; it's a confirmed available font.
- **Always pass `--script`** with that block's exact HOOK or PAYOFF line. Whisper
  then supplies only the timing; the displayed words come from the script, so
  numbers and wording render the way we wrote them instead of however Whisper
  guessed. (Note: scripts spell numbers out for VO — "one hundred fifty dollars".
  If a caption should read "$150" instead, author a caption-specific line.)
- **Burn per block, before combining.** Each 10s clip carries its own audio, so
  caption each block against its own narration, THEN combine the two captioned
  blocks in CapCut. Concatenation preserves sync — no round-trip needed.
- **Cost:** subtitles is a sandbox operation, NOT a generate_* call, so it is not
  the 20-credit video charge — billed "as usual" for assembly. Actual per-run
  cost not yet confirmed; check before leaning on it at volume.

Pipeline per block: generate (Kling, sound on) -> burn Anton captions
(subtitles workflow) -> hand the captioned block to CapCut for final combine.

Notes:
- **There is no Kling 2.0 on Higgsfield** — only 2.6, 3.0, 3.0 Turbo. Kling 2.6
  exposes no resolution parameter.
- Standalone TTS (seed_audio) is 0.7 credits/line if a separate VO is ever
  wanted, but the current pipeline bakes audio into the video instead.

## Script format

Every Short = **2 blocks x 10s = 20s.** Kevin VO, burned Anton captions, 9:16.
HOOK = block 1 (stop the scroll in 3s). PAYOFF = block 2, always ends on a CTA.
`(visual: ...)` = shot cue. Numbers spelled out for voicing.

Note: `scripts/bright-side/mobile-detailing-5min-blocks.md` names Seedance 2.0,
16:9, narrator "Leo" — that predates these decisions. 9:16 and Kling 3.0 win.

## Two-track production (Higgsfield + local ComfyUI)

**Track 1 — Higgsfield, the main line.** Everything above this section: 30
Shorts/month, 40 credits each, the settled generation settings, the schedule
in `SEPTEMBER-2026-SCHEDULE.md`. This is the primary, funded pipeline and
stays exactly as documented above.

**Track 2 — local ComfyUI, a second pipeline run in parallel, not a
replacement.** Run at night on existing local hardware (16GB-class card).
Config/endpoint swap on an already-built ComfyUI setup, not new
infrastructure — so this is not gated on finishing the September pilot.

Local pipeline shape:
1. **LLM** — script + scene beats, same source scripts as Higgsfield
   (`scripts/bright-side/side-hustle-300-shorts.md`), broken into ~4-5 beats
2. **TTS** — Kokoro or XTTS-v2, local, one consistent voice per video (voice
   CAN vary Short-to-Short — see below — but must stay fixed within one video)
3. **Video gen per beat** — LTX-Video or Wan I2V, ~4-5s per clip, 4-5 clips
   stitched per Short. Continuous 15-20s coherent generation is not realistic
   on consumer VRAM; stitching on scene changes is the correct approach and
   matches this channel's own documented cadence (see below).
4. **Assembly** — ffmpeg concatenates clips + overlays narration; Whisper
   generates caption timing. Whisper is timing ONLY — feed it the actual
   script line as ground truth text (same principle as the Higgsfield
   `subtitles` workflow's `--script` flag) so numbers and wording render as
   written instead of however Whisper transcribes them.

### Decisions specific to the local track

- **Narrator voice does not need to match Higgsfield's (Grady) or stay
  consistent across videos.** Shorts compete on their own hook in the feed,
  not on returning-viewer brand recognition — voice identity is not a growth
  lever here. A voice that changes Short-to-Short is fine, even a novelty.
  The one hard rule: voice must NOT change **within** a single video — that
  reads as a broken pipeline, not a bit.
- **Visual cadence: change the shot every 3-6 seconds.** This is not a new
  rule invented for the local track — it is the original documented pattern
  from `analysis/brightside-channel-analysis.md` ("visual changes every 3-6
  seconds"), and 4-5 clips x 4-5s across a 20s Short lands inside it.
- **B-roll over literal depiction, on both tracks.** Generic satisfying
  motion/atmosphere b-roll reads better than AI trying to depict a specific
  concept literally. This is the same failure mode already seen on the
  Higgsfield track (invoice lines, calendars, contract signing, chart
  overlays are the clips most likely to misfire) — apply "motion over
  graphics" to prompts on both tracks, not just the local one.
- **Local output does not count against the 1200 Higgsfield credit budget.**
  It is a separate, parallel supply of Shorts with no premium generation
  cost beyond local compute/time.

## Scope

Bright Side is the main line. The Rocco / Buck / Murph character scripts
(`scripts/characters/`) are a separate lane — **exclude them from Bright Side
work unless asked.** ShowTheReceipts is a different product entirely and lives
on branch `claude/showthereceipts-overview-krj50d`.
