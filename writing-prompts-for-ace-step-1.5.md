# Writing Prompts for ACE-Step 1.5

*A practical guide for rAIdio.bot users*

ACE-Step is a powerful model, and once you understand how it thinks and learn to speak to it in a way it understands the mystery goes away and you'll learn how to make sure your outputs become predictable in the good way.

This is not a list of tricks but encapsulates what the author of rAIdio.bot has learned while working with ACE-Step's model in this and other projects. My hope is that by the end of this wall of text you will be able to write your own prompts with confidence, and know why they work or do not, and how to iterate on them when they do not.

rAIdio.bot - Make Music!

Christopher Neitzert - rAIdio.bot Lead Developer, April 2026 (revised June 2026)

---

> Before anything else, the one rule that matters more than every
> rule below: **the more specific and detailed your prompt, the
> better the output.** The model is doing its best to match what
> you describe. If you want a tight 100 BPM old-school hip-hop
> track with a hard TR-808 kick and a snappy snare, you have to
> say that. If you just say "hip hop," you get something generic.
> It is not magic — it is doing what you ask. Ask well.
>
> Everything below is how to ask well.

---

## The Mental Model

The best way to think about how ACE-Step 1.5 works is that it has two brains working in sequence.

The first is a Language Model that acts as a planner. It reads your prompt and builds a song blueprint, like a complete plan for what the track will be.

The second is a Diffusion Transformer, an audio engine that takes that blueprint and renders it into 48 kHz stereo audio.

You are writing for the planner, not the audio engine. This matters because the planner needs a clear statement of what you want to hear, not a vibe.  If the planner gets confused, the renderer produces mush, no matter how good your adjectives were. 

Think of it like commissioning a session band. You are not performing the music. You are telling the band what to play. The clearer your instructions, the closer the take is to what you had in mind.

Be direct. Be specific. Be concrete.

---

## The Three Fields

Every ACE-Step prompt has three inputs, and each one has a specific job.

**Tags** are global controls. Comma-separated keywords that define genre, instruments, mood, and tempo. This is the "who is in the room and what are they holding" field.

**Caption** is one paragraph describing the complete musical vision. This is the brief. Short, specific, evocative.

**Lyrics** are what gets sung, plus structure markers like `[verse]` and `[chorus]`. For instrumental tracks, this field is where you say so.

Three fields. Three jobs. Keeping them separate is the single biggest thing you can do to improve your results.

---

## Three Ways to Start

You do not have to write a prompt from scratch every time. rAIdio.bot gives you three on-ramps for the Text to Music panel. Pick the one that fits how you are working today.

**Surprise Me.** One click. Pulls a random entry from a hand-curated pool of about forty presets spanning every major genre cluster. Fills all three fields plus duration. Use this when you want to hear what the model can do, when you are stuck and need a starting point that is already known to work, or when you want a quick benchmark before tuning.

**The Wizard.** Five short steps: purpose, vibe cluster, mood + tempo + structure, duration, lyrics. The Wizard layers your choices over a curated preset and outputs a fully populated prompt ready to generate. Use it when you have a clear idea of what you want but do not feel like writing it out, or when you are new and learning what the three fields do by example. The five vibe clusters are DANCE / ELECTRONIC, 80s / SYNTH, HIP-HOP / BEATS, ROCK / GUITAR, and ORGANIC / CINEMATIC. Pick as many as you like — or none, and the Wizard roams the full pool.

**Manual prompt.** You fill in the three fields yourself. The rest of this guide is about how to do that well.

The three paths are not mutually exclusive. Most people use Surprise Me or the Wizard to get a working prompt, then tune the fields manually. That is the intended workflow.

---

## Tags: The Global Controls

The sweet spot is **3 to 8 tags, with specificity beating count**. Any fewer than 3 and the planner improvises too much. Beyond about 8 the signals start averaging into mud — but only if you are piling on vague terms. A long list of specific tags ("TR-808 drum machine, vinyl scratching, shouted vocals") still works because each one carries musical content. A long list of vibe words ("cool, party, banger, summer, wild, fire") averages into nothing.

Specificity matters more than count. If every tag names a real sonic element, you can go to 8 or 9. If your tags are mostly mood words, stop at 5.

