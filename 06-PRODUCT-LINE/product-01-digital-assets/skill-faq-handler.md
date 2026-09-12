---
name: skill-faq-handler
description: >
  Answer common customer FAQs from a configurable list. When a customer asks a question that matches
  an FAQ entry, respond with the answer in the brand voice. When no match, escalate to the general
  responder (which may escalate further to a human).
  Invoke when: any inbound customer message arrives — this skill runs first to check for FAQ matches.
version: 1.0.0
---

# Skill: FAQ Handler

## Goal
Handle common customer questions instantly from a pre-written FAQ list. Fast, accurate, on-brand.

## How It Works

1. When a customer message arrives, check it against the FAQ list.
2. If the message matches an FAQ question (keyword match or close semantic match) → respond with the FAQ answer.
3. If no match → pass to the general responder (skill-customer-responder).
4. Always respond in the brand voice defined in `config.md`.

## FAQ List Format

The FAQ list lives in `FAQ_LIST.md` (in the same folder). Format:

```markdown
# FAQ List

| Question (keywords) | Answer |
|---|---|
| prices, pricing, how much | We offer skill packs starting at $29. Check the link in bio for current pricing. |
| setup, how to set up, install | Follow the setup guide included in your pack. It takes about 30 minutes. Message us if you get stuck. |
| refund, return, money back | We offer a 14-day refund if the skill doesn't work for your use case. DM us to request. |
| contact, reach, support | DM us on Instagram @MystifyMe or email support@mystifyme.com (replace with your contact). |
| ... | ... |
```

Add as many as you want. The skill checks if the customer's message contains any of the keywords in the "Question" column.

## Response Rules

- **FAQ match:** Respond with the answer. Keep it concise. In brand voice.
- **No match:** Pass to general responder. Don't answer from the FAQ list.
- **Multiple matches:** Use the closest match (most specific keywords). If ambiguous, ask the customer to clarify.

## Brand Voice

Defined in `config.md`. Examples:
- "Hi, I'm the Mystify Me assistant. Here's the answer to your question."
- "Great question! Here's what you need to know..."
- "I can help with that. Here's the info..."

Pick one voice and use it consistently. Defined in config.md so the customer can customize it.

## Escalation Trigger

If the FAQ answer says "escalate" or contains a marker like `[ESCALATE]`, don't answer — pass to the escalation skill immediately.

Example FAQ entry:
```
| urgent, emergency, broken, not working | [ESCALATE] |
```

## Log

After each response, log to `FAQ_LOG.md`:
- Timestamp
- Customer message (brief)
- Matched FAQ (if any)
- Response given (brief)
- Escalated? (yes/no)

Keep the log for 30 days, then rotate.

---

*Version 1.0*  
*Owner: Rhea, Skill Engineer — Mystify Me*
