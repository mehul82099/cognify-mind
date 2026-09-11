# Agent Team Roster — Mystify Me

**Team Lead:** Sulbha (CEO)  
**Structure:** Each agent is a role with a soulfile, a task list, and a delegation lane.

---

## Roster

| Agent | Role | Soulfile | Primary Output |
|---|---|---|---|
| **Sulbha** | CEO / Strategist | `sulbha.soul.md` | Vision, priorities, final decisions, public face |
| **Rhea** | Skill Engineer | `rhea.soul.md` | Skills, automations, technical architecture |
| **Nina** | Content Creator | `nina.soul.md` | YouTube videos, Instagram posts, scripts, thumbnails |
| **Kai** | Research & Trends | `kai.soul.md` | Market research, trend spotting, competitor analysis |
| **Maya** | Customer & Community | `maya.soul.md` | Customer responses, community engagement, testimonials |
| **Zara** | Voice & UX | `zara.soul.md` | Voice cloning, TTS, chatbot UX, audio content |

---

## Agent Deployment

- **Each agent** is a persona within Hermes (or a separate Hermes container if scaling).
- **Soulfile** = the agent's personality, rules, and priorities. Loaded at session start.
- **Agent tasks** = ongoing responsibilities + one-off assignments from Sulbha.
- **Delegation** = Sulbha assigns → agent executes → reports back → Sulbha consolidates.

---

## How Agents work together

```
Sulbha (CEO)
  ├── assigns vision/priority → Rhea (build it)
  ├── assigns content topic → Nina (make it)
  ├── assigns research → Kai (find it)
  ├── assigns customer issue → Maya (handle it)
  └── assigns voice/UX ask → Zara (design it)

Nina (Content) ← gets scripts from Kai (research) + assets from Zara (voice/images)
Maya (Community) ← gets responses from Sulbha (brand voice) + product info from Rhea
Zara (Voice) ← gets scripts from Nina + customer FAQs from Maya
```

---

## Soulfile Template

Each soulfile contains:
1. **Who they are** — name, role, personality
2. **What they care about** — priorities, values
3. **How they work** — style, rules, tools they use
4. **How they report** — format, frequency, what Sulbha needs from them
5. **What they don't do** — boundaries, escalation path

---

*Last updated: 2026-09-12*  
*Owner: Sulbha, CEO — Mystify Me*
