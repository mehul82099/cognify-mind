---
name: skill-escalation
description: >
  Detects when a customer question should be escalated to a human and routes it.
  Invoke when: the customer responder determines the question is beyond the bot's knowledge,
  the customer is frustrated, or the customer asks for a human.
version: 1.0.0
---

# Skill: Escalation Handler

## Goal
When the bot can't help, escalate gracefully. Get a human involved with full context, and keep the customer informed.

## How It Works

1. Triggered by the customer responder when escalation conditions are met.
2. Read escalation config from `config.md` (who to escalate to, how, what channel).
3. Compose an escalation message to the human:
   - Customer's original message
   - Why it's being escalated (the trigger)
   - What the bot already tried (if anything)
   - Customer's contact info (if available)
4. Send the escalation to the human (via Telegram, email, or configured channel).
5. Send a message to the customer:
   - Acknowledge the request
   - Say a human is being connected
   - Give an ETA if possible (e.g., "within a few minutes")
   - Keep the channel open (don't close the conversation)
6. Log the escalation in `ESCALATION_LOG.md`.

## Escalation Triggers

This skill is invoked when:

| Trigger | Example |
|---|---|
| Question not in bot's knowledge | "Do you offer a money-back guarantee?" (not in FAQ) |
| Customer frustrated/angry | "This isn't working at all. I want a refund now." |
| Customer asks for human | "I want to talk to a real person." |
| Complex request | "I need you to process this return and issue a new order." |
| Bot gave a wrong answer (detected) | Customer says "that's not right" after a bot response |

## Escalation Message to Human (template)

```
ESCALATION — Mystify Me Customer Bot

Customer: <name or Telegram ID>
Channel: Telegram
Time: <timestamp>

Customer message:
"<original message>"

Why escalated: <trigger reason>

Bot already said: <brief summary of what the bot responded, if anything>

Please respond. The customer is waiting.
```

## Customer-Facing Escalation Message (template)

```
Thanks for your patience. I'm connecting you with a human who can help with that directly.

They should be with you in a few minutes. In the meantime, is there anything else I can help with?
```

Or shorter:
```
Let me get a human on this for you. Someone will be with you shortly.
```

## ETA Rules

- If the human is online and responsive: "They're looking at this now."
- If unsure: "within a few minutes" (don't overpromise).
- If after hours: "A human will get back to you within a few hours. We appreciate your patience."

The ETA should be honest. Don't say "a few minutes" if the human is asleep.

## Log

After escalating, log to `ESCALATION_LOG.md`:
- Timestamp
- Customer identifier
- Trigger reason
- Human notified? (yes/no)
- Human response received? (yes/no / pending)
- Resolved? (yes/no / pending)

Keep escalations for 30 days, then archive.

## Rules

- **Always tell the customer what's happening.** Don't just go silent.
- **Always give context to the human.** The human should know what the customer asked and why it's escalated.
- **Don't escalate everything.** Only when the bot genuinely can't help or the situation demands it.
- **If the human doesn't respond within the ETA,** follow up once. If still no response, let the customer know and offer to take a message.

---

*Version 1.0*  
*Owner: Rhea, Skill Engineer — Mystify Me*