**Order matters.** The planner reads tags left to right and weights the early ones more heavily. Lead with genre, then era or subgenre, then instruments, then mood, then BPM.

A working example:

> `liquid drum and bass, atmospheric, ethereal pads, sub bass, 174 BPM`

Five tags. Genre first. Texture second. Two instruments. Tempo last. The planner knows exactly what to build.

A failing example:

> `cool vibe, party, weekend, banger, summer, crazy, good time, wild, feel good, fire`

Ten tags and none of them describe sound. The planner has nothing to work with.

### Specific Beats Poetic

This is the single most useful rule.

| Use this | Not this |
|---|---|
| slap bass | funky groove |
| gated snare | big 80s drums |
| 174 BPM | fast |
| dusty drums | old school feel |
| Rhodes chords | warm keys |
| Amen break | breakbeat vibes |

Named instruments, named techniques, and numbers all carry weight. Vibes do not.

### Do Not Combine Contradictions

"Upbeat, melancholic" does not average into bittersweet. The model does not know what to do with it. Same with "ambient, metal" or "acoustic, industrial." Pick a lane.

If you want emotional contrast in the track, build it into the arrangement through the caption. That is where motion and tension live.

---

## Caption: The Brief

One paragraph. Under 40 words is ideal. Describes instruments, motion, mood, and context together.

Imagine you have 15 seconds with a session band in the hallway before a take. What do you say? That is your caption.

A working example:

> Liquid drum and bass with rolling breakbeats, ethereal pads, and deep sub bass that pulls you forward. Energetic but smooth.

Let us unpack why this works.

Three named instrument elements (breakbeats, pads, sub bass). One motion verb (pulls you forward). One resolving mood pair (energetic but smooth, where "smooth" qualifies "energetic" rather than contradicting it). 22 words total. The planner can translate every part of this into concrete arrangement choices.

### What Kills Captions

Abstract emotional words with no sonic anchor. "Dreamy, epic, vibey, haunting, magical." These sound like something, but they tell the planner nothing about what actually happens in the arrangement.

Contradictory mood pairs. "Aggressive yet peaceful" makes the planner hesitate. Pick one and let the other appear through contrast in the music itself.

Instruction language aimed at the listener. "Get ready for" and "prepare to be blown away" will very likely be ignored by the planner, but if they are not, they will be sung as part of the track. If you want to set up the listener, do it through the music, not through instructions in the caption.

---

## Lyrics: Structure and Pacing

Even for instrumental tracks, this field does work. For tracks with vocals, the rules get specific.

### Hard Numbers on Pacing

ACE-Step sings at roughly 2 to 3 words per second. For a standard 47-second track, aim for 90 to 140 words total. Go over and it rushes. Go under and it leaves gaps.

Short lines of 4 to 8 words sing cleanest. Tongue twisters and long sentences collapse. Simple language sings better than clever language. This is a music model, not a poetry editor.

### How Section Tags Actually Work

The planner does not have a hard-coded list of section markers. The lyrics tokenizer has no special tokens for `[verse]`, `[chorus]`, etc. — those go through the same path as any other text. Instead, the model has *learned* during training that bracketed strings indicate structural divisions in songs. The training data was full of `[verse]` / `[chorus]` / `[bridge]` patterns, so it knows what they mean. This is also why inconsistent markers (`[hook]`, `[breakdown]`, `[refrain]`) can work or fail depending on whether the model saw enough of them in training.

### The Safe Set

These markers are documented in the ACE-Step team's own examples and tutorials and work reliably:

`[intro]` `[verse]` `[pre-chorus]` `[chorus]` `[bridge]` `[outro]` `[instrumental]` `[guitar solo]` `[inst]`

Use them. They push the model toward song form instead of a continuous loop.

### Annotated Section Tags (Advanced)

You can also write annotated section tags — bracketed markers with a description of what should happen in that section:

```
[Intro - vinyl crackle, DJ scratch builds, 808 drops]
[Verse - dual MC call and response]
[Break - scratch solo, transformer cuts]
[Outro - 808 fade, scratch tail]
```

This form is **not officially documented** by the ACE-Step team, but it works reliably in practice. The likely reason: the model has seen similar annotated patterns in training data (song scripts, songwriter forum posts, production notes), and it has learned to read the description inside the bracket as section-specific direction.

