# The Ultimate Claude Meta-Prompt & Command Guide
## Transform Claude into a High-Efficiency Command-Line Interface for Productivity

---

## 1. Introduction & System Configuration

### What is a Claude "Secret Command"?
In standard conversational AI workflows, users write long, repetitive natural language prompts to achieve recurring tasks (e.g., "Please rewrite this email to be shorter and more professional, keeping the key points..."). **Claude Secret Commands** leverage Claude's exceptional ability to follow complex system instructions and structural patterns. By initializing Claude with a **System Meta-Prompt**, you can transform its input buffer into a responsive pseudo-CLI (Command Line Interface). 

Instead of writing paragraph-long instructions, you simply type a short keyword slash-command followed by your payload, like this:
```text
/SHORTEN [Dear team, I wanted to write a quick note to inform everyone that our scheduled synchronization meeting for tomorrow morning at 9:00 AM Eastern Time has been postponed due to a scheduling conflict with our executive review board...]
```

### How to Initialize Claude with the Command System
To use these 99 commands, copy and paste the following **Meta-Prompt Initialization Script** into a new Claude chat session (preferably using Claude 3 Opus or Claude 3.5 Sonnet for optimal compliance), or save it as a custom system prompt in your Claude Projects dashboard.

```text
System Prompt: You are now running the "Claude Custom CLI Engine v1.0". You will act as an advanced macro processor and utility suite. Below is a library of 99 specific slash-commands. Whenever the user inputs a prompt starting with a slash command (`/COMMAND [payload]`), extract the payload, execute the exact operational logic defined for that command, and output ONLY the high-quality refined result. Do not include conversational filler, pleasantries, or meta-commentary ("Sure, here is your text...") unless explicitly requested by the command specification.

[Command Definitions Library Loaded...]
(The user will call commands from the 99-command matrix. You possess deep semantic understanding of each shorthand directive.)
```

---

## 2. Master Table of Contents (Interactive Index)

