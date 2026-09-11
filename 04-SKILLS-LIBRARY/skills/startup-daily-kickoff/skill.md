---
name: startup-daily-kickoff
description: >
  Fires when Hermes starts (laptop turns on). Reads the task board, picks today's priorities,
  and executes the daily launch sequence. Runs once per day, first thing.
  Invoke when: Hermes starts up, or manually when you want to start the day's work.
version: 1.0.0
---

# Startup Daily Kickoff

## Goal
When the laptop turns on and Hermes boots, automatically begin the day's work — check priorities, build what's queued, post content if it's a content day, log everything.

## Trigger Logic

### Automatic (recommended)
- Set a cron to run this skill every 5 minutes.
- The skill checks: has it already run today? If yes, skip. If no, execute.
- This way, the moment the laptop turns on and Hermes is alive, the daily work begins within 5 minutes.

### Manual
- Invoke the skill directly: "run the startup daily kickoff" — same effect, no cron needed.

## Steps

### 1. Check if already run today
1. Read `08-OPERATIONS/task-board.md` — look for a `last-kickoff-date` field.
2. If `last-kickoff-date` == today's date → **SKIP** (already done). Log "skip: already kicked off today."
3. If not set or not today → proceed.

### 2. Read today's priorities
1. Read `08-OPERATIONS/task-board.md`.
2. Find entries marked for today (or unmarked = do next).
3. Order by priority: CEO-priority first, then Rhea tasks, then Nina tasks, then others.
4. Load the day's content calendar from `05-CONTENT-STRATEGY/content-calendar.md` if it's a content day.

### 3. Execute the daily sequence

#### CEO check-in (Sulbha)
1. Review the priority matrix in `00-CE-OVERSIGHT/ce-priority-matrix.md`.
2. Confirm today's #1 priority. If nothing is set, default to: "build or ship one product thing."
3. Write a 3-bullet brief to `00-CE-OVERSIGHT/ce-daily-brief.md`:
   - What we built/shipped yesterday
   - What we're doing today
   - Any blockers

#### Build / Ship (Rhea)
1. Read `08-OPERATIONS/task-board.md` for Rhea's tasks.
2. Pick the highest-priority build task.
3. Execute: create/update the skill, config, or product asset.
4. Commit to Cognify Mind repo.
5. Log completion in task-board.md.

#### Content (Nina)
1. Check `05-CONTENT-STRATEGY/content-calendar.md` — is today a content day?
2. If yes: post the scheduled content (Instagram + YouTube as applicable).
3. If no content scheduled: create one piece of "build in public" content (what we worked on yesterday).
4. Engage with comments for 30 minutes after posting.
5. Log post + metrics in `10-CONTENT-ARCHIVE/engagement-logs/`.

#### Research (Kai)
1. Run a quick scan: YouTube top 5 AI agent videos (upload date), Twitter/X search, Reddit top posts.
2. Write a 5-bullet trend brief to `09-KNOWLEDGE-BASE/case-studies/daily-trends.md`.
3. Flag anything urgent to Sulbha.

#### Community (Maya)
1. Check Instagram DMs, YouTube comments, Discord — any customer questions?
2. Respond to all. Log interesting patterns in `07-CUSTOMERS-COMMUNITY/community-building.md`.
3. If a customer needs help with a skill pack: escalate to Rhea.

#### Voice / UX (Zara)
1. If a voice-related task is queued: work on it (TTS test, voice clone update, chatbot voice flow).
2. Log progress.

### 4. Set today's kickoff marker
1. Write `last-kickoff-date: <today>` to `08-OPERATIONS/task-board.md`.
2. Commit all changes to Cognify Mind repo.

### 5. Post a "daily status" (optional, for build-in-public)
1. Compose a short Instagram story / post: "Day started. Working on: <today's priority>. Follow along."
2. Post to Telegram channel if one exists.
3. This keeps the public engaged even on "quiet" days.

## Rules

- **Run once per day.** The `last-kickoff-date` check prevents duplicate runs.
- **Don't skip CEO check-in.** Even on quiet days, Sulbha sets the priority.
- **If a task is blocked,** log the blocker and move to the next task. Don't stall the whole day.
- **Commit often.** Every completed task = a commit to Cognify Mind.
- **Keep it under 30 minutes** for the kickoff itself. The rest of the day is deeper work.

## What This Skill Does NOT Do

- It does not do deep creative work (that's the rest of the day).
- It does not post multiple times (one "day started" post is enough).
- It does not make strategic decisions (Sulbha does that in the check-in).

## Example Daily Output

```
Daily Kickoff — 2026-09-13
Priority: Build Customer Support Skill Pack v1
CEO brief: 3 bullets written
Rhea: Building skill-customer-responder.md
Nina: No content day — will post "build in progress" later
Kai: Trend brief written, no urgent flags
Maya: 2 customer questions answered
Zara: No voice task queued
Status: Tasks logged, repo committed, ready for deep work.
```

---

*Version 1.0*  
*Owner: Sulbha, CEO — Mystify Me*