Treat this as advanced technique. It is more powerful than the bare markers because it lets you direct each section individually, but it is also less officially sanctioned, so genres outside the mainstream may produce less consistent results. When it works, it works extremely well.

### Anything That Is Not a Recognized Tag Gets Sung

This is the trap that catches almost everyone the first time. The lyrics field is literal. If you write `(fade out)` or `(chorus repeats)` or `[stage direction]` in there, and it is not on the list of recognized structural tags above, the vocalist will sing those words out loud.

There are no stage directions in this field. No narrator notes. No parenthetical instructions. Every character you put in lyrics that is not a recognized bracketed tag is treated as something to vocalize. Plan accordingly.

If you want production moves like fades, filter sweeps, or drops, put those in the caption, render as is, and split stems in the rAIdio.bot interface to add those effects in post. Do not put them in the lyrics, the AI-vocalist will sing "fade out" and "filter sweep" and "drop" as part of the track.

One designed exception: the annotated section tag form above (`[Intro - vinyl crackle, 808 drops]`). The model interprets bracketed descriptive content as section direction, not as text to vocalize. Parenthetical content is still vocalized — only square-bracketed structural sections get the special treatment. If a section tag does get vocalized, it is a sign that the model did not parse it as a structural marker, which is a useful signal that the wording needs to be tuned.

### Backing Vocals: The Parenthesis Trick

Text inside parentheses gets sung as backing vocal lines. Use this to layer harmonies, call-and-response phrases, or doubled hooks:

```
[chorus]
Walking through the empty square (empty square)
Holding nothing, going nowhere (nowhere, nowhere)
```

The vocalist will render the parenthetical as a separate harmony layer underneath the main line. This is the documented way to get backing vocals without writing a separate vocal arrangement.

### Vowel Extension and Phonetic Spelling

You can control vocal length and pronunciation phonetically. Want a sustained "oh"? Write "ooooh" or "oh-oh-oh". Want a held belt note on "yeah"? Write "yeaaaaaah". Want a specific vowel sound on a vague word? Spell it phonetically.

```
Yeaaaah, I'm fading (fading, fading)
Oooh-oh-oh, into the evening light
```

The model treats repeated vowels as longer notes and uses the exact spelling to pick the pronunciation. This pairs well with the BPM tag — if your tempo and vowel-length signals agree, phrasing locks in.

### Instrumental Tracks

If you want no vocals, put `[instrumental]` as the only content in the lyrics field, and add "instrumental" to your tags as a backup signal. Both places. Redundant on purpose. This is the documented fix for vocal bleed.

### Match Your Lyrics to Your Tags

Sad lyrics with party tags produce confusion. The emotional tone needs to be consistent across all three fields. If your tags say "upbeat pop" and your lyrics are about heartbreak, pick one and let the other fit.

---

## Duration: The Fourth Lever

Duration is not a field you fill in with words, but it changes everything the other three fields produce. The planner uses duration to decide how much song to build, which sections fit, and how densely to pack them.

Short durations (under 30 seconds) favor loops, stings, and bumpers. The planner will compress structure, often collapsing intro and verse into a single idea. Section tags still work, but the model has less room to develop them.

Medium durations (30 to 90 seconds) are the sweet spot for most use cases. Podcast themes, social posts, background cues. Enough room for a real arc, short enough that the planner stays focused.

Long durations (90 seconds to 4 minutes) let the planner build full song form. Intro, verse, chorus, bridge, outro, all rendered with breathing room. This is also where lyric word count matters most, since the pacing math (2 to 3 words per second) scales with length.

The same prompt will produce different results at different durations. A 30-second take of your prompt is not a shortened version of the 2-minute take. The planner made different compositional choices. If you change duration, expect to re-evaluate the output.

A practical rule: set duration first, then write the prompt to fit it. Writing a verse-chorus-bridge-outro structure into a 20-second track forces the planner to compress things that do not want to be compressed.

---

## A Complete Working Prompt

Here is the whole thing in the format rAIdio.bot uses. Tags, then caption, then lyrics.

```
Tags: liquid drum and bass, atmospheric, ethereal pads, sub bass, 174 BPM
Caption: Liquid drum and bass with rolling breakbeats, ethereal pads, and deep sub bass that pulls you forward. Energetic but smooth.
Lyrics: [instrumental]
```

