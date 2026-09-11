---
name: windows-startup-launcher
description: >
  Windows Scheduled Task or Startup script that launches Hermes Agent when the laptop boots,
  ensuring the daily-kickoff cron can fire within minutes of power-on.
  Invoke when: setting up the laptop for the first time, or if Hermes isn't auto-starting.
version: 1.0.0
---

# Windows Startup Launcher for Hermes

## Goal
Make sure Hermes Agent starts automatically when the laptop turns on — so the daily-kickoff cron (every 5 min) fires within 5 minutes of boot, and the day's work begins without you touching anything.

## Why This Matters
Hermes's cron only runs while Hermes is running. If the laptop boots and Hermes isn't open, the cron never fires, and the startup-daily-kickoff never happens. This skill fixes that.

## Two Options

### Option A: Windows Task Scheduler (recommended — reliable, survives reboots)

1. Open **Task Scheduler** (search in Start menu).
2. Create a **Basic Task** named "Hermes Agent Startup".
3. Trigger: **When I log on** (or "When the computer starts" if you want it before login — but you'll need credentials stored).
4. Action: **Start a program**.
5. Program: path to Hermes executable (e.g., `C:\path\to\hermes.exe` or `python C:\path\to\run_agent.py`).
6. Start in: the Hermes working directory.
7. Finish. Test by running the task manually once.

#### Hidden/background option
- In Task Scheduler, check "Run whether user is logged on or not" + "Run with highest privileges" if you want it fully background.
- But for Hermes with UI, "Run only when user is logged on" is better.

### Option B: Startup Folder (simple — launches when you log in)

1. Press Win+R, type `shell:startup`, press Enter.
2. Create a shortcut to Hermes in that folder.
3. Hermes will launch every time you log in.

#### Shortcut target example:
```
"C:\Path\To\Hermes.exe" --no-splash  (if it has a flag to minimize)
```
Or a batch file that launches Hermes and minimizes:
```batch
@echo off
start "" "C:\Path\To\Hermes.exe"
exit
```

### Option C: Windows `schtasks` CLI (for Rhea to configure programmatically)

Rhea can run this command to create the task:
```cmd
schtasks /create /tn "HermesAgentStartup" /tr "C:\Path\To\Hermes.exe" /sc onlogon /ru "%USERNAME%"
```

Or for on-startup (before login):
```cmd
schtasks /create /tn "HermesAgentStartup" /tr "C:\Path\To\Hermes.exe" /sc onstart /ru "SYSTEM"
```

(Adjust paths and credentials as needed.)

## Verification

After setting up:
1. Reboot the laptop.
2. Log in (if on-logon trigger).
3. Wait 2 minutes.
4. Check if Hermes is running (Task Manager → Processes → Hermes, or check the UI).
5. Wait 5 more minutes (cron tick).
6. Check `08-OPERATIONS/task-board.md` — `last-kickoff-date` should be today.

## Fallback: Manual Start

If auto-start fails:
- Click the Hermes shortcut (desktop or start menu).
- Or run `hermes` in terminal.
- Then say: "run the startup-daily-kickoff skill now" — it'll execute immediately.

## Troubleshooting

### Hermes doesn't start on login
- Check Task Scheduler history — any error codes?
- Check the path to Hermes executable is correct.
- Check Hermes isn't being blocked by antivirus / firewall.

### Hermes starts but doesn't connect to anything
- Hermes may need a moment to initialize. The cron fires at :05, :10, etc. — give it at least 5 minutes.
- Check Hermes logs for connection errors.

### Cron doesn't fire even though Hermes is running
- Check Hermes cron is enabled in settings.
- Check the cron job `daily-kickoff-loop` exists and is active.
- Check `task-board.md` — if `last-kickoff-date` is today, it already ran (skip).

## Owner

- Rhea configures this (or Sulbha if she prefers manual setup).
- Sulbha decides: on-login vs on-startup trigger.

---

*Version 1.0*  
*Owner: Sulbha, CEO — Mystify Me*
