# Setup Guide — Customer Support Skill Pack

**Read this first.** This guide walks you through setting up the Customer Support Skill Pack on your own machine, in about 30 minutes. No technical background needed.

---

## What You're Building

A customer support bot on Telegram that:
- Answers your customers' questions in your brand voice
- Handles your FAQs instantly
- Escalates to you when it doesn't know the answer
- Logs every interaction so you can see what customers are asking

All for free. No subscriptions. You own it.

---

## Step 1 — Install Hermès Agent (5 min)

1. Go to the Hermès Agent website.
2. Download the installer for your OS (Windows, Mac, or Linux).
3. Run the installer.
4. Follow the setup wizard — it will ask you to choose an AI model provider.
   - **Free option:** Use Ollama (local LLM) — free, runs on your machine. The wizard will guide you.
   - **Paid option:** Use OpenAI, Anthropic, or any provider you prefer.
5. Finish setup. Hermès is now running.

**Note:** If you want free, choose the local model option. Hermès works with free local models.

---

## Step 2 — Create a Telegram Bot (2 min)

1. Open Telegram on your phone or computer.
2. Search for **@BotFather**.
3. Send `/newbot`.
4. BotFather asks for a name — give it your business name + "Bot" (e.g., "My Salon Bot").
5. BotFather asks for a username — must end in `bot` (e.g., `MySalonSupportBot`).
6. BotFather gives you an **API token**. Copy it. Keep it safe.

This is your bot. It's free. Anyone can create one.

---

## Step 3 — Connect the Bot to Hermès (5 min)

1. In Hermès, go to **Settings → Messaging → Telegram** (or **Channels → Telegram**).
2. Paste the **bot API token** you got from BotFather.
3. Add your **Telegram user ID** as an allowed user (so only you can manage the bot initially).
   - Search for **@userinfobot** on Telegram → it gives you your user ID. Copy it.
4. Save.
5. Restart the Hermès gateway (button in the dashboard, or say "restart gateway").
6. Test: open Telegram, find your bot, send "Hi". You should get a response from Hermès.

Your bot is now connected to Hermès.

---

## Step 4 — Add the Skill Pack (5 min)

1. Unzip the Customer Support Skill Pack you downloaded.
2. Copy the `product-01-digital-assets/` folder into your Hermès skills directory.
   - The skills directory is usually `~/.hermes/skills/` or inside your Hermès workspace.
3. In Hermès, say or run: "reload skills" or restart Hermès.
4. Verify the skills are loaded: ask Hermès "what skills do you have?" — you should see `skill-faq-handler`, `skill-customer-responder`, `skill-escalation`.

The skills are now available to your bot.

---

## Step 5 — Customize the Config (5 min)

1. Open `config.md` in a text editor.
2. Fill in:
   - **Business Name:** Your business name.
   - **Brand Voice:** Pick one of the options, or write your own.
   - **Escalation Contact:** Your Telegram username (so the bot can reach you when it escalates).
3. Save.

### Example config.md (filled in):

```
Business Name: My Salon
Brand Voice: Friendly and direct
Escalation Contact: @myself (my Telegram username)
Channel: Telegram
```

---

## Step 6 — Add Your FAQs (5 min)

1. Open `FAQ_LIST.md` in a text editor.
2. Replace the example FAQs with your actual FAQs.
3. Format: one row per FAQ, with keywords in the "Question" column and the answer in the "Answer" column.

### Example:

```
| prices, pricing, how much | Our services start at $50. Check our website or DM us for a custom quote. |
| opening hours, hours, when open | We're open Monday to Friday, 9am to 6pm. |
| location, where, address | We're at 123 Main Street, Suite 100. DM for parking info. |
| appointment, book, schedule | You can book via our website or DM us and we'll help you set one up. |
```

Add as many as you want. The more FAQs you add, the more the bot can answer on its own.

---

## Step 7 — Test the Bot (3 min)

1. Open Telegram, find your bot.
2. Send a message that matches an FAQ keyword. Example: "What are your prices?"
3. The bot should respond with the FAQ answer.
4. Send a message that's NOT in the FAQs. Example: "Do you offer refunds?"
5. The bot should respond in brand voice — or escalate to you if it doesn't know.
6. Check your Telegram — if it escalated, you should get a notification.

If everything works → the bot is live.

If something doesn't work → check the Hermès logs, or DM us for help.

---

## What to Do Next

- **Watch the logs** for the first few days. See what customers are asking.
- **Add FAQs** for the questions you see coming up repeatedly.
- **Refine the brand voice** if it doesn't sound right.
- **Adjust escalation rules** if the bot is escalating too much or not enough.

---

## Need Help?

DM us on Instagram @MystifyMe (or the contact in this guide). We respond.

---

*Version 1.0*  
*Mystify Me — Sulbha, CEO*