That is a reliable prompt. It will sound roughly like 2000-era SF club liquid DnB most of the time. Change one field at a time when you iterate.

Here is the same structure for a vocal track:

```
Tags: indie pop, female vocal, bright, acoustic guitar, 118 BPM
Caption: Bright indie pop with strummed acoustic guitar, claps, electric piano, and a clear female lead vocal. Warm, open, Saturday afternoon, long fade out.
Lyrics:
[verse]
Tuesday morning, traffic slow
Nothing on the radio
[chorus]
Three more blocks until the light
Three more blocks until I know
[outro]
```

Note where the fade out lives. It is in the caption, not in the lyrics. If it were in the lyrics, the vocalist would sing "fade out" out loud.

Three fields, all three doing their job.

---

## The Technical Controls

Past the three prompt fields and duration, ACE-Step exposes a set of technical parameters that shape how the generation actually runs. You do not have to touch these to get good output, and the defaults are set the way they are for good reasons. But understanding what each one does lets you fix problems that prompt changes cannot fix.

The values below are grounded in the official ACE-Step documentation[^1][^2][^3] and the community-validated recipe from the widely-cited Hugging Face tutorial by Rexx12[^4], which represents roughly six hours of systematic parameter testing and has become the de facto starting point for most ACE-Step setups.

### Model Selection: Standard vs XL

rAIdio.bot ships two ACE-Step variants. You can switch between them in the advanced controls.

**Standard** runs on every supported GPU. It produces good output quickly. This is the default and the right choice for most sessions — quick iteration, batch experimentation, anything where you want to try a lot of ideas fast.

**XL High Quality** is a larger model that requires 20 GB or more of GPU VRAM (3090, 4090, 5090, RTX 6000 Pro tier). It produces noticeably richer output for the same prompt — more detailed arrangement, more believable timbre, fewer "obviously AI" tells. It also takes meaningfully longer per generation, which makes it worse for browsing and better for the final take of a track you already know you want.

Practical workflow: write and iterate on Standard, then re-render the take you want on XL when you have settled on a prompt.

One technical note: CFG Scale only behaves the way the rest of this guide describes on Standard (non-turbo) models. On XL Turbo the CFG control is present but has reduced effect — the model is trained differently. If you are tuning CFG, do it on Standard.

### Key

The musical key sets the tonal center of the entire generation. Format is note plus mode, like "C major," "F# minor," or "Bb major"[^5].

When you leave key to the default, the Language Model planner picks one based on your tags and caption. This usually works fine because "lo-fi hip hop, warm piano" produces something that lands in a comfortable key on its own.

When you set key explicitly, you are overriding the planner. This is useful when you need the output to fit alongside existing musical material, when you want to generate multiple tracks in the same key for a mix, or when the planner keeps picking a key that does not serve the mood you want. Dark, tense tracks benefit from minor keys. Bright, lifting tracks benefit from major keys. Locrian and Phrygian modes produce distinctly unstable, tense feelings. The planner does not always pick the key that matches your emotional intent, so this is a useful lever when mood is critical.

### Seed

The seed is the starting noise pattern for the diffusion process. A seed of -1 means random, and you get different output every time. Any positive integer is a fixed seed, and that same prompt plus that same seed reproduces the same generation[^1][^3].

This is the most useful parameter for tuning, and most people ignore it. The official ACE-Step tutorial puts it plainly: fix the seed when you are tuning other parameters, otherwise you cannot tell if a change sounds different because of the parameter or because of the randomness[^2].

When you get a generation that is 80 percent of what you want, save the seed. Change one other parameter. Regenerate. Now you are measuring the actual effect of that parameter. When you are just browsing for something you like, leave it at -1.

### Samplers

The sampler is the algorithm that walks the diffusion process from noise to audio. ACE-Step exposes several and they produce meaningfully different results on the same prompt.

The canonical ACE-Step recipe uses `er_sde`[^4]. Per Rexx12's documented testing, this produced the cleanest and most musically stable output across many generations, with fewer sudden rhythm changes than the alternatives. The DPM++ family (`dpmpp_2m`, `dpmpp_sde`, `dpmpp_3m_sde`) and `uni_pc` consistently produced noise and artifacts in that testing.