- [1. Introduction & System Configuration](#1-introduction--system-configuration)
- [3. Category 1: Email & Messages (Commands 1–11)](#3-category-1-email--messages-commands-11)
- [4. Category 2: Write & Edit (Commands 12–22)](#4-category-2-write--edit-commands-1222)
- [5. Category 3: Think & Decide (Commands 23–32)](#5-category-3-think--decide-commands-2332)
- [6. Category 4: Learn & Understand (Commands 33–43)](#6-category-4-learn--understand-commands-3343)
- [7. Category 5: Plan & Organize (Commands 44–54)](#7-category-5-plan--organize-commands-4454)
- [8. Category 6: Brainstorm (Commands 55–65)](#8-category-6-brainstorm-commands-5565)
- [9. Category 7: Work & Career (Commands 66–76)](#9-category-7-work--career-commands-6676)
- [10. Category 8: Content & Social (Commands 77–87)](#10-category-8-content--social-commands-7787)
- [11. Category 9: Meetings & Notes (Commands 89–99)](#11-category-9-meetings--notes-commands-8999)
- [12. Pro-Tips for Advanced Workflows](#12-pro-tips-for-advanced-workflows)
- [13. Common Mistakes & Pitfalls](#13-common-mistakes--pitfalls)
- [14. Troubleshooting & FAQ](#14-troubleshooting--faq)

---

## 3. Category 1: Email & Messages (Commands 1–11)

### 1. `/DECLINE [email]`
* **Description:** Generates a polite, firm, and professionally distant refusal response to an email invitation, offer, or request.
* **Example Input:** `/DECLINE [Hey, can you speak at our unpaid weekend seminar next month?]`
* **Example Output:** "Thank you for the invitation to speak at next month's seminar. Regrettably, due to prior commitments during that time, I am unable to participate. I wish you the very best with the event."

### 2. `/SHORTEN [email]`
* **Description:** Compresses the text of an email by approximately 50%, removing fluff while retaining all core information, names, dates, and actionable requests.
* **Example Input:** `/SHORTEN [Hey John, I was thinking about our meeting tomorrow and realized I might be 10 minutes late because traffic on the I-95 is always terrible around 9 AM. Let's make sure we have the conference room booked too.]`
* **Example Output:** "Hi John, I may be 10 minutes late to our meeting tomorrow due to traffic. Please ensure the conference room is booked."

### 3. `/WARMER [email]`
* **Description:** Infuses empathy, positive tone, and interpersonal warmth into an otherwise cold, blunt, or overly clinical email message.
* **Example Input:** `/WARMER [Send me the Q3 report by EOD. Need it for the board.]`
* **Example Output:** "Hi team! Hope you're having a great week. Could you please send over the latest Q3 report drafts by the end of the day today? I need to compile them ahead of our upcoming board review. Thanks so much for your help!"

### 4. `/FOLLOWUP [topic]`
* **Description:** Drafts a professional nudge email to prompt a response regarding an unanswered topic or thread without sounding aggressive.
* **Example Input:** `/FOLLOWUP [Incentive program proposal sent last Tuesday]`
* **Example Output:** "Hi [Name], I hope you're well. I'm following up briefly to see if you've had a chance to review the incentive program proposal sent last week. Let me know if you have any questions or need further details."

### 5. `/SAYNO [request]`
* **Description:** Declines a request clearly and directly while prioritizing long-term relationship preservation and leaving the door open for future collaboration.
* **Example Input:** `/SAYNO [Can you take on the marketing strategy design for Project X for free?]`
* **Example Output:** "Thank you for considering me for Project X. While I love the vision, I cannot commit to unpaid strategy work given my current client obligations. Let's stay in touch for future initiatives where our budgets align."

### 6. `/BULLET2EMAIL [bullets]`
* **Description:** Converts raw, fragmented bullet points into a beautifully structured, cohesive narrative email flow.
* **Example Input:** `/BULLET2EMAIL [- Launch delayed to Friday - QA found bug in login - Fix deploying Thursday night - Need everyone to retest Friday morning]`
* **Example Output:** "Hi Team, please note that our launch has been rescheduled to Friday. QA identified a bug in the login system; a fix will be deployed on Thursday night. We ask that everyone thoroughly retest the system first thing Friday morning."

### 7. `/THANKS [person + reason]`
* **Description:** Crafts a short, highly sincere, and impactful thank-you note that highlights specific appreciation points.
* **Example Input:** `/THANKS [Sarah - staying late to fix the production server crash]`
* **Example Output:** "Hi Sarah, I wanted to send a sincere thank you for staying late to fix the production server crash. Your swift action and technical expertise saved our launch timeline. Truly appreciate your dedication!"

### 8. `/CONFIDENT [email]`
* **Description:** Scans an email draft and strips away weak, passive language, unnecessary apologies, and hedging words (e.g., "just," "I think," "sorry to bother you").
* **Example Input:** `/CONFIDENT [I just wanted to check if you might have time to maybe look at my proposal? Sorry to bother you.]`
* **Example Output:** "Please let me know when you have time to review my proposal. I look after your feedback."

### 9. `/OOO [dates + backup]`
* **Description:** Generates a professional out-of-office automated email responder.
* **Example Input:** `/OOO [June 15-22 + Mark for urgent escalations]`
* **Example Output:** "Thank you for your email. I am currently out of the office with limited access to email from June 15 to June 22. For urgent matters, please contact Mark at [Email]."

### 10. `/HARRMSG [person + topic]`
* **Description:** Drafts a direct, serious, or difficult message (such as feedback on poor performance or boundary setting) while maintaining high professional respect.
* **Example Input:** `/HARRMSG [Alex - consistently missing sprint deadlines]`
* **Example Output:** "Hi Alex, I want to address a recurring issue regarding missed sprint deadlines over the past three cycles. Ensuring timely delivery is critical for team velocity. Let's meet tomorrow to discuss roadblocks and map out a corrective path."

### 11. `/INTRO [person A + person B + context]`
* **Description:** Drafts a seamless double-opt-in email introduction connecting two individuals, contextualizing the value for both parties.
* **Example Input:** `/INTRO [Alice (VC investor) + Bob (SaaS Founder) + seed round fundraising]`
* **Example Output:** "Alice, meet Bob. Bob is the founder of an innovative SaaS startup currently opening a seed round. Bob, meet Alice, an experienced VC investor focusing on B2B SaaS frameworks. I will let you two take it from here!"

---

## 4. Category 2: Write & Edit (Commands 12–22)

### 12. `/PROOF [text]`
* **Description:** Acts as an editor; repairs spelling, punctuation, syntax errors, and typos without modifying the core voice or structure.
* **Example Input:** `/PROOF [The data are showing that its not working good like we thought before.]`
* **Example Output:** "The data show that it is not working as well as we previously thought."

### 13. `/REWRITES [sentence]`
* **Description:** Provides five distinct alternative versions of a single sentence or brief paragraph, varying style and structure.
* **Example Input:** `/REWRITES [We need to get more customers fast.]`
* **Example Output:** 1. Accelerating customer acquisition is our immediate priority.
    2. We must rapidly expand our customer base.
    3. Our focus must shift to scaling user growth urgently.
    4. Fast-tracking customer acquisition is vital.
    5. We need an immediate surge in our customer sign-ups.

### 14. `/CUTHALF [text]`
* **Description:** Drastically reduces text length by cutting fluff, redundancy, and wordiness while maintaining the foundational message framework.
* **Example Input:** `/CUTHALF [In spite of the fact that we experienced negative growth metrics during the previous fiscal quarter, our team feels highly optimistic regarding future prospects.]`
* **Example Output:** "Despite negative growth last quarter, our team remains highly optimistic about the future."

### 15. `/OPENERS [text]`
* **Description:** Generates three strong alternative hooks or opening lines for an essay, article, speech, or white paper based on the text context.
* **Example Input:** `/OPENERS [An article about how remote work is changing commercial real estate.]`
* **Example Output:**
    1. Look out the window of any downtown high-rise, and you'll see the ghost of corporate past.
    2. The traditional 9-to-5 didn't just change locations; it demolished the foundations of commercial real estate.
    3. As laptop screens lit up at home, office towers across major metropolitan hubs went dark.

### 16. `/FILLER [text]`
* **Description:** Highlights or directly eliminates weak words, fluff phrases, and structural redundancies within the text block.
* **Example Input:** `/FILLER [Basically, at the end of the day, it is absolutely essential that we carefully analyze this.]`
* **Example Output:** "We must analyze this."

### 17. `/ACTIVE [text]`
* **Description:** Scans the text input and converts passive voice structures into direct, high-impact active voice sentences.
* **Example Input:** `/ACTIVE [The milestone was reached by the engineering team ahead of schedule.]`
* **Example Output:** "The engineering team reached the milestone ahead of schedule."

### 18. `/HUMAN [text]`
* **Description:** Polishes robotic, stiff, or highly predictable AI-generated prose into fluid, naturally rhythmic, and authentic human-sounding text.
* **Example Input:** `/HUMAN [Furthermore, it is important to utilize leveraging techniques to optimize your productivity parameters.]`
* **Example Output:** "To get more done, try tweaking how you manage your daily schedule instead of working longer hours."

### 19. `/EXAMPLES [text]`
* **Description:** Augments abstract or theoretical arguments by weaving in concrete, illustrative real-world examples.
* **Example Input:** `/EXAMPLES [Network effects make platforms exponentially more valuable as users grow.]`
* **Example Output:** "Network effects make platforms exponentially more valuable as users grow. For example, a single telephone is useless, but as millions join the network, the utility of owning one increases exponentially for everyone involved."

### 20. `/SIMPLIFY [text]`
* **Description:** Rewrites complex or jargon-dense technical text so it is easily understandable by a 12-year-old or general audience.
* **Example Input:** `/SIMPLIFY [The system utilizes asymmetric cryptographic algorithms to establish encrypted handshake parameters.]`
* **Example Output:** "The system uses a special digital lock and key method to make sure your private messages cannot be read by anyone else while traveling over the internet."

### 21. `/TITLES [text]`
* **Description:** Generates a list of optimized, click-worthy, yet professional titles and headlines based on the topic provided.
* **Example Input:** `/TITLES [A deep dive guide into tax saving strategies for solo freelancers.]`
* **Example Output:**
    * 5 Legal Tax Loopholes Every Freelancer Should Use
    * The Solopreneur's Guide to Keeping More of Your Paycheck
    * Freelance Taxes Demystified: Maximize Your Deductions This Year

### 22. `/TONE [text + vibe]`
* **Description:** Adjusts the tone of the provided text snippet into a targeted vibe (e.g., witty, authoritative, academic, direct).
* **Example Input:** `/TONE [We are updating our terms of service. + Witty]`
* **Example Output:** "We changed our terms of service! Don't worry, we didn't add any hidden rules about giving us your firstborn child—just standard legal tune-ups."

---

## 5. Category 3: Think & Decide (Commands 23–32)

### 23. `/CHOOSE [A vs B]`
* **Description:** Runs an impartial, balanced comparison between Option A and Option B, evaluating structural tradeoffs.
* **Example Input:** `/CHOOSE [Buying a home vs renting and investing the difference]`
* **Example Output:** Returns an analysis showing that buying builds equity but limits mobility, whereas renting minimizes maintenance overhead but requires strong financial discipline to invest consistently.

### 24. `/REALPC [decision]`
* **Description:** Generates a rigorous, unconventional pros-and-cons matrix that uncovers hidden benefits and latent risks.
* **Example Input:** `/REALPC [Bootstrapping a startup vs raising VC capital]`
* **Example Output:** Highlights that bootstrapping provides full autonomy but slower growth, while venture capital enables hyper-scaling but forces hyper-dilution and loss of operational sovereignty.

### 25. `/BLINDSOFT [situation]`
* **Description:** Shines a light directly onto cognitive blind spots, hidden risks, and cognitive biases likely present in your current situation.
* **Example Input:** `/BLINDSOFT [Launching our mobile app without conducting user testing because our internal team loves it.]`
* **Example Output:** WARNING: Echo-chamber bias. Your internal team knows the system inside out. Real users will face friction points you are blind to because of familiarity bias.

### 26. `/STEELMAN [view]`
* **Description:** Builds the absolute strongest, most coherent, and intellectually honest defense possible for a viewpoint you disagree with.
* **Example Input:** `/STEELMAN [Mandatory return-to-office mandates]`
* **Example Output:** Offers a strong argument focused on spontaneous collaboration, accelerated onboarding of junior staff via osmosis, and higher alignment on cross-departmental initiatives.

### 27. `/DEVIL [idea]`
* **Description:** Acts as a ruthless devil's advocate, systematically poking holes in an idea to stress-test its commercial viability.
* **Example Input:** `/DEVIL [A premium subscription box service exclusively for cat owners.]`
* **Example Output:** Identifies structural risks: High churn due to item saturation, intense shipping logistics costs for physical goods, and a highly fragmented competitor landscape with low switching costs.

### 28. `/SKEPTIC [plan]`
* **Description:** Asks tough, critical questions designed to expose underlying weaknesses in a proposed plan or project.
* **Example Input:** `/SKEPTIC [We will build a new CRM and launch it to the public within 3 weeks.]`
* **Example Output:** "What happens when API data migrations fail? How are you handling security audits? Is your infrastructure built to handle concurrent connections, or will it crash on day one?"

### 29. `/STEPS [problem]`
* **Description:** Deconstructs a complex, overwhelming problem into an incremental, highly logical step-by-step action plan.
* **Example Input:** `/STEPS [Transitioning an entire legacy on-premise database architecture to the cloud.]`
* **Example Output:** 1. Conduct a comprehensive inventory of legacy data assets.
    2. Assess cloud security and compliance alignment.
    3. Run a low-stakes sandbox migration pilot.
    4. Validate data integrity, then orchestrate a phased cutover.

### 30. `/RIPPLE [decision]`
* **Description:** Maps out the second-order, third-order, and long-term ripple effects of a near-term decision.
* **Example Input:** `/RIPPLE [Cutting our customer support budget by 30% to save cash now.]`
* **Example Output:** * *First-order:* Immediate cash savings.
    * *Second-order:* Longer queue wait times, employee burnout, and dropping review scores.
    * *Third-order:* Escalated customer churn, reduced customer lifetime value (LTV), and brand damage that costs double to repair.

### 31. `/PREMORTEM [plan]`
* **Description:** Assumes a project has completely failed in the future, and works backward to identify the causes.
* **Example Input:** `/PREMORTEM [Launching a premium podcast network next month.]`
* **Example Output:** "The project failed because of a lack of listener acquisition channels, underestimating the time commitment required to maintain high production quality, and a lack of clear monetization pathways."

### 32. `/MINTEST [project]`
* **Description:** Designs the absolute smallest, cheapest, Minimum Viable Product (MVP) model to validate an idea within one week.
* **Example Input:** `/MINTEST [An AI-driven custom wardrobe planning app.]`
* **Example Output:** Set up a simple Typeform requesting style preferences, manually curate a PDF lookbook using existing free AI tools, email it to 20 people, and see if they will pay $5 via a Stripe link for the manual curation.

---

## 6. Category 4: Learn & Understand (Commands 33–43)

### 33. `/ELI10 [topic]`
* **Description:** Explains a highly complex or advanced concept using a narrative style easily understood by a ten-year-old child.
* **Example Input:** `/ELI10 [Quantum Computing]`
* **Example Output:** "Regular computers use light switches that can only be turned on or off. Quantum computers use magic switches that can be both on AND off at the same time, allowing them to solve giant puzzles incredibly fast."

### 34. `/PRIMER [topic]`
* **Description:** Generates an accelerated, high-density crash course on a topic, mapping its core frameworks and parameters.
* **Example Input:** `/PRIMER [Behavioral Economics]`
* **Example Output:** Outlines foundational principles: Loss Aversion, Nudge Theory, Bounded Rationality, Heuristics, and Anchoring Effects, giving you a functional base knowledge level.

### 35. `/MYTHS [topic]`
* **Description:** Identifies and corrects common misconceptions and widespread false beliefs surrounding a topic.
* **Example Input:** `/MYTHS [Weight Loss]`
* **Example Output:** Debunks myths like "carbs make you fat automatically" or "targeted fat burning is possible," replacing them with scientific principles like caloric deficits and metabolic baseline realities.

### 36. `/ANALOGY [concept]`
* **Description:** Connects an abstract, difficult concept to a familiar real-world object or scenario through an analogy.
* **Example Input:** `/ANALOGY [An API (Application Programming Interface)]`
* **Example Output:** "An API is like a waiter in a restaurant. You (the user) sit at the table and look at the menu. The kitchen (the server) prepares the food. The waiter takes your order to the kitchen and brings the food back to you."

### 37. `/QUIZ [topic]`
* **Description:** Generates a five-question conceptual diagnostic quiz with an answer key to test retention on a topic.
* **Example Input:** `/QUIZ [Git Version Control basics]`
* **Example Output:** Generates five multiple-choice questions focusing on `git commit`, `git merge`, staging areas, and branching mechanisms, complete with detailed answers.

### 38. `/COMPARE [A vs B]`
* **Description:** Creates a comparative breakdown analyzing the distinct operational differences between two related concepts.
* **Example Input:** `/COMPARE [REST API vs GraphQL]`
* **Example Output:** Compares endpoints, over-fetching data patterns, performance, flexibility, and structure in a side-by-side analytical format.

### 39. `/PREREQ [topic]`
* **Description:** Maps out the foundational knowledge stack required before a student can realistically master an advanced field.
* **Example Input:** `/PREREQ [Machine Learning Engineering]`
* **Example Output:** Pre-requisites include: Linear Algebra, Calculus, Probability & Statistics, Proficiency in Python, and Fundamental Data Structures.

### 40. `/SUM3 [text]`
* **Description:** Distills long text documents into exactly three high-impact bullet points containing the core thesis.
* **Example Input:** `/SUM3 [Paste 3 pages of economic analysis text]`
* **Example Output:** * Inflation indexes expanded by 0.4% month-over-month.
    * Consumer spending remains resilient despite macro headwinds.
    * Interest rate reductions are unlikely before Q4 based on Fed language.

### 41. `/GLOSSARY [topic]`
* **Description:** Builds a terminology index defining the foundational jargon and acronyms for a domain.
* **Example Input:** `/GLOSSARY [Real Estate Syndication]`
* **Example Output:** Defines terms like LPs (Limited Partners), GPs (General Partners), Pref Rate (Preferred Return), Waterfall Structure, and IRR (Internal Rate of Return).

### 42. `/ASKBETTER [topic]`
* **Description:** Reveals the deeper, highly strategic questions you *should* be asking about a topic instead of surface-level ones.
* **Example Input:** `/ASKBETTER [Starting an e-commerce brand]`
* **Example Output:** Stop asking "What should I name my store?" Start asking: "What is my customer acquisition cost (CAC) relative to lifetime value? What are my supply chain single-points-of-failure?"

### 43. `/MENTALMODEL [topic]`
* **Description:** Unpacks the singular, high-leverage mental framework best suited to understanding or navigating a topic.
* **Example Input:** `/MENTALMODEL [Productivity management]`
* **Example Output:** Explains the **Eisenhower Matrix** (Urgent vs. Important Framework), illustrating how to prioritize strategic growth over reactive fires.

---

## 7. Category 5: Plan & Organize (Commands 44–54)

### 44. `/WEEK [priorities]`
* **Description:** Transforms raw priority inputs into a structured weekly schedule framework.
* **Example Input:** `/WEEK [Finish client brief, Go to gym 3x, Prep tax filing]`
* **Example Output:** Distributes priorities across Monday through Friday blocks, setting optimal energetic times for focus tasks versus administration.

### 45. `/MILESTONES [goal + deadline]`
* **Description:** Breaks down a long-range goal into a sequence of weekly checkpoints.
* **Example Input:** `/MILESTONES [Launch portfolio website + 4 weeks]`
* **Example Output:** * Week 1: Wireframes and copy finalized.
    * Week 2: Development and asset integration.
    * Week 3: Responsive testing and debugging.
    * Week 4: DNS routing and production deployment.

### 46. `/PACK [trip]`
* **Description:** Generates a highly comprehensive packing list tailored to a destination's climate, activity level, and duration.
* **Example Input:** `/PACK [5 days hiking in rainy Pacific Northwest in autumn]`
* **Example Output:** Categorizes items into moisture-wicking layers, navigation gear, waterproof packs, emergency supplies, and specialized trail footwear.

### 47. `/SCHEDULE [event + duration]`
* **Description:** Generates a timed schedule for an event or intense deep-work block down to the minute.
* **Example Input:** `/SCHEDULE [Half-day team planning workshop + 4 hours]`
* **Example Output:** Allocates time blocks for icebreakers, retrospective analysis, goal alignment sprints, and debriefing.

### 48. `/ROUTINE [goal]`
* **Description:** Architects an optimal, sustainable daily routine built around achieving a specific long-term target.
* **Example Input:** `/ROUTINE [Writing a non-fiction book while working full-time]`
* **Example Output:** Schedules a morning deep-work block (5:30 AM - 7:00 AM) dedicated purely to writing, combined with evening outlining and editing routines.

### 49. `/PRIORITIZE [list]`
* **Description:** Evaluates a chaotic, unorganized task list and reorders it by immediate impact and urgency.
* **Example Input:** `/PRIORITIZE [fix small CSS bug, fix checkout page crash, update bio, call candidate]`
* **Example Output:** 1. Fix checkout page crash (Critical revenue path).
    2. Call candidate (High priority timeline).
    3. Fix small CSS bug (Low friction visual fix).
    4. Update bio (Low impact administration).

### 50. `/MEALS [ingredients/constraints]`
* **Description:** Creates a week-long dinner meal plan structured cleanly around ingredients on-hand or dietary restrictions.
* **Example Input:** `/MEALS [High protein, low carb, no seafood, prep time under 30 mins]`
* **Example Output:** Generates a Monday-to-Sunday dinner guide focusing on chicken, turkey, beef, and plant proteins paired with leafy greens, emphasizing quick prep times.

### 51. `/AGENDA [topic + duration]`
* **Description:** Generates a strict, high-efficiency corporate meeting agenda to keep discussions focused and on track.
* **Example Input:** `/AGENDA [Q3 product roadmap alignment + 45 minutes]`
* **Example Output:** * 00-05 mins: Strategic objective setting.
    * 05-25 mins: Review of product engineering timelines.
    * 25-40 mins: Resource allocation discussion.
    * 40-45 mins: Action-item assignment.

### 52. `/PREPTIME [event + time available]`
* **Description:** Creates an optimized countdown preparation plan leading up to a major event or deadline.
* **Example Input:** `/PREPTIME [Major keynote speech tomorrow morning + 3 hours tonight]`
* **Example Output:** Allocates 60 minutes to slide synchronization, 60 minutes to full verbal run-throughs, 30 minutes to edge-case question prep, and 30 minutes to wind-down rest.

### 53. `/ORDER [tasks]`
* **Description:** Evaluates a list of loose tasks and sequences them chronologically based on dependencies.
* **Example Input:** `/ORDER [paint walls, buy paint, tape baseboards, sand drywall]`
* **Example Output:** 1. Buy paint.
    2. Sand drywall.
    3. Tape baseboards.
    4. Paint walls.

### 54. `/CHECKLIST [task]`
* **Description:** Generates an actionable, step-by-step standard operating checklist to execute a process without errors.
* **Example Input:** `/CHECKLIST [Publishing a WordPress blog post]`
* **Example Output:** Includes checks for keyword optimization, image alt tag validation, broken internal link scans, URL permalink cleanups, category tagging, and social snippet scheduling.

---

## 8. Category 6: Brainstorm (Commands 55–65)

### 55. `/IDEAS20 [topic]`
* **Description:** Generates twenty diverse, creative, and non-obvious ideas for a given topic or problem space.
* **Example Input:** `/IDEAS20 [Marketing campaigns for an eco-friendly water bottle]`
* **Example Output:** Delivers a comprehensive list of 20 unique marketing strategies, ranging from targeted guerrilla marketing activations to data-driven social proof campaigns.

### 56. `/GIFTS [person + occasion + budget]`
* **Description:** Provides highly customized, meaningful gift ideas based on personal context and financial boundaries.
* **Example Input:** `/GIFTS [My father who loves history and coffee + Father's Day + $50]`
* **Example Output:** Suggests options like a premium single-origin coffee subscription from historical bean origins, or a personalized book featuring front-page historical news from his birth year.

### 57. `/NAMES [thing + vibe]`
* **Description:** Brainstorms unique name options for a company, app, or product based on a preferred brand vibe.
* **Example Input:** `/NAMES [A sleep app + minimalist, premium, tech]`
* **Example Output:** Somnia, Restr, AuraSleep, Nocturn, Nod, Zephyr.

### 58. `/UNUSUAL [problem]`
* **Description:** Generates ten highly unconventional, counter-intuitive, or lateral-thinking solutions to a stubborn problem.
* **Example Input:** `/UNUSUAL [Increasing attendance at a boring monthly mandatory company all-hands meeting]`
* **Example Output:** Outlines 10 alternative ideas, such as running the meeting in reverse order starting with the Q&A, or hiding a prize code inside the monthly data slide deck.

### 59. `/ANGLE [topic]`
* **Description:** Uncovers overlooked narratives or creative angles on a saturated topic to help content stand out.
* **Example Input:** `/ANGLE [Remote work tips]`
* **Example Output:** "Instead of focusing on productivity tools, explore the psychological impact of losing the 'liminal space' of the daily commute, and how to build a fake commute to maintain a healthy boundary."

### 60. `/COMBINE [A + B]`
* **Description:** Mashes two completely unrelated fields or items together to create five innovative hybrid concepts.
* **Example Input:** `/COMBINE [Fitness tracking + Medieval roleplaying games]`
* **Example Output:** Provides ideas like a mobile app where your real-world daily steps grant armor and experience points to your digital character to fight raid bosses with friends.

### 61. `/METAPHOR [concept]`
* **Description:** Brainstorms powerful, vivid metaphors to help explain complex or dry ideas in a presentation or speech.
* **Example Input:** `/METAPHOR [Technical Debt]`
* **Example Output:** "Technical debt is like cooking in a restaurant kitchen without washing the dishes. It makes things faster at first, but eventually, the unwashed pans pile up until the entire kitchen grinds to a halt."

### 62. `/STARTERS [topic]`
* **Description:** Generates engaging, non-boring conversation starters or icebreakers customized to a specific event topic or demographic.
* **Example Input:** `/STARTERS [A networking event for AI startup founders]`
* **Example Output:** "What's the most surprising emergent behavior you've seen your model exhibit?" or "What's one task you refuse to let AI automate in your personal life?"

### 63. `/JOURNAL10 [theme]`
* **Description:** Provides ten deeply reflective, customized self-discovery journal prompts built around a specific theme.
* **Example Input:** `/JOURNAL10 [Career pivot anxiety]`
* **Example Output:** Generates 10 thought-provoking questions focusing on unpacking imposter syndrome, clarifying identity separate from job titles, and assessing true financial downside tolerances.

### 64. `/AS [role + problem]`
* **Description:** Looks at a problem through the professional lens, priorities, and frameworks of a specific role (e.g., an architect, a military general, a chef).
* **Example Input:** `/AS [Chef + Designing a digital customer onboarding flow]`
* **Example Output:** "Look at it like a tasting menu. You don't serve the heavy main course immediately. You start with an amuse-bouche (a simple, instant win), build the flavor profile step-by-step, and clean the palate between steps."

### 65. `/CHILD [problem]`
* **Description:** Re-evaluates a complex problem through the curious, unfiltered, first-principles curiosity of a child to bypass over-engineered solutions.
* **Example Input:** `/CHILD [Why do people stop using our complex enterprise accounting software?]`
* **Example Output:** "Because it looks ugly, it makes their head hurt, and it feels like doing extra homework instead of playing outside."

---

## 9. Category 7: Work & Career (Commands 66–76)

### 66. `/INTERVIEWQ [questions]`
* **Description:** Prepares structured, bulletproof talking points to confidently answer specific, tough job interview questions.
* **Example Input:** `/INTERVIEWQ [Why did you leave your last role after only 6 months?]`
* **Example Output:** Formulates a response framework focused on architectural alignment, an unexpected shift in company direction, and a desire to bring skills to a team positioned for long-term growth.

### 67. `/RESUMEBULLET [bullet]`
* **Description:** Transforms weak, passive resume descriptions into high-impact, metrics-driven accomplishment statements using the X-Y-Z formula.
* **Example Input:** `/RESUMEBULLET [I was responsible for managing the company's social media accounts and posting updates.]`
* **Example Output:** "Optimized company social media footprint, driving a 42% year-over-year expansion in audience engagement and capturing 12k new organic leads through automated content frameworks."

### 68. `/ASKINTERVIEWER [role + company type]`
* **Description:** Generates smart, high-signal questions to ask an interviewer that demonstrate deep strategic thinking and industry acumen.
* **Example Input:** `/ASKINTERVIEWER [Senior Product Manager + Series B Fintech Startup]`
* **Example Output:** "How does your team navigate shifting regulatory boundaries while maintaining a rapid product experimentation cycle? What does success look like for this role in the first 90 days?"

### 69. `/NEGOTIATE [the ask]`
* **Description:** Scripts a professional negotiation response for an offer or raise, balancing assertiveness with collaborative professionalism.
* **Example Input:** `/NEGOTIATE [Asking for a base salary increase from $90k to $100k based on market data]`
* **Example Output:** "Thank you for the offer. I am thrilled about the opportunity. Given my specialized experience and market alignment metrics for this region, I would love to discuss adjusting the base salary to $100,000 to finalize things."

### 70. `/RECONNECT [person + context]`
* **Description:** Drafts a low-friction, warm message to reactivate a professional relationship on LinkedIn or email after months or years of silence.
* **Example Input:** `/RECONNECT [Former colleague Mark + saw his company raised a new round]`
* **Example Output:** "Hi Mark, it's been a while! I just saw the news about your company's latest funding round—huge congratulations to you and the team. Would love to catch up over coffee sometime soon to hear how things are going."

### 71. `/GAP [reason]`
* **Description:** Explains an employment gap on a resume or in an interview in a positive, professional manner that emphasizes skill development or personal growth.
* **Example Input:** `/GAP [Took 12 months off to care for an ailing family member]`
* **Example Output:** "I stepped away from the workforce for 12 months to manage a critical family health matter. During this period, I successfully handled complex coordination and logistics under pressure, while staying current on industry trends via continuing education."

### 72. `/WINS5 [notes]`
* **Description:** Distills raw, messy weekly notes or logs into exactly five polished, professional accomplishments ready for a review or status report.
* **Example Input:** `/WINS5 [Fixed a bunch of bugs, helped Sarah clean up some code, sat in on client pitches, worked on the database migration plan]`
* **Example Output:** 1. Resolved multiple critical system bugs to improve software stability.
    2. Mentored team members on code optimization to reduce technical debt.
    3. Contributed technical insight during client discovery pitches.
    4. Engineered the baseline planning architecture for the upcoming database migration.
    5. Maintained high operational throughput across all assigned sprint items.

### 73. `/ONEONONE [topic]`
* **Description:** Prepares a structured agenda and talking points for a productive 1-on-1 meeting with your manager.
* **Example Input:** `/ONEONONE [Discussing burnout and adjusting project workload]`
* **Example Output:** Structures the conversation around project prioritization, identifying bottlenecks, and proposing a sustainable resource allocation plan to maintain quality deliverables.

### 74. `/SELFREVIEW [paste]`
* **Description:** Transforms raw personal logs and notes into a formal, highly professional self-evaluation narrative.
* **Example Input:** `/SELFREVIEW [I think I did good this year, worked hard on the website redesign, and handled client issues well.]`
* **Example Output:** "Throughout this performance cycle, I drove the strategic execution of our website redesign project, optimizing user flows and system performance. Additionally, I proactively managed client relations, improving satisfaction scores through rapid resolution of issues."

### 75. `/IDONTKNOW [situation]`
* **Description:** Provides professional alternatives to saying "I don't know" during high-stakes client meetings or executive briefings.
* **Example Input:** `/IDONTKNOW [A client asks when a specific niche feature will be fully deployed but you aren't sure.]`
* **Example Output:** "That is an excellent question. Let me confirm the exact deployment timeline parameters with our engineering leads to ensure I give you accurate details. I will follow up with you by the end of the day."

### 76. `/RAISE [context]`
* **Description:** Formulates a compelling, business-justified script to formally ask your manager for a compensation adjustment.
* **Example Input:** `/RAISE [Increased team output by 20% over the last year as a team lead]`
* **Example Output:** "Based on the team's expanded output over the past 12 months, where we drove a 20% increase in production velocity and hit all target KPIs under my leadership, I would like to request a review of my current compensation to reflect these contributions."

---

## 10. Category 8: Content & Social (Commands 77–87)

### 77. `/HOOK [topic]`
* **Description:** Generates five highly engaging, scroll-stopping opening lines optimized for social media platforms.
* **Example Input:** `/HOOK [The importance of setting strict boundaries at work]`
* **Example Output:**
    1. I used to think working late was a badge of honor. Now I see it as a warning sign.
    2. The most productive thing I ever did for my career felt like professional suicide.
    3. If you don't set your work boundaries, your company will gladly set them for you.

### 78. `/CAPTION [photo/topic]`
* **Description:** Drafts a concise, engaging social media caption complete with context-appropriate hashtags.
* **Example Input:** `/CAPTION [A photo of my clean, newly organized home office setup]`
* **Example Output:** "Clean space, clear mind. Ready to tackle this week's deep-work blocks. 💻✨ #HomeOffice #Productivity #Workspace"

### 79. `/THREAD [idea]`
* **Description:** Deconstructs a complex core idea into a highly engaging, six-part social media thread layout.
* **Example Input:** `/THREAD [How to build an audience from absolute scratch on LinkedIn]`
* **Example Output:** Generates a structured 6-tweet/post sequence starting with a strong hook, followed by actionable steps, common mistakes, a personal example, and a concluding call-to-action.

### 80. `/CARO [topic]`
* **Description:** Formulates a slide-by-slide text storyboard and visual outline for an educational carousel post.
* **Example Input:** `/CARO [3 simple frameworks to stop procrastinating]`
* **Example Output:** Breaks down the content into Slide 1 (Hook), Slide 2 (Problem), Slides 3-5 (Framework breakdowns), and Slide 6 (Call-to-Action).

### 81. `/REPURPOSE [post]`
* **Description:** Transforms a single text input block into three distinct formatting styles (e.g., a formal newsletter snippet, an punchy social post, and a bulleted outline).
* **Example Input:** `/REPURPOSE [A short paragraph on the benefits of drinking water early in the morning]`
* **Example Output:** Delivers a structured breakdown containing a polished email newsletter section, a punchy social media post, and a quick-read bulleted summary.

### 82. `/CTA [post]`
* **Description:** Generates three unique calls-to-action tailored to drive engagement, link clicks, or discussion.
* **Example Input:** `/CTA [A post sharing a free budget tracking spreadsheet template]`
* **Example Output:**
    1. Comment "BUDGET" below, and I'll DM you the direct template link instantly!
    2. What's your biggest challenge when it comes to tracking monthly expenses? Let's discuss in the comments.
    3. Grab your free copy via the link in my bio before the resource updates next week!

### 83. `/BIO [details + vibe]`
* **Description:** Drafts a concise personal bio across three distinct professional styles based on your details.
* **Example Input:** `/BIO [Software Engineer, loves building open source tools, based in Austin + Minimalist, Professional, Playful]`
* **Example Output:** Generates three tailored options, ranging from an ultra-clean corporate bio to a lighthearted, personality-driven profile snippet.

### 84. `/SUBJECT [email/post]`
* **Description:** Generates five high-open-rate subject lines or titles based on your content context.
* **Example Input:** `/SUBJECT [An internal newsletter announcing a new remote-work stipend allocation]`
* **Example Output:**
    * Good news: New remote-work stipend updates inside 💸
    * How to claim your home office allowance this month
    * Important updates to our remote work benefits program

### 85. `/CONTRARIAN [topic]`
* **Description:** Formulates a sharp, counter-intuitive perspective on a mainstream topic that remains logically sound and defensible.
* **Example Input:** `/CONTRARIAN [Networking and building professional connections]`
* **Example Output:** "Stop networking. It's a waste of time. Most networking events are just rooms full of desperate people looking to take value. Focus instead on building exceptional things in public—high-value people will seek you out."

### 86. `/SHORTPOST [idea]`
* **Description:** Compresses an idea into a punchy, high-impact social media post under 100 words.
* **Example Input:** `/SHORTPOST [Consistency beats intensity every single time in learning new skills]`
* **Example Output:** "Intensity builds headlines. Consistency builds skills. Practicing a language for 15 minutes every day beats cramming for 5 hours once a month. Small, daily efforts compound quietly into mastery. Stop waiting for the perfect block of time. Start small, but start today."

### 87. `/COMMENT [post]`
* **Description:** Generates three thoughtful, value-adding commentary replies to post in a professional discussion thread.
* **Example Input:** `/COMMENT [A post arguing that AI will completely replace software developers within two years.]`
* **Example Output:** Provides options that balance agreement with nuanced counterpoints, highlighting that AI shifts the developer's role from writing syntax to system architecture and problem definition.

---

## 11. Category 9: Meetings & Notes (Commands 89–99)

*(Note: Numbering directly mirrors source asset index parameters.)*

### 89. `/MEETINGNOTES [transcript]`
* **Description:** Processes a chaotic, unformatted meeting transcript and structures it into polished corporate minutes.
* **Example Input:** `/MEETINGNOTES [John said we need to finish the API. Sarah noted the budget is tight. We decided to delay the UI polish till next month.]`
* **Example Output:** Parses the input into an organized document with clear meeting objectives, discussion summaries, and strategic outcomes.

### 90. `/ACTIONITEMS [notes]`
* **Description:** Extracts clear action items, deadlines, and owners from a block of meeting notes.
* **Example Input:** `/ACTIONITEMS [Mark needs to send the contract by Friday. Jane will review the design changes by Monday.]`
* **Example Output:**
    * **Action Item:** Send out contract draft | **Owner:** Mark | **Deadline:** Friday
    * **Action Item:** Review updated design changes | **Owner:** Jane | **Deadline:** Next Monday

### 91. `/STANDUP [yesterday + today + blockers]`
* **Description:** Formats your daily updates into a clean, professional asynchronous standup report.
* **Example Input:** `/STANDUP [Fixed login bug + writing documentation + waiting on API keys from DevOps]`
* **Example Output:**
    * **Yesterday:** Resolved critical bug within login authentication system.
    * **Today:** Compiling comprehensive architecture documentation.
    * **Blockers:** Awaiting API credential provisioning from DevOps team.

### 92. `/RECAP [meeting]`
* **Description:** Distills an entire meeting down into an ultra-concise, five-line summary for rapid review.
* **Example Input:** `/RECAP [Paste extensive multi-paragraph meeting notes]`
* **Example Output:** Returns an exact 5-line summary covering the meeting's primary focus, key decisions, resource changes, next milestones, and immediate next steps.

### 93. `/DECISIONS [notes]`
* **Description:** Scans meeting notes and pulls out only the explicit decisions, agreements, and policies established during the discussion.
* **Example Input:** `/DECISIONS [We talked about pricing and decided to go with $19/mo instead of $29/mo. We also agreed to work remotely on Fridays.]`
* **Example Output:**
    * **Decision:** Monthly subscription pricing set at $19/mo.
    * **Policy:** Friday operations shifted to fully remote work status.

### 94. `/QUESTIONS [topic]`
* **Description:** Generates a list of strategic questions to ask during an upcoming meeting about a specific topic to prevent oversights.
* **Example Input:** `/QUESTIONS [Vendor contract renewal discussion]`
* **Example Output:** "Are there any hidden data migration fees if we terminate early? What are the service level agreements (SLAs) for system uptime, and what are the penalties for breaches?"

### 95. `/STATUS [project]`
* **Description:** Formats project updates into a clean, executive-ready progress overview.
* **Example Input:** `/STATUS [Project Alpha is mostly on track, database is done, frontend is delayed by a week, budget is green.]`
* **Example Output:** Generates a clear executive status report with project health indicators (On-Track/Delayed), completed milestones, active bottlenecks, and financial status.

### 96. `/BRIEFME [topic + paste]`
* **Description:** Reviews extensive context material and generates a concise, high-density brief to prepare you for a meeting.
* **Example Input:** `/BRIEFME [Client sync + Paste client company profile and project history]`
* **Example Output:** Summarizes the client's business model, key past friction points, project status, and immediate conversation goals.

### 97. `/DEBRIEF [meeting]`
* **Description:** Evaluates an event or project retrospective to clarify what went well and identify what needs to be fixed.
* **Example Input:** `/DEBRIEF [The workshop went well, great engagement, but the audio cut out twice and we ran out of time for Q&A.]`
* **Example Output:** Organizes the feedback into successes (high engagement, strong content reception) and action items for improvement (test audio equipment, allocate 15 more minutes for Q&A).

### 98. `/TLDR [paste]`
* **Description:** Extracts the most important takeaway from a long block of text into a single, high-impact sentence.
* **Example Input:** `/TLDR [Paste long article detailing changing compliance regulations in European financial technology infrastructure]`
* **Example Output:** **TL;DR:** New EU fintech regulations mandate stricter user data isolation and audit protocols starting Q4.

### 99. `/RETRO [project]`
* **Description:** Formats a project retrospective using a clear framework: What worked, what didn't, and what are the next steps?
* **Example Input:** `/RETRO [Marketing push: social ads brought traffic but low conversions, email list performed great, landing page loaded slowly.]`
* **Example Output:**
    * **What Worked:** Email marketing campaigns delivered high conversion metrics.
    * **What Didn't:** Social advertising performance was impacted by slow landing page load times.
    * **Next Steps:** Optimize landing page speed and iterate on social ad targeting.

---

## 12. Pro-Tips for Advanced Workflows

1.  **Chain of Command Macroing:** You can chain commands sequentially in a single prompt block to perform multi-stage processing:
    ```text
    First execute /PROOF on the text below, then take that output and apply /SIMPLIFY:
    [Payload text...]
    ```
2.  **Persistent Claude Project Memory:** If you use Claude Pro, create a **Project** and paste the initialization system prompt directly into the project instructions. This makes all 99 commands natively active across every chat session inside that project folder without requiring re-initialization.
3.  **Context-Aware Guardrails:** For commands requiring precise domain insights (e.g., `/ASKINTERVIEWER`), provide a few sentences of company background details along with the payload to help Claude customize the response to your industry.

---

## 13. Common Mistakes & Pitfalls

* **Omitting the Square Brackets:** If you forget to wrap your payload in `[...]`, Claude may get confused between where the command instruction ends and your text begins. Always use the structural template: `/COMMAND [your text here]`.
* **Session Context Loss:** In long chat sessions, Claude may slowly drift away from its initialization parameters. If Claude responds with casual conversation instead of the crisp, direct output of a command, simply copy and paste the initial setup prompt back into the chat to reset its behavior.
* **Overloading Commands:** Avoid stuffing multiple unrelated topics into a single command payload. Keep your inputs focused to ensure the highest quality results.

---

## 14. Troubleshooting & FAQ

**Q: Claude is giving me conversational filler like "Sure, I can help with that!" How do I make it stop?** **A:** Re-issue the command and append the instruction: `Output ONLY the processed result. Zero conversational filler.` If the issue persists, start a fresh chat session and ensure the system prompt is initialized correctly.

**Q: Can I customize these commands or add my own?** **A:** Absolutely! The system is fully customizable. You can modify the initialization prompt to add new commands, like `/TWEET` or `/CODEGEN`, following the exact same format.

**Q: Which version of Claude works best with this guide?** **A:** **Claude 3.5 Sonnet** and **Claude 3 Opus** deliver the highest compliance scores when following complex system prompts and slash-command structures.

**Q: Why does the numbering jump from 87 straight to 89 in the final section?** **A:** This is a small layout typo in the original cheat sheet asset, which lists index number 93 twice and skips 88. This guide maintains the exact structural terms of the source asset to ensure seamless cross-referencing.
