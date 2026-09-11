---
name: configure-startup-kickoff
description: >
  Set up the startup-daily-kickoff skill to run automatically when Hermes (and the laptop) starts.
  Configures Hermes cron, creates a startup marker file, and tests the skill.
  Invoke when: first time setup, or when the cron needs reconfiguration.
version: 1.0.0
---

# Configure Startup Daily Kickoff

## Goal
Make it so that when the laptop turns on and Hermes boots, the daily kickoff skill runs automatically — no manual trigger needed.

## How It Works (Hermes Cron)

Hermes has a built-in cron system. We'll use it to run `startup-daily-kickoff` every 5 minutes. The skill itself checks "has it already run today?" and skips if yes. This means:

- Laptop off overnight → turns on in the morning → Hermes boots → within 5 minutes, kickoff runs.
- Laptop already on → kickoff ran at first cron tick after midnight (or first boot of the day).

## Setup Steps

### Step 1: Verify the skill exists
1. Check that `04-SKILLS-LIBRARY/skills/startup-daily-kickoff/skill.md` exists in Cognify Mind.
2. If not, build it first (see that skill's README).

### Step 2: Create the cron job in Hermes
In Hermes (CLI or dashboard):

1. Say: "create a cron job that runs every 5 minutes"
2. Prompt: "run the startup-daily-kickoff skill"
3. Hermes will create the cron. Confirm it shows in the cron list.

Alternatively, if Hermes has a direct cron-create command:
- Name: `daily-kickoff-loop`
- Interval: every 5 minutes
- Action: `run-skill startup-daily-kickoff`

### Step 3: Test the cron
1. Wait 5 minutes (or trigger manually if Hermes allows).
2. Check `08-OPERATIONS/task-board.md` — should have a `last-kickoff-date` set.
3. Check `00-CE-OVERSIGHT/ce-daily-brief.md` — should have today's brief.
4. If both exist, the cron is working.

### Step 4: Verify auto-start behavior
1. Restart Hermes (or reboot laptop).
2. Wait 5–10 minutes after Hermes comes back up.
3. Check `last-kickoff-date` — should be today.
4. If yes: the startup trigger works.

## Manual Trigger (fallback)

If the cron isn't working or you want to force a kickoff:
- Say: "run the startup-daily-kickoff skill now"
- Hermes executes it immediately, regardless of cron.

Use this when:
- You just turned on the laptop and don't want to wait 5 minutes.
- The cron failed and you want to re-run.
- You're testing the skill.

## Cron Configuration Reference

```
Cron name: daily-kickoff-loop
Schedule: every 5 minutes (or at :00, :05, :10, ... :55)
Skill: startup-daily-kickoff
Max runtime: 30 minutes (kill if stuck)
Log: yes (Hermes cron logs)
```

## What Gets Created

| File | Purpose |
|---|---|
| `08-OPERATIONS/task-board.md` | Stores `last-kickoff-date` + daily task list |
| `00-CE-OVERSIGHT/ce-daily-brief.md` | CEO's daily 3-bullet brief |
| `05-CONTENT-STRATEGY/content-calendar.md` | Today's content schedule (if applicable) |
| Cron job in Hermes | The actual trigger mechanism |

## Troubleshooting

### Cron doesn't fire after laptop restart
- Check Hermes is set to start on login (Windows: Task Scheduler or Startup folder).
- Check Hermes cron is enabled (some setups require cron service to be running).
- Check network — if Hermes needs internet for any step, a disconnected laptop won't run it.

### Skill runs but does nothing
- Check `task-board.md` — does `last-kickoff-date` say today? If yes, it skipped (as designed). Delete that line and re-run to test.
- Check Hermes logs — any errors when running the skill?

### Cron runs but skill errors
- Read the error in Hermes logs.
- Common issue: skill references a file that doesn't exist yet (e.g., `task-board.md` not created). Fix the missing file.

## Owner

- Sulbha (CEO) owns the cron configuration.
- Rhea owns the skill itself.
- If cron setup fails, escalate to Sulbha.

---

*Version 1.0*  
*Owner: Sulbha, CEO — Mystify Me*
