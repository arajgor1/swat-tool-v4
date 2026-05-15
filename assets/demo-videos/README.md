# HeyGen Avatar Clips — SWAT Demo

Drop HeyGen-generated MP4 clips into the persona folders below using the
exact filenames listed. They're loaded at runtime by `DEMO_VIDEO_MANIFEST`
in `index.html` (search the file for that constant to edit the mapping).

When a clip exists for a step it plays inside the meeting-frame webcam
panel, replaces the static presenter image, and supplies its own audio.
The TTS narration is suppressed for that step. Auto-advance fires on the
video's `ended` event.

If a clip is missing or fails to load, the step gracefully falls back to
the existing TTS narration + static image.

## File requirements

- **Format:** MP4 (H.264 + AAC). Web-friendly; works in all modern browsers.
- **Aspect ratio:** 4:3 to fit the webcam panel (`object-fit: cover` will crop).
- **Resolution:** 720x540 or 960x720 is plenty — the panel is ~240px wide.
- **Audio:** Embedded; this is what the audience hears (no TTS overlay).
- **Length:** Match the narration. The step auto-advances 1.5s after `ended`.

## Sub-point sync

Steps with `subPoints` (e.g. the spotlight moves between cells mid-narration)
fire those cues based on the video's `currentTime`. The `at:` value in each
sub-point is interpreted as **milliseconds from video start**. Tune those
numbers in `index.html` once you've recorded the clip and know its pacing.

## Filenames

### Buyer — Sarah Mitchell (`buyer/`)

| Step | Filename |
|------|----------|
| 0  | `01-morning-login.mp4` |
| 1  | `02-red-banner.mp4` |
| 2  | `03-kpi-check.mp4` |
| 3  | `04-kanban.mp4` |
| 4  | `05-triage.mp4` |
| 5  | `06-checkpoints.mp4` |
| 6  | `07-commits.mp4` |
| 7  | `08-buyer-actions.mp4` |
| 8  | `09-overnight-agents.mp4` |
| 9  | `10-comms-agent.mp4` |
| 10 | `11-alert-queue.mp4` |
| 11 | `12-supplier-intel.mp4` |
| 12 | `13-wrapup.mp4` |

### Planner — David Chen (`planner/`)

| Step | Filename |
|------|----------|
| 0 | `01-arrival.mp4` |
| 1 | `02-kanban.mp4` |
| 2 | `03-drilldown.mp4` |
| 3 | `04-bom-cascade.mp4` |
| 4 | `05-demand-gap.mp4` |
| 5 | `06-simulation.mp4` |
| 6 | `07-validation.mp4` |
| 7 | `08-wrapup.mp4` |

### Plant Manager — Maria Gonzalez (`plant/`)

| Step | Filename |
|------|----------|
| 0 | `01-floor-walk.mp4` |
| 1 | `02-kpi-scan.mp4` |
| 2 | `03-kanban.mp4` |
| 3 | `04-critical-filter.mp4` |
| 4 | `05-root-cause.mp4` |
| 5 | `06-overnight-agents.mp4` |
| 6 | `07-escalations.mp4` |
| 7 | `08-wrapup.mp4` |

## Source narration

Each step's narration text is in `index.html` inside the persona scripts:
`DEMO_SCRIPT` (buyer), `DEMO_SCRIPT_PLANNER`, `DEMO_SCRIPT_PLANT`.
Use those exact lines as the HeyGen prompts so the spoken pacing matches
what the on-screen typewriter shows.

## Autoplay note

Browsers block autoplay with sound until the user has interacted with the
page. Demo entry happens via a button click, so this is normally fine. If
the first clip ever silently retries muted, that's the autoplay-policy
fallback firing — click the 🔊 button in the meeting frame to unmute.
