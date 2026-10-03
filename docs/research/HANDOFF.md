# Handoff: driving-coaching research

This research started in a cloud session attached to the wrong repository (`meneerdejong/meneerdejong`). Give this file to a new Claude session in the PitCrew project so it can carry on.

## Goal

PitCrew's purpose is to improve its users' driving skills. The research turns the coaching content of [SimRacing Arnout](https://www.youtube.com/@SimracingArnout) and [Suellio Almeida](https://www.youtube.com/@SuellioAlmeida) into a skill model, telemetry-detectable faults, drills and product principles.

## What was done

- Listed both channels in full (217 + 204 videos). Kept the 235 videos about driving skill and downloaded English transcripts for 219 of them with `yt-dlp`.
- Read 58 transcripts in full with timestamps, and searched the rest by theme.
- Wrote the findings with every claim linked to the second of video it comes from.
- After a while YouTube started blocking caption downloads from the cloud server with a bot check. Transcripts for 19 relevant videos are still missing and will be exported locally.

The raw transcripts lived in the cloud session's scratch space and were not kept. They are the creators' copyrighted text, so only paraphrased notes are stored here.

## Files

| File | Contents |
|---|---|
| `driving-coaching.md` | Main research doc: 10 key findings, how the two channels differ, skill ladders, technique model, a catalogue of 22 faults with telemetry signatures, a library of 14 drills, how to practise, mindset and racecraft, pre-flight hardware checks, product implications, gaps |
| `video-notes.md` | Per-video notes (58 videos) with timestamps |
| `transcript-requests/README.md` | How to export transcripts locally with `yt-dlp`, plus lists of every requested video |
| `transcript-requests/missing-arnout-suellio.txt` | The 19 missing Suellio videos, including *I Mapped Out Every Skill* and *Roadmap to Top 1%* |
| `transcript-requests/track-guides-*.txt` | 553 track guides from other creators: LMU 239, ACC 57, iRacing 247, Driver61 real-world 10 |

## Next steps

1. Export `.vtt` transcripts locally for `missing-arnout-suellio.txt`, then for the LMU and ACC track-guide lists (the command is in `transcript-requests/README.md`).
2. Fold the 19 missing videos into `driving-coaching.md`, above all Suellio's full skill order.
3. Mine the track guides for per-corner reference data PitCrew can use: brake markers, gears, apex speeds, and the common mistakes for each corner.
4. Calibrate the fault-catalogue thresholds (§5 of `driving-coaching.md`) against real user telemetry.
