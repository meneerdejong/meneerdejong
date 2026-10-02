# PitCrew research: what makes sim racers faster

PitCrew exists to make its users better drivers. This document distils the coaching content of two creators whose audiences overlap with ours, and turns it into product requirements PitCrew can measure and coach on.

| Creator | Focus | Core belief |
|---|---|---|
| [SimRacing Arnout](https://www.youtube.com/@SimracingArnout) (Arnout Hoekstra) | Car setup, vehicle dynamics, mindset. Sells setups in five skill levels and *The Art of Car Setups*. | A predictable car frees the driver to learn. Drive at 90% on purpose. |
| [Suellio Almeida](https://www.youtube.com/@SuellioAlmeida) (Almeida Racing Academy) | Driving technique and motor learning. Has coached 12,000+ students, wrote *The Motor Racing Book* and *The Motor Racing Checklist*. | "Speed is a byproduct of control." You can't set up your way around bad technique. |

> **Method note.** YouTube and both creators' own sites are blocked from the research environment, so this is built from search-indexed excerpts of their videos, Substack posts, course pages and books (see [Sources](#sources)). Treat the quotes as paraphrases. Before we ship any coaching copy that cites them, someone should check it against the original videos.

---

## 1. Where the two creators agree

1. **Consistency comes before speed.** Suellio: hit the same brake point, turn-in and throttle point every lap. Arnout names "one-lap pace, zero consistency" as problem #1. Both want repeatable laps first and treat lap time as what follows.
2. **Overdriving is the default failure.** Arnout: trying harder means more steering, more corrections and tunnel vision. Suellio: an over-slowed car means too much brake, and a snappy car means too much steering, so relax the hands.
3. **Exit speed beats entry heroics.** Arnout: brake earlier, release earlier and get to full throttle sooner. Suellio: smooth means no wasted movement, not slow.
4. **Train one thing at a time.** Suellio does 5–10 laps on a single skill and ignores lap time. Arnout changes one setup item at a time and feels the result.
5. **Confidence is built, not felt.** Arnout says confidence means knowing what happens next, and you get there by repetition. Suellio says bad habits live in subconscious muscle memory and only drills overwrite them.

## 2. Skill model

PitCrew should coach along these axes. The pillars come from Suellio's checklist modules (Vision, Braking, Balance/Consistency) and his "three tools for rotation". The car-side axis comes from Arnout.

| Skill | What "good" looks like | Typical fault |
|---|---|---|
| **Vision** | Eyes on the next reference point before the current one is reached | Looking just past the bumper or at the apex, which makes inputs late and jerky |
| **Braking** | Late, hard initial pressure, then a progressive release | Brake point varies lap to lap, or pressure is too low for too long (over-slowing) |
| **Trail braking / rotation** | Brake release matched to rising steering angle, which keeps the fronts loaded | Releasing before turn-in (no trail), or too much steering while trailing (snap) |
| **Rotation tools** | Uses steering, engine braking and trail braking on purpose | Relies on steering alone, which leads to understeer |
| **Throttle** | Progressive application, especially in high-torque or oversteer-prone cars | Hammered throttle on exit, so the car snaps or pushes wide |
| **Consistency** | Small lap-to-lap spread over 10 laps | One fast lap and then scatter |
| **Racecraft & mind** | Same lines with a car behind; driving at about 90% | Mirror-driving, frustration, collisions from pushing |
| **Car understanding** | Can read understeer and oversteer and fix them with setup | Fighting a twitchy "esport" setup they can't drive yet |

## 3. Telemetry signals PitCrew can detect

The coaching above maps to signals we can compute from standard telemetry (speed, throttle, brake, steering, gear, lap distance, wheel slip and yaw where available).

| Signal | Computation | Coaching trigger |
|---|---|---|
| Brake-point scatter | σ of brake-onset distance per corner across clean laps | σ above threshold → consistency drill for that corner |
| Trail overlap | Overlap of brake > 0 with rising \|steer\| after turn-in | Overlap near 0 → "no trail braking" lesson |
| Over-slowing | Minimum corner speed below the driver's best (or a reference) while peak brake ran long | "Braking too hard / too long" |
| Snap risk | Yaw-rate or counter-steer spikes during the brake release | "Too much steering while trailing — relax your hands" |
| Steering corrections | Count of steering-direction reversals per corner | High count → overdriving flag |
| Coasting | Time with throttle and brake both ≈ 0 | Indecision between phases |
| Throttle progression | Max d(throttle)/dt on exit and time from apex to full throttle | Jerky exit, or full throttle arriving late |
| Exit speed | Speed at a fixed distance past the apex compared with the best lap | The main lap-time lever per Arnout |
| Lap spread | σ and range of the last *n* clean laps | Feeds a consistency score and challenge mode |
| Traffic delta | Sector time with a car within X m behind compared with clean air | "Losing time under pressure" insight |

## 4. Training formats to build

These are taken directly from the creators' methods.

- **Single-skill sessions.** Pick one skill, run 5–10 laps, hide the lap timer and score only that skill (Suellio's deliberate practice).
- **Consistency Challenge.** Run 10 consecutive laps under a target time with a semi-difficult car. The streak resets on a miss (Suellio's Consistency Challenge).
- **90% mode.** Give the driver a pace target a few tenths off their best. The reward is a lower correction count and a smaller spread, not a faster time (Arnout).
- **New-track protocol.** Run a structured first stint: half-throttle lateral grip test, then find brake points progressively, then build consistency, with no crashing or guessing (Suellio).
- **Brake → release ladder.** Start with straight-line braking, then add trail on one corner, then extend it across the lap, with each step gated by a measured trail overlap.
- **Setup ladder.** Recommend setups from stable (L1) to aggressive (L5) based on the driver's consistency and snap-risk metrics. Move up only when the driver can control the current level (Arnout's five skill levels).

## 5. Product principles

1. **Diagnose one thing at a time.** Each session ends with a single focus item, not a list of 12.
2. **Reward control over pace.** The headline score is consistency and input quality, and lap time sits underneath it.
3. **Say what to do, not what is wrong.** "Release brake 10 m later into T3", not "bad trail braking".
4. **Account for the car.** Many symptoms are setup problems, such as oversteer from rake. Flag them as such so drivers stop fighting the car.
5. **Coach the mind too.** Spot frustration patterns (spinning after a bad lap, worse sectors with traffic) and suggest a reset or 90% mode.

## Sources

**SimRacing Arnout**
- [YouTube channel](https://www.youtube.com/@SimracingArnout) · [Patreon](https://www.patreon.com/SimracingArnout) · [Substack](https://arnouthoekstra.substack.com)
- [10 problems every simracer runs into](https://arnouthoekstra.substack.com/p/10-problems-every-simracer-runs-into)
- [Pushing Too Hard](https://arnouthoekstra.substack.com/p/pushing-too-hard)
- [Esport Setups Kill Progress](https://arnouthoekstra.substack.com/p/esport-setups-kill-progress)
- [Fast, safe and dangerous car setups](https://arnouthoekstra.substack.com/p/fast-safe-and-dangerous-car-setups)
- [Arnout's Car Setup Model](https://arnouthoekstra.substack.com/p/arnouts-car-setup-model)
- [Confidence is Built, Not Felt](https://arnouthoekstra.substack.com/p/confidence-is-built-not-felt)
- [When you stop improving](https://arnouthoekstra.substack.com/p/when-you-stop-improving)
- [Simracing Frustration](https://arnouthoekstra.substack.com/p/simracing-frustration)
- [How to achieve faster lap times](https://arnouthoekstra.substack.com/p/how-to-achieve-faster-lap-times-in)
- [Where does your oversteer come from?](https://arnouthoekstra.substack.com/p/where-does-your-oversteer-come-from)

**Suellio Almeida**
- [YouTube channel](https://www.youtube.com/@SuellioAlmeida) · [Almeida Racing Academy](https://almeidaracingacademy.com/)
- [Trail Braking lesson](https://almeidaracingacademy.com/sim-racing/learn/lessons/trail-braking) · [5 Steps to Master Trail Braking](https://almeidaracingacademy.com/blog/5-steps-finally-master-trail-braking-sim-racing)
- [50 Sim Racing Mistakes (blog)](https://almeidaracingacademy.com/blog/50-sim-racing-mistakes-killing-lap-times-fix-them) · [video](https://www.youtube.com/watch?v=51Dw_vhcUBA)
- [The Only Training Method That Actually Works](https://almeidaracingacademy.com/blog/get-better-racing-only-training-method-actually)
- [How to Quickly Learn a New Track](https://almeidaracingacademy.com/sim-racing/learn/lessons/how-to-quickly-learn-a-new-track)
- [Consistency Challenge 2](https://almeidaracingacademy.com/sim-racing/learn/lessons/consistency-challenge-2)
- [Motor Racing Checklist course](https://suellioalmeida.samcart.com/products/motor-racing-checklist-course/)
- [The Motor Racing Book, Vol. 1 (quotes)](https://www.goodreads.com/work/quotes/204056521)
- [TikTok: trail braking](https://www.tiktok.com/@suellioalmeida/video/7331135067957251333)
- [Drivesport podcast interview](https://drivesport.buzzsprout.com/2501255/episodes/18187810-how-sim-training-accelerates-real-world-driving-skills-with-suellio-almeida)