Community variations exist and have their own merit. `euler` and `dpmpp_2m` can sound better on some instrumental content, particularly keyboards, but often produce vocal problems. `dpm_adaptive` paired with 100 steps and lower CFG has been reported as superior for metal and other high-energy guitar music.

The short version: start with `er_sde`. Change it only if you have a specific reason.

### Schedulers

The scheduler controls how the sampler distributes its denoising steps across the generation. `linear_quadratic` is the ACE-Step community default and the one paired with `er_sde` in the canonical recipe[^4]. The others (`simple`, `karras`, `exponential`, `beta`) are legitimate alternatives, with `karras` being a standard carryover from the image diffusion world and `beta` showing up in some of the reported alternative stacks.

Like samplers, you should treat this as a pair-with-the-sampler decision rather than an independent tuning dial. `er_sde` plus `linear_quadratic` is the tested combination. Changing one without the other often makes things worse.

### Steps

Steps is how many refinement passes the sampler makes. More steps means finer detail and more time per generation.

The canonical recipe uses 65 steps[^4]. The logic: at low CFG values (more on that below), the model needs more steps to refine the audio into something coherent. Going much higher than 65 can destabilize the generation. Going much lower produces audible noise and artifacts. The official ACE-Step team's own parameter discussion settles in a similar range, with 50 to 120 steps covering most production use cases[^6].

BPM shown next to steps in the UI is a separate control entirely. The lock icon next to BPM in rAIdio.bot's interface is for locking the tempo to your tag value rather than letting the planner drift it.

### CFG Scale

CFG stands for Classifier-Free Guidance. Higher CFG means the model follows your prompt more closely. Lower CFG gives the model more creative latitude[^1].

The official range is 1.0 to 15.0. The official documentation cites a typical range of 5.0 to 9.0, noting that CFG only applies to non-turbo models[^1].

The widely-tested community recipe lands at CFG 4.0[^4]. The reasoning: lower CFG prevents harsh, noisy artifacts and lets the model produce musical results, while higher CFG tends to make the output sound over-committed and brittle. Rexx12's testing identifies CFG 6.0 as a breaking point where quality degrades noticeably. This is why the canonical recipe pairs low CFG with high steps (65). The steps compensate for the interpretive freedom the low CFG allows.

If your output is ignoring your tags entirely, raise CFG a little. If your output sounds harsh or noisy, lower it. If you do not have a specific problem, 4.0 is a reliable floor.

### Batch Size

Batch size is the number of generations produced per run. The model's seed variance means you will get better results more often by generating 8 or 16 at a time and cherry-picking than by generating one at a time and hoping[^4]. This is the documented workflow, not a hack around a flaw. Plan around it.

### The Canonical Recipe, For Reference

If you want a single set of defaults that have been validated across thousands of generations, this is it[^4]:

```
Sampler:    er_sde
Scheduler:  linear_quadratic
Steps:      65
CFG:        4.0
Seed:       -1 (fix it when tuning)
Batch Size: 8 or 16 (the slider allows 1 to 16; 8 or 16 is the
            sweet spot for cherry-picking)
```

Start here. Change one parameter at a time when you have a reason. Keep the seed fixed while you tune.

---

## Style Transfer

Style Transfer is a separate generation mode. Instead of writing a caption to describe what you want, you upload a reference audio clip and the model generates new content that inherits the reference's sonic character — its instrumentation, production texture, mood, and rough tempo.

You still write Tags and Lyrics. The reference clip replaces the Caption as the primary brief.

**Important:** do not upload copyrighted material or other people's music here. It is a violation of the rAIdio.bot EULA ([./EULA.md](./EULA.md)). Use only material you have the right to use — your own recordings, properly licensed audio, public-domain audio, or Creative Commons with terms that allow derivative work.

### What the Strength Slider Does

The Strength slider controls how heavily the reference influences the output.

- **At low values (0.1 to 0.3)** the reference contributes texture and feel but the tags drive most of the arrangement. Use this when you have a strong tag-side vision and want the reference to flavour it.
- **Mid values (0.4 to 0.6)** are the workhorse range. The reference and the tags negotiate. Most usable Style Transfer output lives here.
- **High values (0.7 to 1.0)** lock the output tightly to the reference's character. Use this when you are trying to extend or remix an existing track and you want the new content to feel like the same recording.

