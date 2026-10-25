# Voice-over and Animation

A [Claude Code](https://claude.com/claude-code) skill that turns a voice recording (or a to-camera phone
video) into a finished, animated vertical Short: every shot is an HTML/GSAP scene timed to the spoken word,
rendered frame by frame in headless Chromium, and mixed with synthesized sound effects and a voice-ducked
music bed.

## What it does

1. **Transcribes locally** with faster-whisper, giving every word a timestamp (the audio never leaves the machine).
2. **Proofreads captions**: names and technical terms are fixed before they're burned in.
3. **Plans a stage list**: for each idea, which real interface to show and what happens in it, word by word. You approve it before anything renders.
4. **Sources media**: photos and clips of the people and products mentioned (Wikimedia, Openverse, Internet Archive, Pexels, YouTube), all credited.
5. **Animates** with the `studio` house style (below) or one of eight other themes.
6. **QA**: an automatic layout check (text off-frame, text under captions, empty shots) plus contact-sheet stills.
7. **Sound**: synthesized hits, whooshes, clicks, message chimes, ticks, plus a music bed that ducks under the voice; mastered to −14 LUFS.
8. **Encodes** 1080x1920 (or 1920x1080) MP4 and reports credits ready to paste into the description.

## The studio style

Distilled from high-performing reference explainers:

- **Show the real thing.** WhatsApp is a WhatsApp chat with messages arriving; M-Pesa is the confirmation SMS; a card payment is a checkout form rejecting the number. Never an icon and a word.
- **The spoken line is the headline.** Words appear at the top as they're said; the keyword gets a selection box with handles and an optional emoji.
- **One stage per idea, constant change inside it.** Clicks, ticks, bars filling, counters, spotlight focus, camera push-ins.
- **Light and bright**, with dark scenes for the twist.
- **Ends with a real ask**: a comment or save CTA.

See [`references/studio-blocks.md`](references/studio-blocks.md) for the UI kit and rules, and
[`references/scene-blocks.md`](references/scene-blocks.md) for transitions, blocks and sound cues.

## Install

```bash
git clone https://github.com/JoylynnWamjiru/VOICE-OVER-AND-ANIMATION.git ~/.claude/skills/voiceover-video
mkdir -p ~/.config/voiceover-video
cp ~/.claude/skills/voiceover-video/brands/joylynntechy.json ~/.config/voiceover-video/brand.json
bash ~/.claude/skills/voiceover-video/scripts/setup.sh
```

Needs `ffmpeg`, `node`, Python with `faster_whisper` and `numpy`; `setup.sh` installs the headless
Chromium, GSAP and the brand fonts. Optional: `yt-dlp` for YouTube clips, `PEXELS_API_KEY` for Pexels.
On Windows read [`docs/windows.md`](docs/windows.md).

## Use

In Claude Code: `/voiceover-video` followed by the path to your recording, e.g.
`/voiceover-video ~/Downloads/mpesa-voiceover.m4a vocab: "M-Pesa, Safaricom, Fuliza"`.

## Layout

```
SKILL.md                 the workflow Claude follows
references/              studio-blocks.md (house style + UI kit), scene-blocks.md (blocks, transitions, sound)
templates/               studio.html (default), kinetic.html, themes/*.css, templates.json
scripts/                 transcribe, captions, media search, template fill, render, sound synth, mix/encode
brands/                  brand files (handle, colours, fonts, output dir)
docs/windows.md          Windows notes
```
