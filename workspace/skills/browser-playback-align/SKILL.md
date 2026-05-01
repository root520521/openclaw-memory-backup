---
name: browser-playback-align
description: Align a browser media playback session with a local worker, runtime, or decrypt/remux pipeline. Use when debugging playback mismatches between browser and local runs, reproducing worker state locally from a page URL or playlist, comparing `vmpTag`-like state sequences, tracing zero-length decrypt outputs, mapping browser worker calls back to raw media units, or replaying browser-to-worker message order offline.
---

# Browser Playback Align

Use this skill when a browser player works one way and a local reproduction works another way.

## Core Workflow

1. Identify the real browser session.
   Capture the target page URL, actual worker URL, actual session/media ID, actual playlist/segment URLs, and the browser worker state sequence.

2. Reproduce with the worker path first.
   Prefer the actual browser worker or worker-harness path over calling a lower-level runtime directly. Lower-level runtime calls are useful for reduction, but they often miss session state.

3. Map zero-output calls back to raw media units.
   Search worker logs for zero-length outputs, then map them to segment index, call ordinal, media unit type, timing, and raw input bytes.

4. Compare state lines, not just inputs.
   When the same media unit behaves differently, compare the browser and local state sequence at the same ordinal. A matching input with a different state line is a different experiment.

5. Replay browser message order locally.
   Capture the actual main-worker `postMessage` sequence from the browser. Replaying just the final media segments is often not enough.

6. Reduce the divergence window.
   Once you locate a problematic call, compare its neighboring ordinals, try alternate timing tags, and skip earlier ordinals to find which earlier inputs build the later state line.

## Operating Rules

- Treat the browser main worker as authoritative for state sequencing.
- Ignore audio-worker state when the bug is in the main video/decrypt path.
- Do not assume the worker state is a pure function of one media unit. Earlier control messages and prior media units can matter.
- Do not assume matching page URL, time, and worker URL are sufficient. They help, but they do not guarantee a matching state line.
- Keep browser capture artifacts and local replay artifacts side by side so each claim can be traced to a file.

## Typical Questions This Skill Should Answer

- Which earlier browser call first pushed the worker into the problematic state line?
- Does zero-length output happen only in the browser, only locally, or in both?
- Is the problem tied to one timing tag, one media unit family, or one state transition?
- Does skipping or replaying an earlier ordinal change the later failure?
- Does replaying the browser main-worker message order make the local state sequence converge?

## Reference File

- For concrete capture, replay, and reduction patterns, read [references/playbook.md](references/playbook.md).