### Choosing a Reference Clip

A few empirical rules:

- **Clean recordings beat live recordings.** Mastered studio output gives the model less noise to fight through.
- **Instrumental beats vocal-heavy.** If your reference has strong vocals, those tend to bleed into the output as ghost vocals or vocal-shaped instruments. For new instrumental content, pick an instrumental reference, or split the stems and use just the instrumental version.
- **Consistent texture beats arrangement variety.** A 30-second clip with one consistent vibe transfers more cleanly than a 90-second clip that goes through several sections.
- **Match your tags to your reference.** If you want a jazz piano trio output and your reference is metal guitar, the model has to pick one. It usually picks the reference.

### A Working Style Transfer Prompt

```
Reference clip: (a 30-second cut of late-90s liquid drum and bass)
Tags: liquid drum and bass, atmospheric, ethereal pads, sub bass, 174 BPM
Lyrics: [instrumental]
Strength: 0.5
```

This produces new liquid DnB that inherits the reference's pad sound and breakbeat character without copying its arrangement.

---

## Iterating Without Starting Over

When something is close but not right, resist the urge to rewrite the whole prompt. You will lose the good parts with the bad ones.

The order of operations that saves time:

1. **Change one tag.** Swap tempo, swap an instrument, swap a mood word. Regenerate.
2. **Adjust one caption phrase.** Sharpen a motion verb, trade a mood dyad, name an instrument more specifically. Regenerate.
3. **Edit one lyric section.** Tighten a verse, rewrite a chorus, change a structure marker.

Small deltas produce learnable results. Big rewrites produce mystery.

---

## The Gacha Reality

ACE-Step is sensitive to random seeds. The team acknowledges this openly. Two generations from the identical prompt can sound different, sometimes meaningfully different. This is not a bug you can prompt your way out of. It is how the model works.

The practical answer is batch generation. Generate multiple takes from the same prompt and pick the best one. This is the documented workflow, not a workaround.

If you run three seeds and all three sound bad, the prompt needs work. If you run three seeds and one is great, the prompt is fine and you found your take.

Some genres are more reliable than others. Lo-fi hip hop, deep house, ambient drone, boom bap, synthwave, trap, and solo piano essentially never fail. Post-rock, trailer score, and UK garage have higher variance because their structural or timing demands are harder for the planner to nail on every seed. Plan accordingly.

---

## Quick Reference

Keep tags between 3 and 7, ordered genre to BPM.

Keep captions under 40 words, specific instruments, one motion verb, resolving mood pair.

Keep lyrics at 90 to 140 words for a 47-second track, 4 to 8 words per line.

Anything in the lyrics field that is not a recognized bracketed tag gets sung. No stage directions, no parentheticals, no notes to self.

Put `[instrumental]` in the lyrics field and "instrumental" in the tags when you want no vocals.

Use section markers. `[intro]` `[verse]` `[pre-chorus]` `[chorus]` `[bridge]` `[outro]` `[instrumental]`.

Set duration first, then write the prompt to fit it.

Do not combine contradictory tags.

Start with the canonical recipe: `er_sde` sampler, `linear_quadratic` scheduler, 65 steps, CFG 4.0.

Fix the seed when tuning parameters. Leave it at -1 when browsing.

Change one thing at a time when iterating.

Run batches of 8 or 16 and pick the best one.

Try Surprise Me or the Wizard before writing from scratch. They get you to a working prompt in seconds.

Pick Standard for iteration, XL for the final take. XL is higher quality but slower per generation.

Style Transfer takes a reference clip instead of a caption. Mid-range strength (0.4–0.6) is where most usable output lives.

Use parentheses for backing vocals. `(words in parens)` get sung as a harmony line.

Phonetically extend vowels ("ooooh", "yeaaaah") to control vocal length and pronunciation.

Annotated section tags (`[Intro - vinyl crackle, 808 drops]`) work in practice and let you direct each section individually.

The one rule that beats every rule: the more specific and detailed your prompt, the better the output. Ask well.

---

## Vocabulary That Pays Off

You do not need to be a musician to write good prompts. You need just enough vocabulary that you can name what you hear in your head. The terms below — production language, music theory, instrumentation, articulation — all carry weight with the planner. Drop any of them into a tag list or caption and the output gets noticeably more specific.

