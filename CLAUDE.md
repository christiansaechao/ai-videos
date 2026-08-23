# Production Strategy — Bright Side Shorts

Decisions that are settled. Read this before planning production or spending credits.

## Budget (the binding constraint)

Higgsfield **Plus: 1200 credits/month.** Verified costs via `get_cost` preflight
(preflighting is free — always preflight before generating):

| Config — 10s, 9:16 | Credits | Per Short (2 blocks) |
|---|---|---|
| **Kling 3.0 std, no native audio** | **15** | **30** |
| Kling 3.0 Turbo 720p | 15 | 30 |
| Kling 3.0 std, native audio | 20 | 40 |
| Seedance 2.0 Mini 720p | 25 | 50 |

**Ceiling: 40 Shorts/month.** Growth is production-capped, not idea-capped —
300 scripts is ~10 months of supply, so credits are the constraint, never ideas.

## Posting cadence

**1 Short per day. 30/month = 900 credits. Hold 300 back for re-rolls**
(~20 retries at 15 credits/block). Never plan to spend 100% on first attempts.

Do **not** post 2/day — it burns the month in 20 days and goes dark.

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

- **Model: Kling 3.0**, `mode: std`, `duration: 10`, `aspect_ratio: 9:16`
- **`sound: off`** — the clip file has no audio track; the Kevin VO is laid over
  it in the edit. The published Short is never silent. Native audio costs +5
  credits/block (+10/Short = 10 fewer Shorts a month) and yields a voice and
  ambience that can't match the written script.
- **720p is correct for Shorts.** Spec is 1080x1920 but 720x1280 is within spec
  and not penalized. Motion and legible captions matter more than pixel count.
- **There is no Kling 2.0 on Higgsfield** — only 2.6, 3.0, and 3.0 Turbo.
  Kling 2.6 exposes no resolution parameter at all.
- Voiceover costs are not yet measured.

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
