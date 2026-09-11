# Free Toolchain — Mystify Me

**Commitment:** Zero subscriptions. Every capability must have a free, open-source, or free-tier alternative.

---

## Video Production

| Task | Free Tool |
|---|---|
| Scripting | Own LLMs (local) + this repo's prompt library |
| Stock footage | Pexels, Pixabay, Mixkit (all free, no attribution required) |
| Screen recording | OBS Studio (free, open-source) |
| Video editing | DaVinci Resolve (free version), Shotcut (open-source), OpenShot |
| Subtitles/captions | Whisper.cpp (local) for transcription + Aegisub or Shotcut for captions |
| Thumbnail images | Canva free tier, GIMP (open-source) |
| Voiceover | Open-source TTS (see Voice section) |
| Video export | Any of the above editors |

### Notes
- DaVinci Resolve free version is fully functional for 99% of creators.
- OBS + Whisper.cpp for captions = full free captioning pipeline.
- Pexels/Pixabay API available for programmatic stock footage retrieval.

---

## Image Generation & Design

| Task | Free Tool |
|---|---|
| AI image generation | Stable Diffusion (local via Automatic1111 / ComfyUI), FLUX.1-schnell (open weights), Hugging Face free inference for some models |
| Design/Canva alternative | Canva free tier, GIMP, InkWell |
| Logos/icons | SVG-edit, Figma free tier, GIMP |
| Stock photos | Pexels, Pixabay, Unsplash (all free) |
| Image editing | GIMP, Photopea (browser, free) |

### Notes
- Run Stable Diffusion locally if GPU available; otherwise use free Hugging Face spaces.
- FLUX.1-schnell is open-weight and runs locally.
- Canva free tier sufficient for thumbnails, social posts, basic branding.

---

## Voice & Speech

| Task | Free Tool |
|---|---|
| Text-to-Speech (TTS) | Coqui TTS (open-source), Piper TTS (fast, local), Silero TTS, Bark (open-source), OpenVoice |
| Voice cloning | OpenVoice (open-source), Coqui TTS voice conversion, YourTTS |
| Speech-to-Text (transcription) | Whisper.cpp (local, fast), OpenAI Whisper (open-source), Vosk (offline) |
| Voice editing | Audacity (free, open-source) |
| Audio cleanup | Audacity, RNNoise (noise suppression) |

### Notes
- **Coqui TTS** is the primary recommendation — supports voice cloning, multi-language, runs locally.
- **Piper TTS** is extremely fast for real-time use, runs on CPU.
- **Whisper.cpp** for transcription — runs locally, fast, no API cost.
- Voice cloning: OpenVoice can clone from short samples. Coqui TTS has voice conversion.
- All processing local = no per-character API fees.

---

## Code & Agent Logic

| Task | Free Tool |
|---|---|
| LLM inference (local) | Ollama (run Llama, Mistral, Qwen, etc. locally), LM Studio, llama.cpp |
| Online free LLM tiers | Hugging Face Inference API (free tier), Google Gemini free tier, Perplexity free |
| Code generation | Any of the above LLMs |
| Agent framework | Hermes Agent (open-source, MIT), AutoGen, CrewAI (open-source) |
| Browser automation | Playwright (open-source), Selenium |
| Web scraping | curl, Python requests + BeautifulSoup, yt-dlp for video metadata |

### Notes
- **Ollama** is the primary local LLM runner — pull models once, run forever, zero API cost.
- Hermes Agent itself is open-source (MIT) and free.
- Free online tiers (Gemini, Hugging Face) have rate limits but cost nothing.
- For YouTube: yt-dlp for metadata, youtube-transcript-api (Python) for transcripts.

---

## Hosting & Infrastructure

| Task | Free Tool |
|---|---|
| Static site / portfolio | GitHub Pages (free), Vercel (free tier), Netlify (free tier) |
| Backend / API | Render (free tier), Railway (trial), Python anywhere (free tier) |
| Database | SQLite (local), Supabase free tier, Firebase free tier |
| File storage | GitHub LFS (limited), local storage, Google Drive free |
| Domain | Free subdomains (GitHub Pages, Vercel, etc.), cheap .xyz domains (~$1/yr) |
| Cron / scheduling | GitHub Actions (free minutes), local cron, Hermes built-in cron |

### Notes
- GitHub Pages for Mystify Me portfolio / landing page — free, looks professional.
- Render free tier for any backend services.
- Hermes Agent cron for all scheduled tasks — no external scheduler needed.

---

## Marketing & Distribution

| Task | Free Tool |
|---|---|
| Social media posting | Instagram (free), YouTube (free), Twitter/X (free), LinkedIn (free) |
| Scheduling | Native platform schedulers, Buffer free tier (limited) |
| Analytics | Instagram Insights (free), YouTube Analytics (free), Google Analytics (free) |
| Community | Instagram comments/DMs, YouTube comments, Discord (free), Telegram (free) |
| Email list | Mailchimp free tier (up to 500 contacts), Google Forms for signup |
| Link-in-bio | Linktree free tier, Beacons free tier, custom GitHub Pages page |

---

## Documentation & Knowledge

| Task | Free Tool |
|---|---|
| Notes / wiki | This GitHub repo (Markdown), Obsidian (free), Notion free tier |
| Diagrams | Mermaid (in Markdown), Excalidraw (free), draw.io (free) |
| Project management | GitHub Projects (free), this repo's task-board.md |
| CRM / tracking | GitHub Issues, spreadsheets (Google Sheets free / LibreOffice) |

---

## Toolchain Decision Rules

1. **Local first.** If it can run locally for free (Ollama, Whisper.cpp, Coqui TTS, Stable Diffusion), run it locally. No API cost, no rate limits, no dependencies.
2. **Free-tier second.** If local isn't viable, use a free tier (GitHub Pages, Canva free, Render free).
3. **Open-source third.** If neither works, find the best open-source alternative.
4. **Never pay for:** TTS, transcription, stock footage, basic video editing, basic hosting, basic analytics. All available free.
5. **Pay only for:** domain names (optional, ~$1/yr), premium stock if absolutely needed (rare).

---

*Last updated: 2026-09-12*  
*Owner: Sulbha, CEO — Mystify Me*
