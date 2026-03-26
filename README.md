# Phase Machine

A browser-based phase machine inspired by Steve Reich's tape and process compositions.

Two identical loops play simultaneously. One runs slightly faster. As they drift apart, the auditory system constructs patterns that don't exist in either loop alone. Hold **K** to freeze the offset and run both tapes at the same speed — a feature from Reich's live performance practice that most digital implementations omit.

→ **[Read the article](https://www.jordanelias.de/blog/phase-machine/)** — the history of *It's Gonna Rain*, what the sync function reveals about process and agency, and the connection between phase music and therapeutic frameworks.

---

## How to use

**Option 1 — use it live**
The tool is embedded in the article at [jordanelias.de/blog/phase-machine/](https://www.jordanelias.de/blog/phase-machine/).

**Option 2 — download and open locally**
Download ZIP → unzip → open `index.html` in any modern browser. No internet required after first load (Google Fonts will be absent offline but everything else works).

**Option 3 — clone**
```bash
git clone https://github.com/jordan-elias/phase-machine.git
cd phase-machine
open index.html
```

---

## Controls

| Control | What it does |
|---|---|
| **Drift rate** | How much faster tape B runs, as a percentage. +1% means tape B runs 1% faster. |
| **Tape A vol / Tape B vol** | Independent volume for each tape. Useful for bringing one loop in and out. |
| **K key (hold)** | Runs both tapes at the same rate while held. Offset freezes. Release resumes drift. |
| **K button** | Same as the K key, for mobile. Press and hold. |
| **Reset** | Returns both tapes to the start of the loop. |

---

## Sources

- **Default loop** — a short generated rhythmic pattern (1.6 seconds) designed so phasing effects are immediately audible
- **Upload file** — any audio format the browser supports (MP3, WAV, OGG, etc.)
- **Microphone** — records up to 6 seconds; click the record button, speak or play something, click stop

---

## The sync hold

Most digital phase machine implementations omit the sync hold function. This omission matters: without it, the tool can only simulate the original tape accident (continuous, uncontrollable drift). With sync hold, the performer has genuine agency — they can choose which phase relationships to hold and when to let drift resume.

Reich's phasing began as an artefact of imprecise motor speeds in analogue tape equipment. The machines did what the machines did. Transferring that process to live performers (in *Piano Phase*, *Violin Phase*) introduced intention into what had been mechanical. The sync hold continues that logic: it turns an otherwise automatic process into a gesture, a choice, a compositional act.

---

## What to listen for

As the loops drift:
- **Canons** form when the offset is short — the later loop echoes the earlier one
- **Polyrhythm** emerges at mid-phase — the two streams are maximally interleaved
- **Apparent accelerations** arise as the auditory system re-groups the material
- **Re-unison** occurs when the offset completes a full loop length

These effects are most pronounced with short loops (under 2 seconds) and are clearest with rhythmically distinct material — percussive sounds, spoken syllables, short melodic fragments.

---

## Loop length and drift rate

| Drift | 0.5s loop | 1.6s loop (default) | 4s loop |
|---|---|---|---|
| +0.5% | ~100s per cycle | ~5 min | ~13 min |
| +1.0% | ~50s per cycle | ~2.5 min | ~7 min |
| +2.0% | ~25s per cycle | ~80s | ~3.5 min |

---

## Technical notes

- Web Audio API — no server, no dependencies
- Two `AudioBufferSource` nodes with independent `playbackRate` values
- Sync hold: captures approximate current position of both sources using `AudioContext.currentTime`, stops and restarts both from those positions at rate 1.0, then restores drift on release
- Position tracking is approximate (derived from elapsed time × rate) because Web Audio's `AudioBufferSourceNode` does not expose a readable playback position


## About

Made by [Jordan Elias](https://www.jordanelias.de) — music therapist, researcher, and educator based in Berlin.
