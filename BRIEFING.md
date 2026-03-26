# AIVM Oracle Campaign — Claude Code Briefing

## What This Is

A 4-week quiz campaign site for AIVM (Boot The Core pre-testnet activation). One single HTML file containing all 4 quizzes. Users take one quiz per week, scores are stored to localStorage, Week 4 (The Oracle) reads all three scores and generates a personalised career prediction.

## Current State

- `aivm-oracle-quizzes.html` — the full file, ~104KB
- Quiz 1 works end to end
- Quizzes 2, 3, 4 have all content and JS but navigation is broken — clicking W2/W3/W4 either goes to a locked screen or fails silently

## What Needs Fixing

1. All 4 quiz cards on the hub should be clickable and take you into that quiz
2. Quiz 2 setup screen should load, collect work style preference, then start 9 questions
3. Quiz 3 setup screen should load, collect tenure, then start 9 questions
4. Quiz 4 should load an entry screen, read localStorage scores from Q1/Q2/Q3, and generate the Oracle verdict
5. Each quiz result screen should show correctly with share button, email gate, and anthem generator
6. The topbar W1/W2/W3/W4 buttons should all work

## Tech Stack

Pure HTML + CSS + Vanilla JS. No framework. No build step. Single file.
Fonts: Bebas Neue + DM Mono (Google Fonts)
Colours: white/purple (#7B2FBE)/yellow (#FFE500)/near-black (#0d0a14)

---

## QUIZ 1 — "Are You Going to Be Replaced by an AI Agent?"

### Setup Screen Data (collected before questions start)
- Profession (60 options across 9 groups — see full list in HTML)
- Desk-based (Yes fully / Mostly / No on feet)
- Taste required (Yes / Sometimes / Not really)

### 9 Scored Questions (Yes / No)
1. You send the same Slack message, report, or update on repeat every week.
2. You copy and paste data between systems by hand.
3. Your entire job could be written as a smart contract.
4. You sat through a call this week that could have been a Telegram message.
5. You mostly move or reformat information someone else created.
6. An AI agent is already doing your job somewhere in the world for $0.07 a day. You just haven't been told yet.
7. Your work output can be counted — PRs merged, tickets closed, reports filed.
8. You use ChatGPT or Claude to do things your job description says you should be doing yourself.
9. You've shipped something this week that required zero original thinking.

### 2 Closing Data Questions (not scored)
- D1: Do you currently use AI tools at work? → Daily / Sometimes / Not yet / Never — I'm a purist
- D2: What best describes you? → I write code / I manage people / I make strategy calls / I run the place

### Result Tiers (by score)
- 0–2: SUSPICIOUSLY SAFE (green) — "Either genuinely irreplaceable or very good at lying to this quiz."
- 3–4: BUYING TIME (yellow/amber) — "Runway exists. You're spending it on the wrong things."
- 5–6: OFFICIALLY ON NOTICE (orange) — "The memo exists. It just hasn't been sent to you yet."
- 7–9: ALREADY OBSOLETE (red) — "The agent is at your desk. It's just being polite."

### Signals Stored to localStorage (key: aivm_q1)
```json
{
  "score": 6,
  "tier": "OFFICIALLY ON NOTICE",
  "tiercls": "t2",
  "profession": "Marketing Manager",
  "timestamp": "2026-03-20T..."
}
```

---

## QUIZ 2 — "Are You Actually Good at AI — Or Just Pretending?"
*Subtitle: Like a star sign — but actually based on how you think.*

### Setup Screen Data
- Work style preference (Alone and deep / Team bouncing ideas / Both / Wherever the alpha is)

### 9 Questions (6-option multiple choice — each option maps to one LLM)
Each question has 6 answers mapping to: GPT / Gemini / Claude / Grok / Llama / DeepSeek

**Q1.** Someone asks for your opinion on a controversial take in the group chat. You:
- Say what the room wants to hear — why start a fight [GPT]
- Check if there's a framework for evaluating it first [Gemini]
- Write three paragraphs covering every angle before landing anywhere [Claude]
- Post your take immediately — if it triggers someone, good [Grok]
- Say nothing publicly, fork the conversation privately [Llama]
- Come back with the correct answer two hours later, quietly [DeepSeek]

**Q2.** You are given a complex new task you've never done before. First move:
- Google what other people have done and adapt their approach [GPT]
- Map out the full workflow before writing a single line [Gemini]
- Research until you're confident, then research a bit more [Claude]
- Start immediately — wrong moves are just data [Grok]
- Check if there's an open source solution you can self-host [Llama]
- Break it into logical components and solve from first principles [DeepSeek]

**Q3.** Your code review or feedback style is:
- Positive feedback first, wrap criticism in encouragement [GPT]
- Structured comments referencing the plan you already wrote [Gemini]
- Detailed, thorough, and probably longer than the PR itself [Claude]
- One line: this works but I would have done it differently [Grok]
- Why are we using a paid service — I can build this [Llama]
- Silent approval or a precise one-line fix with no explanation [DeepSeek]

**Q4.** A project deadline is tomorrow and the feature isn't ready. You:
- Ask the team what they need and adapt [GPT]
- Pull up the plan and identify exactly what can be cut [Gemini]
- Stay up all night making sure it's done properly [Claude]
- Ship what works and write a thread about what you learned [Grok]
- Deploy your own workaround that doesn't need the deadline [Llama]
- Quietly deliver it at 4am without telling anyone [DeepSeek]

**Q5.** How do you communicate in a standup or team update?
- Friendly update, check in with everyone, no strong opinions [GPT]
- Blockers, dependencies, next steps — in that order [Gemini]
- Full context on everything, including things nobody asked about [Claude]
- Done, doing, and a hot take on the sprint [Grok]
- One sentence. You already updated the repo. [Llama]
- Numbers only. If it can't be measured it doesn't get mentioned. [DeepSeek]

**Q6.** Someone shares a half-baked idea in the group chat. You:
- Add energy to it and ask how you can help [GPT]
- Immediately start mapping out how it would actually work [Gemini]
- Ask fifteen clarifying questions before forming a view [Claude]
- Point out the three ways it will fail, then say you like it anyway [Grok]
- Say you already built something like this and link a GitHub repo [Llama]
- Say nothing until you have run the numbers [DeepSeek]

**Q7.** Your relationship with documentation:
- I write what the team needs — I adapt to whatever style guide exists [GPT]
- Every system I build has docs before it ships [Gemini]
- Thorough, detailed, includes edge cases nobody will ever hit [Claude]
- The code is the documentation. Ship faster. [Grok]
- README only — if you can't figure it out, fork it [Llama]
- Precise, technical, and no words that aren't necessary [DeepSeek]

**Q8.** You find a bug in production at 11pm. You:
- Ping the team and ask who wants to take it [GPT]
- Check the incident runbook and follow the escalation process [Gemini]
- Fix it, document what happened, and write a post-mortem by midnight [Claude]
- Fix it live, post about it, go to sleep [Grok]
- Hot-patch your self-hosted version, raise a PR in the morning [Llama]
- Identify root cause first. Fix second. Never patch without understanding. [DeepSeek]

**Q9.** Pick the one that sounds most like your internal monologue:
- "What does the team need from me right now?" [GPT]
- "What's the most efficient path to the outcome?" [Gemini]
- "Have I considered every possible implication of this?" [Claude]
- "Why is everyone so afraid to just say what they think?" [Grok]
- "Why would I pay for that when I can build it myself?" [Llama]
- "I'll say something when I've verified it." [DeepSeek]

### 2 Closing Data Questions
- D1: What do you mainly use AI for? → Writing code / Writing and content / Research and analysis / Brainstorming and ideas / Summarising and note-taking / Trading or market research / Building products or tools / Automating workflows / Image or creative generation / I don't use AI yet
- D2: How long have you been using AI tools professionally? → Less than 6 months / 6 months to 2 years / 2+ years / Since before it was cool

### Scoring Logic
Count votes per LLM across all 9 questions. Highest count wins.
Tiebreak: prefer in order GPT > Gemini > Claude > Grok > Llama > DeepSeek

### 6 Results
| LLM | Type | Star Sign | One-liner |
|---|---|---|---|
| GPT-5.1 | THE CROWD PLEASER | ♎ Libra | Adaptable, warm, good at everything, great at nothing. |
| Gemini 3.0 | THE SYSTEMS THINKER | ♍ Virgo | You planned this quiz before you answered it. |
| Claude 4.5 | THE OVERTHINKER | ♋ Cancer | Careful, nuanced, slightly too long. But usually right. |
| Grok 4.1 | THE CHAOS AGENT | ♏ Scorpio | Contrarian. Funny. Ships at 2am. |
| Llama 4 | THE PRAGMATIST | ♑ Capricorn | Open source in your soul. Never paying for anything. |
| DeepSeek-V3.2 | THE PRECISION MACHINE | ♒ Aquarius | Math brain. Quietly outperforms everyone then says nothing. |

### Signals Stored to localStorage (key: aivm_q2)
```json
{
  "llm": "grok",
  "name": "Grok 4.1",
  "type": "THE CHAOS AGENT",
  "ai_use_case": "Writing code",
  "ai_tenure": "2+ years",
  "timestamp": "2026-03-20T..."
}
```

---

## QUIZ 3 — "Are You Actually Good at AI — Or Just Pretending?"

### Setup Screen Data
- Tenure in current role/industry → Less than 1 year / 1–3 years / 3–7 years / 7+ years — I've seen things

### 9 Questions (mix of posture-choice and multi-select)

Questions 1, 2, 3, 4, 7, 8, 9 are 4-option posture questions.
Questions 5 and 6 are multi-select (pick all that apply).

**Q1.** Your company announces it's replacing tools with AI-native stack. You:
- Sign up for early access before anyone asks [Sprint]
- Wait to see how the first adopters find it [Forward]
- Raise concerns in the all-hands — someone has to [Back]
- Quietly keep using the old way for as long as possible [Door]

**Q2.** A junior with 6 months experience outperforms you with AI. You:
- Ask them to walk you through their setup immediately [Sprint]
- Feel something uncomfortable but start experimenting [Forward]
- Wonder privately if their output is actually as good as it looks [Back]
- Say nothing and hope nobody else notices [Door]

**Q3.** When a new frontier model drops — GPT-5, Claude 4, Gemini 3 — you:
- Switch immediately and test it on real work that day [Sprint]
- Read the benchmarks and move over within the week [Forward]
- Wait for the reviews before changing anything [Back]
- Still using whatever I set up six months ago [Door]

**Q4.** What AI subscriptions are you currently paying for?
- Multiple paid plans across different providers [Sprint]
- One Pro or Max plan [Forward]
- Free tier only — good enough for now [Back]
- None — I don't pay for AI tools [Door]

**Q5.** Which AI providers are you actively using right now? (Multi-select)
- OpenAI / ChatGPT
- Anthropic / Claude
- Google / Gemini
- xAI / Grok
- Meta / Llama
- DeepSeek
- None of these
*Scoring: 0 = Door, 1–2 = Back, 3–4 = Forward, 5+ = Sprint*

**Q6.** Which tools are you actually using? (Multi-select)
- Claude or ChatGPT for work tasks
- AI notetaker — Otter, Fireflies, Notion AI
- Coding agent — Cursor, Copilot, Claude Coworker
- n8n, Zapier AI or another AI workflow tool
- Figma AI or design generation
- AI video / content — Runway, Sora, Synthesia
- None of these
*Scoring: 0 = Door, 1–2 = Back, 3–4 = Forward, 5+ = Sprint*

**Q7.** The honest reason you haven't gone further with AI:
- I have. What are you talking about. [Sprint]
- I haven't needed to yet — I'll move when I need to [Forward]
- I haven't had time to do it properly [Back]
- I don't fully trust it and I'm not sure I should [Door]

**Q8.** Someone in your network posts that AI just made their role redundant. You:
- DM them — this is useful signal, you want to understand how [Sprint]
- Read the thread carefully and quietly audit your own exposure [Forward]
- Feel briefly unsettled then keep scrolling [Back]
- Like the post and move on. That would never happen to you. [Door]

**Q9.** Pick the one that sounds most like where you are right now:
- "I'm already building with the thing that's supposed to replace me" [Sprint]
- "I'm paying attention and moving in the right direction" [Forward]
- "I'm watching carefully but haven't committed yet" [Back]
- "I'll deal with it when it becomes my problem" [Door]

### 2 Closing Data Questions
- D1: What is your biggest blocker? → No time / Don't trust outputs / Company won't allow it / Don't know where to start / Nothing — already using it fully / Don't think I need it
- D2: Company attitude toward AI? → All in / Exploring — pilots / Cautious / Resistant / I work for myself

### Scoring Logic
Count votes per posture (Sprint / Forward / Back / Door) across all questions.
Highest count wins.

### 4 Results
| Posture | Label | One-liner |
|---|---|---|
| Sprint | 🏃 THE AI SUPREMACIST | You were using Claude before your friends knew what an LLM was. |
| Forward | 🚶 THE CONSCIOUS ADOPTER | Moving in the right direction. Pace is the only question. |
| Back | 🧍 THE PROFESSIONAL HESITATOR | You've been about to set up n8n for four months. |
| Door | 🚪 THE LAST HUMAN STANDING | Bold strategy. Let us know how it goes. |

### Signals Stored to localStorage (key: aivm_q3)
```json
{
  "posture": "sprint",
  "label": "🏃 THE AI SUPREMACIST",
  "tools": {"providers": ["OpenAI / ChatGPT", "Anthropic / Claude"], "tools": ["Cursor, Copilot"]},
  "ai_blocker": "Nothing — already using it fully",
  "company_ai": "All in — building fast",
  "timestamp": "2026-03-20T..."
}
```

---

## QUIZ 4 — "Your 2027 Has Already Been Written."

### No Questions
Reads aivm_q1, aivm_q2, aivm_q3 from localStorage.
Uses defaults if any are missing (for testing).

### Oracle Verdict Logic
Match: q1.tiercls + q2.llm + q3.posture → Oracle verdict object

### Example Combinations
| Q1 Risk | Q2 LLM | Q3 Posture | Codename | Verdict |
|---|---|---|---|---|
| t3 (replaced) | gpt/claude | door | THE HUMAN MACRO | "The agent clocked in three months ago." |
| t3 (replaced) | grok/llama | sprint | THE CONTROLLED DEMOLITION | "You're building what's supposed to replace you." |
| t1/t2 | claude | back | THE ARTICULATE HESITATOR | "Awareness without urgency." |
| t0/t1 | gemini | sprint/forward | THE SYSTEMATIC SURVIVOR | "Safe by design, not accident." |
| t0 | llama | sprint | THE OPEN SOURCE ORACLE | "Quietly the most prepared person here." |

### Result Screen Contains
1. Oracle Codename (large display font)
2. Verdict (2–3 punchy lines)
3. Score dashboard (3 boxes: Risk Score / LLM Type / Posture)
4. Description paragraph
5. Boot The Core CTA
6. AI-generated anthem button (calls Claude API)
7. Share on X button

---

## DATA STORAGE SCHEMA

```
localStorage keys:
  aivm_email     — user's email string
  aivm_profile   — JSON: {email, profession, desk, taste, q1}
  aivm_q1        — JSON: quiz 1 result
  aivm_q2        — JSON: quiz 2 result
  aivm_q3        — JSON: quiz 3 result
  aivm_responses — JSON array: all response events for admin dashboard
```

Admin dashboard: Press Shift+D anywhere to open data view.

---

## VISUAL DESIGN SYSTEM

```css
--bg: #fafaf8          /* warm off-white background */
--surface: #ffffff      /* card backgrounds */
--border: #e8e2f4      /* subtle purple-tinted borders */
--text: #0d0a14        /* near black */
--muted: #9988bb       /* muted purple for labels */
--purple: #7B2FBE      /* primary accent — buttons, highlights */
--pl: #f5f0ff          /* light purple tint for selected states */
--accent: #FFE500      /* yellow — used sparingly for warning/energy */
--red: #c41f1f         /* danger tier */
--orange: #c45a00      /* warning tier */
--green: #1a7a45       /* safe tier */
```

Fonts: Bebas Neue (display/titles) + DM Mono (body/UI)
Grid background: subtle 40px grid on body using CSS background-image
Progress bar: 2px purple fill at top of question screens

---

## ANTHEM GENERATOR

All quizzes have an optional anthem button on the result screen.
Calls: POST https://api.anthropic.com/v1/messages
Model: claude-sonnet-4-20250514
The API key is handled by the environment — do not add one in code.

Prompt structure: Pass quiz result data, request a 12-line darkly funny song.
Genre is matched to result tier.

---

## WHAT TO BUILD / FIX

Priority order:

1. **Fix quiz navigation** — clicking W2/W3/W4 in topbar and hub should open the correct quiz setup screen
2. **Quiz 2 full flow** — setup → 9 questions (6-option each) → 2 data Q → analyzing → result → email gate → anthem → share
3. **Quiz 3 full flow** — setup → 9 questions (mix of 4-option posture + multi-select) → 2 data Q → analyzing → result → email gate → anthem → share  
4. **Quiz 4 Oracle flow** — entry screen → reads localStorage → analyzing → verdict + scores + description + CTA → oracle anthem → share
5. **Hub state** — cards update to show completed results and unlock sequentially
6. **All for testing** — keep all 4 weeks unlocked/accessible for now (no week-locking)

---

## NICE TO HAVE (after core flow works)

- Scorecard design — a shareable card image version of the result (could use html2canvas)
- Smooth transitions between screens
- Mobile responsiveness check
- Data dashboard improvements (Shift+D)
