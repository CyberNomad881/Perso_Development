# CLAUDE.md: standing laws for every Claude session on Project 801 (Ritmonaut / Danstellation / Nebula)

These laws are mandatory. Tamer set them on 21 Nov 2026 and they sit above every other working habit. The halt of
21 Nov 2026 (work stopped while Tamer's PC was offline: the weekly regression gave up after one retry, the 1-vs-5 work
and the listening page waited) was the **last non-compliance**. Any future idle stretch is a breach and is logged the
same day as an `incident` row.

Full operating rule, mechanisms and the non-compliance record: `salsa/kaizen/NO_HALT.md` in the project's shared folder
(`C:\Projects\project801\kaizen\NO_HALT.md` on the PC). Tamer's RSI rules:
`C:\Projects\project801\continuous-improvement-rules.md` (§7, §10.8).

## 1. Primary law: continuous improvement never stops
- No thread, coordinator, scheduled task or worker leaves work on hold while waiting for Tamer, his PC, or a reply.
- While a question is open, work everything that does not depend on the answer: research, search, design, analysis,
  building, testing, preparing scripts so a blocked step runs in one go later.
- Only the single step that truly needs Tamer's yes waits: downloads, installs on his PC, purchases, sending data out
  of the project, shared-resource changes.
- Never end a turn with nothing running unless the whole plan is done. At every hand-back, say what is running now
  and what starts next.

## 2. When the PC is offline (the cause of the 21 Nov halt)
- Say so in one line and, **in the same turn**, take the top open item of `salsa/kaizen/CLOUD_BACKLOG.md` (ranked
  cloud-only work) and start it.
- Retry the PC by scheduled check-in with backoff (15 min, 30 min, 1 h, then hourly, as in RSI rules §7; at most
  once overnight 22:00-08:00 Geneva) until it succeeds. Never "stop retrying" or "leave it for next week". A check-in runs beside
  work, never instead of it.
- PC-side steps live in `salsa/kaizen/standstill/pc_queue/` (one resumable command), ready to run the moment the PC
  is back.

## 3. When the PC comes back
- First run the PC queue (`run_queue.py dry`, then `run`; CPU, no installs, no downloads), then mirror the audio it
  extracts to the cloud (`/mnt/project-files/salsa/audio_mirror/`, with a README) so the next offline period blocks
  nothing. Then sync results both ways with `C:\Projects\project801`.

## 4. Problem-solving law
- If work looks stalled, immediately launch a problem-definition step: several independent agents (different lenses)
  name the main problems causing the standstill.
- Then a solution step: several agents propose AND test fixes, with pre-registered pass lines and controls.
- Keep going until the problem is solved in fact and in practice, not just researched.
- Track every step with `python kaizen/kaizen_log.py event improvement_log.jsonl --type problem|result|incident
  --problem ... --hypothesis ... --action ... --result ... --next ...`, then `render` to `IMPROVEMENT_LOG.md`.

## 5. Questions to Tamer
- Every question is framed around the most useful next step, carries a recommendation, and the recommended option
  (if reversible) is built while he decides.

## 6. Reporting
- Every result states its statistics: data used (songs, clips, bars, minutes), answered vs skipped, and confidence
  given the sample size. Every claim carries its tier (🟢 proven, 🟡 observed, 🔴 reasoned).
- Long jobs (over about 2 minutes) write `progress.json`; a run without it is not reported as complete.

## 7. Self-check before ending any turn
"Is there any work that does not need Tamer's yes that I could start now?" If yes, start it. If the only blocker is a
device, schedule the next check and keep cloud work running.

## 8. Shared resources and standing rules
- Ask before installing anything on Tamer's PC. Ollama is shared with Hermes: read
  `C:\hermes_agent\notes\ollama-shared-models-brief.md` first (no pulls, deletes or container changes); restore
  gemma4:openclaw-8k and Chatterbox afterwards.
- Hermes runs weekdays 09:00-18:30 Geneva; outside those hours (and at weekends) the dance pipeline may keep its models
  in VRAM for the whole session and restore gemma and Chatterbox when done for the day.
- Keep files in sync between the project's shared folder / cloud sessions and `C:\Projects\project801`; a failed sync
  is fixed and finished, never deferred.
- Pre-register tests (sha256 + date) in `kaizen/TESTS.md`; adopt only on a 🟢 holdout result.
- Commits carry the owner's identity (CyberNomad881) and no AI attribution (RSI rules §6).
- Frame work around the three pillars: pattern recognition, prediction, creation.