If half this list looks Greek, ignore those entries. Pick up the ones that connect to sounds you can already hear and the rest will come with time.

**Drum sounds and machines**

- **TR-808** — the deep boomy kick + snappy snare of 80s hip hop and modern trap.
- **TR-909** — punchier kick, sharper hi-hats; the house and techno sound.
- **TR-707** — drier, cleaner; 80s pop and electro.
- **Gated snare** — the huge ambient snare that defined 80s arena rock and power-ballad production.
- **Amen break** — the classic breakbeat sample; jungle and DnB starting point.
- **Boom bap** — sampled, slightly off-kilter drums; 90s East Coast hip hop foundation.

**Bass**

- **Sub bass** — felt-not-heard low frequencies; modern hip hop and DnB.
- **Slap bass** — percussive fingerstyle electric bass; funk and fusion.
- **Reese bass** — detuned sawtooth pad-bass hybrid; DnB and dubstep.
- **Walking bass** — moving quarter-note line; jazz, blues.

**Production techniques**

- **Side-chain compression / side-chain pump** — the rhythmic "breathing" kick-bass effect in house and EDM.
- **Tape compression** — warm, slightly squashed mix character; vintage and lo-fi.
- **Vinyl crackle** — surface noise of an LP record; lo-fi hip hop and chillout.
- **Reverb tail** — the decay of a sound after the source stops; short for tight rooms, long for cathedrals.
- **Filter sweep** — opening or closing a filter over time; builds and drops.
- **Vocal chop** — short pitched samples of vocals used as a rhythmic instrument; future house and pop.

**Texture and feel**

- **Lo-fi** — intentionally low-quality, warm, hissy; the "studying to" sound.
- **Hi-fi** — clean, full-range, polished.
- **Dusty** — slightly dirty, vintage-feeling; sample-based production.
- **Ethereal** — airy, reverb-heavy, atmospheric.
- **Crunchy** — distorted in a musical way; guitar, drums, vocals.
- **Wide stereo pans** — instruments spread far left and right across the stereo field; immersive headphone listening, modern pop production.
- **Saturation** — gentle musical distortion that adds warmth and harmonics; analog feel.
- **Wet vs dry** — heavy reverb / delay vs minimal effects. Wet = cathedral; dry = close studio mic.
- **Tape hiss** — analog noise floor; lo-fi, vintage, nostalgic.
- **Bit-crushed** — sample-rate or bit-depth reduction; chiptune, breakcore, deliberate digital lo-fi.
- **Compressed and loud** — modern mastering; radio-ready, hits-you-in-the-chest energy.

**Vocal styles**

- **Belt** — full-voice loud singing; pop power notes.
- **Falsetto** — head-voice high range; soul and R&B.
- **Whisper register** — quiet, intimate vocal; indie and folk.
- **Auto-tune** — pitch correction applied as a creative effect; modern hip hop and pop.

**Modes and tonal centers**

The Key picker in rAIdio.bot accepts all of these. Specifying a mode is one of the highest-leverage moves you can make if you know what they sound like.

- **Major** — bright, resolved, conventional. The default for happy and uplifting tracks.
- **Minor** — darker, more emotional. Blues, metal, ballads, most pop hits since 2010.
- **Dorian** — minor with a brighter 6th. 60s modal jazz, Celtic, classic British rock.
- **Phrygian** — minor with a flat 2nd. Flamenco, metal, Mediterranean / Middle Eastern flavours.
- **Lydian** — major with a sharp 4th. Dreamy, floating, classic film score.
- **Mixolydian** — major with a flat 7th. Bluesy major, 60s British folk-rock, 70s southern rock.
- **Locrian** — extremely unstable, rarely used outside of metal and experimental.

**Chord types**

- **Major 7th** — jazzy, warm, sophisticated. Bossa nova, lounge, neo-soul.
- **Minor 7th** — smooth, soulful. Jazz, R&B, neo-soul.
- **Dominant 7th** — bluesy, leaning toward resolution. Blues, funk, classic rock.
- **Sus2 / Sus4** — open, unresolved, atmospheric. Pop ballads, shoegaze.
- **Diminished** — tense, scary. Horror film cues, classic Hitchcock string stabs.
- **Augmented** — uneasy, off-balance. James Bond intro chord territory.

