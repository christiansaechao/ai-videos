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

## Scope

Bright Side is the main line. The Rocco / Buck / Murph character scripts
(`scripts/characters/`) are a separate lane — **exclude them from Bright Side
work unless asked.** ShowTheReceipts is a different product entirely and lives
on branch `claude/showthereceipts-overview-krj50d`.
