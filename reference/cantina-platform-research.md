# Cantina — Platform Research

Research notes on how [Cantina](https://cantina.com/homefeed) actually works, gathered
before adapting our side-hustle concepts to it. **No scripts yet** — this is the
mechanics-and-constraints pass.

Sources: Cantina Help Center (Video Editor 101, Using Imagine to Create Videos,
Prompting 101, Structure Your Prompt, Starter Prompt Library, Storylines, Creator
Tips), plus third-party coverage of the AI-fruit/brainrot trend.

---

## 1. What Cantina Actually Is

Cantina is **not** a text-to-video prompt box like Kling, Sora, or Higgsfield.
It is a **character-first social platform**. The unit of creation is a **bot**
(a persistent AI character with a look, personality, and voice), and videos are
those bots *performing*. There is also a built-in social feed, so the app is
both the studio and the distribution channel.

This is the single most important finding, and it breaks a core assumption in our
existing library — see §6.

| Element | How Cantina does it |
|---|---|
| **Core object** | Persistent bots/characters, reusable across videos |
| **Video model** | Multi-scene: each scene = one or more bots speaking + acting |
| **Narration** | Character dialogue, not a detached faceless narrator |
| **Distribution** | Native community feed + Storylines; also exports out to TikTok/IG |
| **Cost** | Free tier covers bot creation, images, and short videos |

## 2. The Creation Pipeline

Two entry points lead to the same **Video Editor**:

**A. Imagine tab (the fast path — this is the one for volume)**
1. Imagine tab → tap **Video** at the top.
2. Pick up to **six characters** (search existing bots or create your own).
3. Describe the video: choose a **trending topic**, a **theme**, or write your own.
4. Cantina auto-generates the whole thing — script, images, and action prompts
   across multiple clips.
5. Edit dialogue / action prompts, or delete clips.

**B. Bot profile path**
- Select a bot → **Create Video** under their profile photo.
- Or screenshot a room, or use the blue wand (bottom right) to enter the editor.

**In the Video Editor:**
- **Scene thumbnails row** — tap `+` to add a shot; choose **Character** to set
  which bots appear (`+ Add` for more).
- Each shot has two authoring fields:
  - **Dialogue** — what the bot *says*
  - **Action Prompt** — what the bot *does* (e.g. "the muscular man talks
    animatedly to the camera, leaning back")
- **Topic / Plot** sits at the top of the full script view (**Edit Script**).
- **Re-write Script** regenerates *all* dialogue and action prompts across every
  clip to match a changed Topic/Plot. Individual lines have their own **Rewrite**.

> **Leverage point:** Topic/Plot → auto-generate → targeted edits is the highest-throughput
> loop. We should be authoring *Topic/Plot seeds*, not hand-writing every line.

## 3. Voice Is the Gate

**A bot must have a voice before it can make videos.** Bots without a voice can
only chat. You can create a unique voice or clone one.

Voice direction is prose, not a dropdown — the docs' own example reads:
> "A 25-year-old woman, California accent, bright and casual, upbeat, comfortable
> laughing mid-sentence, speech is loose and natural, lots of 'like' and 'you know,'
> sounds like she's smiling."

Creator Tips stress giving each bot a **distinct** voice — a catchphrase, a lisp,
formal vs. casual — so characters stay recognizable across shots.

## 4. Prompting Model

Cantina's docs are explicit that **prompts should be long, layered, and detailed** —
"that's what it takes to get results that look like the videos you see on your feed."
Terse prompts underperform.

**Prompt layers** (stack them, add until detailed enough):
Subject → Action/pose → Setting → Wardrobe → Camera (shot type, angle, lens) →
Lighting (natural light, time of day) → Color/atmosphere (grade, mood) →
Finish (quality + style cues).

**For video specifically**, add the two time-based layers:
- **Action verbs stacked in sequence** — "walks in, looks up, smiles, turns away"
- **Camera movement** — how the shot evolves ("soft handheld follow with a slight
  zoom-in on the smile")

Available styles include JOJO, Ghibli, Disney, Pixar, and anime-inspired looks.

## 5. Why the Fruit/Brainrot Format Wins Here

The viral AI-fruit format (@ai.cinema021's *Fruit Love Island* did 300M+ views in
nine days) maps perfectly onto Cantina's architecture, which explains why the app
took off on that trend:

- Fruits are **non-human bots** — in bot creation, pick species **Other** and
  describe the look; the app renders whatever you describe.
- They are **recurring characters** → reusable across a whole series.
- The content is **dialogue-driven soap opera** → exactly Dialogue + Action Prompt.
- Serialized drama → **Storylines** (videos as a series of episodes, released as
  chapters, run on your profile or your bot's).

**The engine behind the trend is: persistent absurd characters + escalating
interpersonal conflict + serialization.** Not narration.

## 6. Implications for Our Side-Hustle Library — The Key Conflict

Our existing `scripts/bright-side/side-hustle-300-shorts.md` is built as:

```
HOOK:   [Kevin VO narration]  (visual: b-roll cue)
PAYOFF: [Kevin VO narration]  (visual: b-roll cue)
```

That is **faceless narrator + stock-style b-roll**. Cantina has no real equivalent —
it renders *characters talking*, and voice is attached to bots, not to the project.

So the 300 shorts **cannot be pasted into Cantina as-is**. Adapting requires a
structural conversion, and there are three viable routes:

| Route | Approach | Trade-off |
|---|---|---|
| **A. Cast a host bot** | One recurring "hustle guy" bot delivers our existing HOOK/PAYOFF as dialogue to camera | Closest to current scripts; least native to the feed; talking-head is weaker on the algorithm |
| **B. Two-hander dialogue** | Convert each short into a 2-character exchange — skeptic vs. hustler, broke friend vs. earner | Real conversion work, but conflict is what the format rewards |
| **C. Brainrot-native cast** | Absurd recurring characters (anthropomorphized pressure washer, talking driveway, fruit crew) arguing side-hustle economics | Highest ceiling, rides the live trend, most native — furthest from our current text |

Route B or C is where the platform's grain actually points. Route C plus
**Storylines** would let one recurring cast carry many episodes, which compounds
far better than 300 one-off narrations.

## 7. Confirmed Constraints

- Up to **six characters** per Imagine scene.
- **Multi-scene / multi-clip** per video; add shots freely via the thumbnails row.
- Bot **must have a voice** to generate video.
- Non-human characters supported via species **Other** + description.
- Publish to community feed, Storylines, or **export outside Cantina**.
- Free tier covers bots, images, and short videos without subscription.

## 8. Open Questions (verify in-app — not documented publicly)

These are the gaps that block precise script sizing. Direct doc fetches were
blocked, and none of the below appear in public documentation:

1. **Exact clip duration** — seconds per shot, and max total video length.
2. **Max shot count** per video.
3. **Dialogue character limit** per shot (determines line length — critical for
   writing to spec).
4. **Free-tier throughput** — generations per day, queue speed, cooldowns. This
   directly caps "how many videos can I put out right now."
5. **Watermarking** on free exports, and output resolution / aspect ratio control.
6. Whether exported video retains Cantina branding for cross-posting to our own
   TikTok/Shorts channels.

**Recommended next step:** run one throwaway video end-to-end in the app to
measure #1–#5 empirically, then write scripts to the measured spec rather than
guessing.
