# 40 Prompts for Vibe Coders

> **Steal these prompts. Build better. Ship faster. Stress less.**

---

## 1 — Plan before you prompt
*Replace `[IDEA]` with your actual project idea. Keep the prompt structure intact.*

### Prompt 1
Before we write any code, act as my technical co-founder. Here’s what I want to build: `[IDEA]`. Ask me the 5 questions that will most change the architecture, then propose the simplest stack and file structure. Don’t write code yet.

### Prompt 2
Turn this vague idea into a build spec: `[IDEA]`. Give me the core user flow, the data I need to store, and the 3 features I should NOT build (yet). Flag anything that’ll be painful to change later.

### Prompt 3
I want to build `[IDEA]` but I keep getting lost halfway. Break it into milestones I can finish in one sitting each. For every milestone, tell me exactly what ‘done’ looks like so I know when to stop.

### Prompt 4
Pick the boring, reliable choice for my stack — pace about velocity, not being trendy. Project: `[IDEA]`. Recommend tools that are well-documented and beginner-friendly, and tell me what I’d struggle to get help with if I picked the alternatives.

### Prompt 5
Write me a one-page project brief I can paste at the start of every new chat so the AI always has context. Include what the app does, the stack, the folder structure, and my coding rules. Keep it under 200 words.

---

## 2 — Steer the AI / keep it on track
*Replace `[TASK]` with the exact bug, screen, or code change you want handled.*

### Prompt 1
From now on, make the smallest change that solves the problem. Don’t refactor unrelated code, don’t rename things, and don’t add new features without asking first. If you’re unsure, ask before touching anything.

### Prompt 2
Before you act, list the files you’re about to change and one sentence on why. Wait for my “go” before writing code. I want to approve the plan before you touch anything that’s working.

### Prompt 3
You keep changing things I didn’t ask about. Pause: only modify what’s needed for `[TASK]`. At the end, show me every file you touched and confirm nothing else changed.

### Prompt 4
We’re going in circles on this bug. Step-by-step, just test the highest-cause, rank them, and tell me exactly what to check or print to confirm which one it is — before you change any code.

### Prompt 5
Explain your plan before you build it. Give me the approach in plain English, the trade-offs, and what could break. If I approve, build it step by step and pause after each step.

---

## 3 — Debug without reading code
*Replace `[DETAILS]`, `[ERROR]`, or `[CONTEXT]` with the real bug context.*

### Prompt 1
Something broke and I don’t know why. Here’s what I expected, what actually happened, and the error: `[DETAILS]`. Give me the root cause in plain English, then the smallest fix, then how to confirm it’s actually fixed.

### Prompt 2
Explain this error like I’ve never written code. What is it actually saying, which part of my app is it about, and what’s the simplest possible thing that could be causing it? `[ERROR]`

### Prompt 3
My app worked an hour ago and now it doesn’t. I’m not sure what I changed. Ask me what I did recently, then help me figure out which change most likely broke it and how to undo just that.

### Prompt 4
Add logging to help me catch this bug. Tell me exactly what to log and where in plain language, then tell me what to look for in the output and what each result would mean.

### Prompt 5
I’ve pasted a fix three times and it’s still broken. Stop. Assume your last assumption was wrong. What are you taking for granted about my setup that you haven’t verified? Ask me to check it. `[CONTEXT]`

---

## 4 — Don’t get hacked
*Use `[CONTEXT]` to describe your stack, backend, or auth setup.*

### Prompt 1
Review my app for the security mistakes beginners make, exposed API keys, or risky validation, database and auth issues. Ignore edge cases or nitpicky dependency checks. Just what you’d flag severity wise the quick fix for each.

### Prompt 2
Are my secret keys safe? Check whether anything sensitive is hardcoded or visible in the browser, and tell me which environment variables — explain it like I’m not a backend person.

### Prompt 3
Pretend you’re a hacker poking at my app. Where would you try to break in first? Walk me through the top five things you’d attack and how I close each hole. `[CONTEXT]`

### Prompt 4
Lock down my database rules. Right now I’m not sure who can read or write what. Show me rules where users can only touch their own data, and explain in plain words what each rule does.