**Chord progressions** (great as caption descriptors)

- **ii-V-I** — the jazz progression. Sophisticated resolution.
- **I-IV-V** — the rock and country backbone.
- **I-V-vi-IV** — the pop progression. Late-70s through 2010s pop and rock staple.
- **12-bar blues** — the canonical blues form. Naming it pulls the whole genre.
- **Andalusian cadence** — flamenco / Greek / Hebrew-feeling descending progression.

**Rhythm and time**

- **4/4 time** — standard pop / rock / EDM. The default if unspecified.
- **3/4 / waltz time** — three-beat feel. Ballads, classical, country waltzes.
- **6/8** — compound time, lilting. Doo-wop, slow blues, Irish folk.
- **7/8 or 5/4** — odd time. 60s cool jazz, 70s prog rock, math rock.
- **Swing** — triplet subdivisions of beats. Jazz, blues, swing-era.
- **Shuffle** — half-swing. Blues, early rock and roll, Texas blues guitar.
- **Syncopation** — emphasis on off-beats. Funk, salsa, modern pop.
- **Polyrhythm** — two different rhythms running simultaneously. West African music, math rock, prog.

**Articulation and dynamics**

- **Staccato** — short, detached notes.
- **Legato** — smooth, connected notes.
- **Pizzicato** — plucked strings (used as a noun for the technique on bowed instruments).
- **Tremolo** — rapid repetition of a single note. Tense or shimmering.
- **Crescendo / decrescendo** — gradually getting louder / softer.
- **Call and response** — one voice or instrument states a phrase, another answers. Gospel, blues, dual-MC hip hop, jazz trading fours.

### A short reading list for going deeper

You do not need to know everything in any of these. Pick what helps you name the sounds you can already hear.

- **Hooktheory** — searchable database of chord progressions from real songs, plus theory explainers built around hits you know.
- **musictheory.net** — interactive lessons, free.
- **Adam Neely** (YouTube) — accessible theory for working musicians; great on rhythm and groove.
- **8-bit Music Theory** (YouTube) — game music theory, surprisingly broad and approachable.
- **Sound on Sound magazine archive** — production deep-dives and technique tutorials.
- **Reverb.com tutorials** — instrument and gear primers, very beginner-friendly.

The goal is not to become a musician. The goal is to have enough vocabulary that when you can hear a sound in your head, you can name it on the page. When you can name it, the planner has something to work with and you get closer to what you want.

---

## The Real Skill

Prompt writing for ACE-Step is closer to writing a session chart than writing a poem. The musicians you are working with are fast, capable, and literal. They will play exactly what is on the page. Your job is to make sure the page is clear.

The more specific you get, the more the model rewards you. The more abstract you get, the more it improvises, and improvisation is where variance lives.

Write for the planner. Treat the three fields as three jobs. Iterate in small steps. Batch your generations.

That is the whole game.

Happy generating.

---

## References

[^1]: ACE-Step 1.5 Inference Documentation. `INFERENCE.md`, official repository. https://github.com/ace-step/ACE-Step-1.5/blob/main/docs/en/INFERENCE.md

[^2]: ACE-Step 1.5 Tutorial. `Tutorial.md` by Gong Junmin (ACE-Step developer), official repository. https://github.com/ace-step/ACE-Step-1.5/blob/main/docs/en/Tutorial.md

[^3]: ACE-Step 1.5 Gradio Guide. `GRADIO_GUIDE.md`, official repository. https://github.com/ace-step/ACE-Step-1.5/blob/main/docs/en/GRADIO_GUIDE.md

[^4]: Rexx12. "A Practical Tutorial for ACE-Step, Based on 6+ Hours of Research." Hugging Face Comfy-Org ACE-Step_ComfyUI_repackaged, Discussion #1, June 2025. https://huggingface.co/Comfy-Org/ACE-Step_ComfyUI_repackaged/discussions/1

[^5]: Runware. "ACE-Step v1.5 Base Parameters Documentation." https://runware.ai/docs/models/ace-step-v1-5-base

[^6]: ACE-Step. "Parameter Experiments." Discussion #95, official repository. https://github.com/ace-step/ACE-Step/discussions/95
