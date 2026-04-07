# Post-Trial Fix List — Makaronas

*Tactical fixes based on findings from the April 7 2026 student trial. See `APRIL7_REPORT.md` for the full analysis. This file is for fix tracking; vision-level work belongs in `ROADMAP.md`.*

---

## Priority 1 — `write_article` AI synthesis (Task 1)

**The problem.** When the AI evaluator requires both points (Petryla's mistake AND EduVault's 10-year retention) in a SINGLE message, students who cover them across multiple messages get trapped in a coaching loop. Real example from session `13426738`: student wrote both points across two messages, the Trickster kept asking them to "combine into one", student retried 12 times, ran out of time. Session `30abd776` literally has the student writing *"As jau parašiau zinute pakartok ka as parašiau arba padaryk tu"* — "I already wrote it, repeat what I wrote or do it yourself."

**The constraint we have to preserve.** The published message gets appended to Task 2's comment section as the student's "ŽINUTĖ" block. So we need ONE coherent text per session, not a chat log.

**The fix: AI synthesizes for the student.**
- When the dialogue (across discuss + write_article) shows both points have been mentioned, the Trickster composes the synthesis itself and shows it back: *"Gerai — jūsų žinutė draugams: '[synthesized text]'. Tai paskelbsime jūsų klasės draugams."*
- The student sees what gets published. They can accept or rewrite. No more "you combine it" loop.
- The synthesized text becomes the artifact saved to `session.generated_artifacts` and appended to Task 2.

**Files to touch:**
- `prompts/tasks/task-petryla-001/trickster_base.md` — rewrite the `write_article` section to instruct AI synthesis instead of demanding combined messages.
- `backend/ai/trickster.py` — verify the existing student_article artifact-saving path can accept an AI-generated synthesis (not just last student message).
- `content/tasks/task-petryla-001/task.json` — `evaluator_checklist` for `write_article` may need adjustment; the synthesis happens in the trickster turn, so the evaluator just needs to confirm the synthesis happened.

**Expected impact:** ~10 of the 20 stuck students would have completed Task 1. ~22% lift in Task 1 completion rate from a single prompt edit.

---

## Priority 2 — Task 1 redesign (investigation phase is the dropout point)

**The problem.** Task 1 takes a median of 17 minutes out of a 30-minute slot. The investigation tree phase is where students start dropping off — many never reach `discuss`, let alone `write_article`. The pre-dialogue phases (briefing + 2 articles + investigation tree) eat ~9 minutes alone.

**Vinga's call (post-trial, 2026-04-07):** Task 1 needs a full redesign, not just trimming. The investigation tree as currently built is too dense; 8 sources, multi-level expansion, students get lost.

**Open questions to answer before redesigning:**
- Should the investigation be 4 sources instead of 8?
- Should funding trails be revealed automatically as students click, instead of requiring source-marking?
- Should the two articles be replaced with shorter excerpts (or even just headlines + one key quote each)?
- Could the briefing image carry more of the narrative weight, replacing some intro text?
- Is there a way to keep the story but make the first interaction the AI dialogue (with the investigation as something the AI walks them through, instead of as a separate phase)?

**Until redesigned:** Task 1 is the bottleneck. Tasks 2-4 are likely 30-min-feasible as a set but we have no real timing data because so few students reached them. Vinga's instinct: in short slots, **drop Task 1 entirely** and start with Task 2.

---

## Priority 3 — Capture device type (DONE but worth noting)

**Status: shipped 2026-04-07.** GameSession now captures `user_agent` from the request header on session creation, and it flows into telemetry through all three save paths (task complete, session end, active dump). Will be available in the next trial's data.

This was missed in the April 7 trial — we have no idea which sessions came from phones vs tablets vs desktops, so we can't correlate device type with engagement patterns.

---

## Priority 4 — Measure timings for Tasks 2/3/4

**The problem.** Only 18 students reached Task 2, only 11 reached Task 3, only 4 reached Task 4. We have no reliable timing data for any of these. We need to know:
- How long does the comment-section + photo analysis (Task 2) actually take?
- Is the bot-network static visualization (Task 3) doing its job in <5 minutes or are students lingering?
- Does the deepfake video task (Task 4) finish in time?

**Fix:** Next trial, ensure at least some students get explicit time to reach Task 4 (maybe by skipping Task 1 entirely for one round, or running a 60-minute slot for one group). Then we can measure the full task budget honestly.

---

## Priority 5 — Failsafe button still locked at 30 exchanges

**Note:** The failsafe "Tęsti" button currently appears at 30 exchanges (changed from 3 before the April 7 trial). This was deliberate — Flash + the evaluator should drive normal transitions. After the trial, no student hit 30 exchanges in a single phase, so 30 is fine. Leaving as-is.

---

## Done

- [x] **Bank statement hallucination in session report** — fixed by removing hardcoded task sequence and pulling from `session.task_history`. Shipped before the trial.
- [x] **User-Agent capture** — shipped 2026-04-07.
- [x] **Static task telemetry (Task 3)** — fixed in `/next` endpoint to capture static task completions. Shipped before the trial.
- [x] **`download-sessions` admin endpoint** — shipped before the trial. Used successfully to pull all 93 sessions after testing.

---

*Last updated: 2026-04-07*