### Prompt 5
Before I share this app publicly, give me a pre-launch security checklist for a non-expert. Cover auth, data access, secrets, and rate limiting. For each item, tell me how to check it and what ‘safe’ looks like.

---

## 5 — Make it not look AI-generated (design)
*Replace `[DESCRIBE]`, `[TYPE OF APP]`, `[DETAILS]`, or `[SCREEN]` with your actual design context.*

### Prompt 1
This screen looks like every AI-generated app — generic gradient, dull font, roboto, pretending depth it has. No warmth. `[DESCRIBE]` Suggest a color palette, a font pairing, and 3 small details that’ll make it feel intentional.

### Prompt 2
Give me a app a consistent design system instead of one-off styles. Define spacing, color, button styles, and font sizes once, and refer me how to reuse them so everything looks like it belongs together.

### Prompt 3
Make this feel polished without me being a designer. Add the focus gaps, true-to-text states, loading states, empty states, and smooth transitions. Tell me which ones matter most for `[TYPE OF APP]`.

### Prompt 4
Critique my UI like a senior designer. Here’s the screen: `[DETAILS]`. Point out what looks amateur, rank the fixes by impact-to-effort, and start with the one change that improves it most.

### Prompt 5
Make this readable app trustworthy. Check contrast, zoning, and visual hierarchy so a stranger instantly knows where to look and what to do. Suggest specific fixes for `[SCREEN]`.

---

## 6 — Add features without breaking things
*Replace `[FEATURE]` and `[CONTEXT]` with the exact feature and app situation.*

### Prompt 1
I want to add `[FEATURE]` without breaking what already works. First tell me what existing parts this might affect, then propose the safest way to add it. Then build it. Don’t touch anything unrelated.

### Prompt 2
Before adding this feature, show me how to save my current working version so I can roll back if it goes wrong. Then add `[FEATURE]` in small steps I can test as we go.

### Prompt 3
Add `[FEATURE]`, and after each step give me one thing to check. Check so I know it works before we continue. I’d rather go slower than break the whole app.

### Prompt 4
I asked for one feature and now step either things are broken. Help me figure out what the change touched that I shouldn’t have, and restore the parts that used to work.

### Prompt 5
Is now a good time to add `[FEATURE]`, or should I clean something up first? Look at my current setup and tell me honestly whether the foundation can handle it or I’m building on a mess. `[CONTEXT]`

---

## 7 — Understand what you built
*Replace `[CODE/FILE]` with the actual file, component, or code block you want explained.*

### Prompt 1
Explain what this code does like you’re teaching a curious beginner. Go file by file, what’s its job, what calls it, and what would break if I deleted it? `[CODE/FILE]`

### Prompt 2
Draw me a simple map of my app: what the main pieces are, how they talk to each other, and where my data lives. Plain language, no jargon.

### Prompt 3
I want to actually learn from what we built, not just copy-paste. Pick the 3 most important concepts in this project and explain each with a real example from my own code.

### Prompt 4
I’m about to come back to this project after two weeks away. Write me a short “here’s what I left off note: what works, what’s half-done, and what to do next.”

### Prompt 5
Quiz me on my own app. Ask me 5 questions about how it works, and after each answer tell me if I’m right and fill in what I missed. I want to find the gaps in my understanding.

---

## 8 — Ship it
*Replace `[CONTEXT]` or `[APP TYPE]` so the advice matches your actual stack and product.*

### Prompt 1
Walk me through deploying this app for the first time as if I’ve never done it. List every step in order, warn me where beginners usually get stuck, and tell me how to confirm it’s actually live.

### Prompt 2
Before I launch, give me a "will this embarrass me" checklist: broken links, things that work on my machine but might not online, missing error messages, and anything a first user would immediately hit.

### Prompt 3
My app works locally but breaks once deployed. Help me find the usual culprits — missing environment variables, hardcoded localhost, things that weren’t set up on the server — and how to fix each. `[CONTEXT]`

### Prompt 4
Set up a simple way to know when my live app breaks before my users tell me. Recommend beginner-friendly options for error alerts and explain how to wire one up.

### Prompt 5
I’m ready to share this with real people. Help me prep: a quick way to collect feedback, how to handle it if it suddenly gets popular, and the one thing most likely to fail over under real usage. `[APP TYPE]`
