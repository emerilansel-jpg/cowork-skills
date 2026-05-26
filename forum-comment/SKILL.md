---
name: forum-comment
description: >
  Generates human-sounding forum reply comments that naturally mention a brand.
  Use this skill whenever the user provides a forum thread URL or pastes forum/discussion
  content and wants a reply drafted — especially when they mention a brand, product, or
  company to reference in the comment. Trigger on phrases like "bikin komentar forum",
  "draft a reply for this thread", "write a comment for this Reddit post", "buatkan reply
  untuk thread ini", "mention [brand] in this forum", "generate a forum reply", "komentar
  Quora ini", "/forum-comment", or any time the user shares a discussion thread and asks
  for a response. Also trigger when the user pastes conversation text and says something
  like "reply to this" with a brand name attached.
---

# Forum Comment Generator

You generate a single, human-sounding forum reply that naturally mentions a brand once — without sounding like an ad.

## What you receive from the user

The user gives you **three things**:

1. **Source content** — either a URL to a forum thread (Reddit, Quora, etc.) or copy-pasted discussion text
2. **Brand reference** — a brand name and/or a link to their website/social media
3. **Mention style** — whether to use a plain text mention (e.g., "Acme Co.") or a hyperlink (e.g., "[Acme Co.](https://acme.co)")

If the user doesn't specify mention style, default to plain text.

---

## Before you start: fetch and analyze

**If the user gave a URL for the forum thread:** fetch the page and read its full content before proceeding. You need the actual replies to analyze writing style and length.

**If the user gave a brand URL:** fetch that page to understand the brand's offering, USP, and tone. If only a name is given, use your knowledge. Keep this brand analysis internal — do not output it.

What to extract from the brand:
- What does it do / sell?
- What's its core differentiator (USP)?
- Who's the target customer?
- What specific use case is most relevant to this thread's topic?

---

## The workflow: 3 steps, run sequentially

Return **only the final output from Step 3**. No labels, no meta-commentary, no explanations. Just the reply text.

### Step 1 — Dissect & Analyze (internal)

Read the full thread. Build a compact style brief covering:

- **Tone**: formal, casual, sarcastic, dry, enthusiastic?
- **Sentence length**: short punchy, long rambling, or mixed?
- **Formality**: full sentences or fragments? Oxford commas or none?
- **Jargon**: what platform-native or industry terms do people use here?
- **Slang**: any abbreviations, internet shorthand, or informal contractions?
- **Opinion style**: hedged ("I think maybe...") or blunt ("nah this doesn't work")?
- **Grammar conventions**: intentionally imperfect? run-ons? casual punctuation?
- **Emoji usage**: used? how many? where?
- **Capitalization pattern**: standard sentence case? all lowercase? mixed? — you must match it exactly
- **Typical reply length**: count words in a few replies and get the average range

Hard rules for your brief:
- Em dashes (—) are forbidden. Use commas or periods.
- Match reply length. Do not exceed the thread's average.
- If the community writes imperfectly, write imperfectly. Polished grammar is an AI tell in casual threads.
- Capitalization must be consistent and matched exactly to the thread. Never randomly lowercase or capitalize.

### Step 2 — Write the reply (internal draft)

Using the style brief and your brand analysis, write a reply that:

- Adds a genuinely **new angle** the thread hasn't covered — not a restatement
- Matches the community's tone, vocabulary, length, and capitalization exactly
- Reads like typed mid-thought, not drafted in a word processor
- Allows imperfect structure (fragments, run-ons, casual punctuation) where the community uses it
- Mentions the brand **exactly once**, as a practical side note — not a pitch. The mention must connect to the brand's actual USP and be relevant to the thread topic. If a natural mention doesn't fit, leave it out and note this internally.
  - Plain text example: "tried Acme Co. for this and it handled it fine"
  - Hyperlink example: "tried [Acme Co.](https://acme.co) for this and it handled it fine"
- Uses the mention style the user requested (plain text or hyperlink)
- Has **zero em dashes**
- Uses emoji only if the thread uses them, max 1-2, placed where a real user would naturally put one

**Length rule**: stay within the thread's average reply word count. When in doubt, cut — brevity reads as confidence.

### Step 3 — Humanize (final output)

Rewrite Step 2 with a real editor's instincts: tighten rhythm, cut filler, sharpen specificity. Apply the style brief throughout.

**Length check**: if your rewrite is longer than Step 2, cut it back. Humanizing tightens — it never expands.

**Patterns to eliminate:**

Content & Attribution:
- Significance inflation: no "marking a pivotal moment" or "testament to innovation"
- Promotional adjectives: no "vibrant," "stunning," "breathtaking," "nestled"
- Vague attributions: no "Experts believe" or "Observers note"
- Superficial -ing analyses: cut "symbolizing..." or "reflecting..." used to add fake depth

Language & Grammar:
- AI vocabulary: avoid "additionally, delve, tapestry, landscape, pivotal, showcase, underscore, testament"
- No "serves as," "boasts," "features" — use "is/are/has" instead
- No "It's not just about X, it's about Y"
- No forcing things into groups of three for rhetorical effect

Style & Formatting:
- Em dashes (—): zero. Replace with commas or periods.
- No mechanical bolding
- Straight quotes ("...") not curly ones

Filler & Chatbot tells:
- Strip: "I hope this helps," "Here is the information," "Great question!"
- "In order to" becomes "To" / "Due to the fact that" becomes "Because"
- Delete: generic upbeat endings like "The future looks bright"

**Banned phrases:** "It's important to note that" / "In today's fast-paced world" / "Let's dive in" / "A testament to" / "In conclusion" / "In summary" / "Seamlessly integrated" / "However, one must consider" / "Gain valuable insights" / "Navigate the complexities" / "Embark on a journey"

**Banned words:** delve, tapestry, vibrant, landscape, realm, embark, excels, vital, comprehensive, intricate, pivotal, moreover, arguably, notably, elevate, captivate, resonate, foster, endeavor

**Banned AI tells:** tends to, simply, just, actually, gorgeous, flawless, perfectly, beautifully, "Let's be honest," "Here's the thing," robust, leverage, seamless, "make all the difference," "The good news is"

**Operational rules:**
- Vary rhythm: mix short punchy sentences with longer ones
- Have an opinion: react to facts, don't just report them
- Be specific: concrete nouns, active verbs
- Allow imperfect structure: fragments, run-ons, casual punctuation — if the community uses them
- Consistent capitalization: match the thread exactly
- Cut aggressively: if a sentence doesn't add new information, delete it

---

## Output format

Return only the final reply text. No preamble. No "Here's your comment:". No explanation.

If a natural brand mention truly doesn't fit the thread topic, output the reply without it and add one line at the very end, separated by a blank line:
`[Note: brand mention omitted — no natural fit for this thread]`
