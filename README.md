# AIVM Oracle — Your AI Autopsy 🧠⚡

> *Every single week, we reveal more about yourself and your relationship to AI. The AI Oracle is waiting.*

A 5-week interactive quiz campaign for **AIVM** (Boot The Core pre-testnet activation). One self-contained HTML file. No frameworks. No build step. Pure vibes, pure signal.

---

## 🔗 Live Site

**[omarelsafy.github.io/aivm-oracle-quizzes](https://omarelsafy.github.io/aivm-oracle-quizzes)**

---

## 🧬 What Is This?

A personality-test-meets-career-diagnostic for the AI age. Users take one quiz per week. Each quiz peels back another layer of their relationship with AI — how exposed they are, how they think, how they adapt, and whether they can even tell what's real anymore.

Results stack. By the end, the Oracle has enough signal to deliver a brutally honest career prediction for 2027.

---

## 🗓️ The 5 Weeks

### Week 1 — *Are You Going to Be Replaced by an AI Agent?*
- **Format:** 9 yes/no questions + 2 data questions
- **Setup:** Profession (60 options), desk-based status, taste requirement
- **Result tiers:**
  - 🟢 **SUSPICIOUSLY SAFE** (0–2) — "Either genuinely irreplaceable or very good at lying to this quiz."
  - 🟡 **BUYING TIME** (3–4) — "Runway exists. You're spending it on the wrong things."
  - 🟠 **OFFICIALLY ON NOTICE** (5–6) — "The memo exists. It just hasn't been sent to you yet."
  - 🔴 **ALREADY OBSOLETE** (7–9) — "The agent is at your desk. It's just being polite."

### Week 2 — *What LLM Matches Your Personality?*
- **Format:** 9 multiple choice questions (6 options each, mapped to LLMs)
- **Like a star sign — but based on how you actually think.**
- **Results:**

  | LLM | Type | Star Sign |
  |-----|------|-----------|
  | GPT-5.1 | The Crowd Pleaser | ♎ Libra |
  | Gemini 3.0 | The Systems Thinker | ♍ Virgo |
  | Claude 4.5 | The Overthinker | ♋ Cancer |
  | Grok 4.1 | The Chaos Agent | ♏ Scorpio |
  | Llama 4 | The Pragmatist | ♑ Capricorn |
  | DeepSeek-V3.2 | The Precision Machine | ♒ Aquarius |

### Week 3 — *Are You Actually Good at AI — Or Just Pretending?*
- **Format:** 9 questions (mix of posture-choice + multi-select)
- **Not about what you know. About what you do when the ground shifts.**
- **Results:**

  | Posture | Label |
  |---------|-------|
  | Sprint | 🏃 The AI Supremacist |
  | Forward | 🚶 The Conscious Adopter |
  | Back | 🧍 The Professional Hesitator |
  | Door | 🚪 The Last Human Standing |

### Week 4 — *Can You Even Tell What's Real?*
- **Format:** 5 detection challenges (images, text, video)
- **The quiz that makes you question everything.**
- Users are shown content and must determine: **Real or AI-generated?**
- Score: 0–5 detection accuracy

### Week 5 — *The Oracle Verdict*
- **No questions.** Reads all 4 quiz results from localStorage.
- Combines threat level + LLM personality + AI posture + detection score
- Delivers a personalized career prediction for 2027
- Templated paragraph system — no API credits needed

---

## 🃏 Score Card System

Each quiz generates a **score card** (inspired by Monad Cards). Features:

- **Large animated PFP** from connected X/Twitter account
- **Pulsing ring** around profile picture (purple glow animation)
- **Cumulative results** — each week's card stacks all previous scores:
  - Week 1 card: W1 result only
  - Week 2 card: W1 + W2 results
  - Week 3 card: W1 + W2 + W3 results
  - Week 4 card: All 4 results + detection score
  - Week 5 card: Full Oracle verdict with all data
- **Share buttons** — X/Twitter, copy link, download card
- **Templated Oracle paragraph** — brutally honest prediction based on all combined scores

---

## 🎠 3D Focus Carousel

Quiz selection uses a **character-select-style carousel**:

- Center card is **scale(1.15)** with full opacity and purple glow
- Side cards scale down to **0.82** and **0.68** with fading opacity
- Spring physics feel — stiff and tactile, not floaty
- Click any side card to bring it to center
- Arrow keys, swipe gestures, and dot navigation
- Progressive unlocking — each quiz unlocks after completing the previous one
- Completed quizzes show ✓ checkmark and result summary

---

## 🖼️ X/Twitter PFP Integration

At the end of Quiz 1, users can connect their X profile:

- Enter X handle → fetches profile picture
- PFP displays on **every subsequent quiz** and score card
- Animated purple ring around the PFP (pulsing glow)
- Shows `@handle` in topbar throughout the experience
- Stored in localStorage for persistence

---

## 🎨 Visual Design System

```
Background:  #fafaf8  (warm off-white)
Surface:     #ffffff  (card backgrounds)
Border:      #e8e2f4  (subtle purple-tinted)
Text:        #0d0a14  (near black)
Primary:     #7B2FBE  (purple — buttons, highlights, accents)
Accent:      #FFE500  (yellow — used sparingly)
Danger:      #c41f1f  (red tier)
Warning:     #c45a00  (orange tier)
Safe:        #1a7a45  (green tier)
```

**Fonts:** Bebas Neue (display/titles) + DM Mono (body/UI)

**AI Graffiti:** Scattered brand slogans fade in/out across the grid background — "BOOT THE CORE", "THE MACHINE KNOWS", "YOUR FUTURE IS BEING COMPILED" etc.

---

## 🛠️ Tech Stack

| Layer | Choice |
|-------|--------|
| Framework | None — vanilla HTML/CSS/JS |
| Build step | None — single file |
| Fonts | Google Fonts (Bebas Neue + DM Mono) |
| Storage | localStorage |
| Hosting | GitHub Pages |
| API (optional) | Claude API for anthem generation |

---

## 📦 Data Storage

```
localStorage keys:
  aivm_email      — user's email
  aivm_xhandle    — X/Twitter handle
  aivm_xpfp       — X/Twitter profile picture URL
  aivm_profile    — JSON: profession, desk, taste, setup data
  aivm_q1         — JSON: Quiz 1 result (score, tier, profession)
  aivm_q2         — JSON: Quiz 2 result (LLM match, type, star sign)
  aivm_q3         — JSON: Quiz 3 result (posture, tools, blocker)
  aivm_q4         — JSON: Quiz 4 result (detection score)
  aivm_responses  — JSON array: all response events for analytics
```

**Admin dashboard:** Press `Shift+D` anywhere to open the data view. Export to CSV.

---

## 🎵 Anthem Generator (Optional)

Each quiz result screen has an optional "Generate Your Anthem" button:
- Calls Claude API (`claude-sonnet-4-20250514`)
- Generates a 12-line darkly funny song based on your result
- Genre matched to result tier (triumphant brass → funeral march)
- Requires API key — works without it, just hides the button

---

## 🚀 Deployment

This is a single `index.html` file. Deploy anywhere:

```bash
# GitHub Pages (current)
# Push index.html to main branch, enable Pages in Settings

# Or drag-and-drop to:
# - Netlify (app.netlify.com/drop)
# - Vercel (vercel.com/new)
# - Cloudflare Pages
```

---

## 📁 File Structure

```
/
├── index.html    ← the entire app (single file, ~120KB)
├── README.md     ← you're reading it
└── BRIEFING.md   ← original quiz content & scoring logic
```

---

## 🧭 Roadmap

- [x] Quiz 1 — AI Replacement Risk
- [x] Quiz 2 — LLM Personality Match
- [x] Quiz 3 — AI Posture Assessment
- [x] 3D Focus Carousel for quiz selection
- [x] X/Twitter PFP integration
- [x] AI Graffiti background layer
- [ ] Quiz 4 — AI Detection Challenge (images/text/video)
- [ ] Quiz 5 — Oracle Verdict (reads all scores)
- [ ] Cumulative score cards with PFP
- [ ] Templated Oracle prediction paragraphs
- [ ] html2canvas shareable card images
- [ ] Mobile responsive polish

---

## 👤 Built by

**[@Ommiii_](https://x.com/Ommiii_)** for the AIVM Oracle Campaign

---

*The machine already knows. The question is whether you do.*
