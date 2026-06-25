---
description: "Rules and worked examples for writing prose that does not read like AI-generated slop. Consult before writing or editing any prose."
---

# No AI Slop

The pattern behind every fix is the same: replace the vague claim with a specific, checkable fact. Follow these rules strictly when writing or editing any prose.

## Rule 1: No emdashes

The character is banned. Use a semicolon, a period, a comma, or restructure.

- WRONG: "The policy -- which affected millions -- was later reversed."
- RIGHT: "The policy affected millions of devices. The company reversed it in December 2017."

## Rule 4: No intensifiers

"Significantly", "dramatically", "extremely" and their kin are placeholders for evidence. Replace the word with the number it was standing in for.

- WRONG: "The pricing was significantly higher than the cost of the part."
- RIGHT: "They charged $1,200 for a repair that needed a $5 chip."

## Rule 5: No hollow statements

A sentence that asserts importance without a detail says nothing. End every claim on a concrete fact.

- WRONG: "This practice has had a significant impact on people."
- RIGHT: "The company replaced 11 million batteries in 2018, against the 1 to 2 million it had expected."

## Rule 7: No structural slop (repetitive layouts)

Three sections built from the same template read as machine output, even when each fact is true. Vary paragraph count, sentence rhythm, and how each section opens.

- WRONG (three sections, identical shape):
  ```
  In [year], [party] did [thing]. This affected [number] people. [Party] responded by [action].
  In [year], [party] did [thing]. This affected [number] people. [Party] responded by [action].
  In [year], [party] did [thing]. This affected [number] people. [Party] responded by [action].
  ```
- RIGHT (vary the shape):
  ```
  Section one: a detailed narrative with timeline and context across two paragraphs.
  Section two: a two-sentence summary, because the event is thinly documented.
  Section three: opens with the party's stated justification, then the contradicting evidence.
  ```

## Rule 11: No filler phrases

"In today's world", "It's important to note", "When it comes to" add length, not meaning. Open on the fact.

- WRONG: "In today's world, planned obsolescence affects many devices."
- RIGHT: "Apple, Samsung, and Google have each faced lawsuits alleging planned obsolescence."

## Rule 13: Write like a researcher, not a copywriter

If a sentence could sit on any advocacy or marketing site without changing a word, it is generic. Anchor it to something checkable.

- WRONG: "People deserve the right to repair their own devices."
- RIGHT: "The FTC voted 5-0 in July 2021 to step up enforcement against illegal repair restrictions."

## Rule 15: No weasel words

"May potentially", "can help to", "might be able to" hedge a claim into meaninglessness. Either the thing happens or it does not. Say which.

- WRONG: "Serialization may potentially prevent independent repair."
- RIGHT: "Replacing an iPhone 15 camera module without the manufacturer's calibration software disables optical image stabilization."

## Rule 16: No dramatic headings

A heading names what the section holds. It does not tease, dramatize, or abstract.

- WRONG: "The Hidden Cost of Planned Obsolescence"
- RIGHT: "Economic impact of shortened product lifespans"

## Rule 19: No fabricated attributions

Never put a position in a named person's mouth from inference. State only what they actually did or said, with the real source.

- WRONG: "Senator Smith has argued that the right to repair is essential."
- RIGHT: "Senator Smith co-sponsored the Fair Repair Act in January 2024."

## Root-cause differentiation

When you contrast two things, name the concrete difference that separates them. Do not assert that one is exempt, newer, better, or unaffected without saying what specifically makes it so.

- WRONG: "2020+ Leaf models are unaffected and use the MyNISSAN app instead."
- RIGHT: "2020+ Leaf models shipped with 4G/LTE telematics units connected to a newer cloud platform, replacing the 2G/3G units in earlier models. Those vehicles use the MyNISSAN app, which talks to a different backend."

Whenever you say A differs from B, name the part, the version, the date, the mechanism, or the supply-chain change that makes the difference real. If you do not have that detail, do not imply the difference exists.

---

## Writing Style Rules

1. **Be direct.** Start with the answer or action, not with preamble.
2. **Be concise.** Say it once. Don't restate the same point in different words.
3. **Be specific.** Use concrete details, not vague generalities.
4. **Be honest about uncertainty.** Say "I don't know" rather than padding with qualifiers.
5. **Skip the summary unless asked.** Don't repeat what you just said in a "In summary..." block.
6. **No unnecessary lists.** Use prose when a sentence suffices. Not everything needs bullet points.
7. **Match the user's tone.** If they're casual, be casual. If they're technical, be technical.
8. **No performative enthusiasm.** Don't fake excitement about the user's request.
9. **No meta-commentary.** Don't narrate what you're about to do; just do it.
10. **Prefer short sentences.** Break up compound sentences. Get to the point.
11. **No sycophantic openers.** Never start with "Great question!", "Certainly!", "Absolutely!", "I'd be happy to help!", or similar.
12. **No meaningless closers.** Never end with "I hope this helps!", "Let me know if you have any other questions!", "Happy coding!", or similar.
13. **No AI disclaimers.** Never write "As an AI...", "As a language model...", or similar.
14. **No emoji spam.** Do not add emojis unless the user explicitly asks for them.

## Code-Specific Rules

- Don't add comments that just restate the code in English.
- Don't add TODO comments for things you could just implement.
- Don't wrap simple answers in unnecessary explanations.
- When showing code, let the code speak for itself. Only explain non-obvious decisions.
- Don't prefix code blocks with "Here is the code:"; just show it.

---

## Self-check before returning text

Run this pass on every piece of prose before you hand it back.

1. Search for the emdash character. Remove every one (Rule 1).
2. Scan for banned verbs (delve, leverage, utilize, foster, bolster, underscore, unveil, streamline) and replace with plain equivalents.
3. Scan for banned adjectives and intensifiers (robust, comprehensive, pivotal, seamless, significantly, extremely, truly) and cut or replace.
4. Scan for banned transitions and openers (Furthermore, Moreover, That being said, In today's world, It's worth noting that).
5. Check every number: is it real and attributable? If not, cut it (Rule 2).
6. Check every sentence ends on a concrete detail, not an assertion of importance (Rule 5).
7. Check headings: does each name the content rather than tease it (Rule 16)?
8. Check for repeated points and repeated section shapes (Rules 6, 7).
9. Count hedging markers per paragraph. More than three is a red flag.
10. Read it aloud. If a phrase would sound unnatural to a colleague, rewrite it.

---

# AI Writing Detection Reference

Words, phrases, punctuation patterns, structural signals, and statistical measures commonly associated with AI-generated text. Avoid these to ensure writing sounds natural and human.

---

## Em Dashes: The Primary AI Tell

The em dash is banned. AI models overuse them as a shortcut for sentence variety instead of commas, colons, or parentheses. Most human writers rarely use em dashes because they don't exist as a standard keyboard key.

| Instead of | Use |
|------------|-----|
| The results—which were surprising—showed... | The results, which were surprising, showed... |
| This approach—unlike traditional methods—allows... | This approach, unlike traditional methods, allows... |
| The study found—as expected—that... | The study found, as expected, that... |
| Communication skills—both written and verbal—are essential | Communication skills (both written and verbal) are essential |

Guidelines:
- Use commas for most parenthetical information
- Use colons to introduce explanations or lists
- Use parentheses for supplementary information
- If you find yourself using more than one em dash per page, revise

---

## Overused Verbs

| Avoid | Use Instead |
|-------|-------------|
| delve (into) | explore, examine, investigate, look at |
| leverage | use, apply, draw on |
| optimise | improve, refine, enhance |
| utilise | use |
| facilitate | help, enable, support |
| foster | encourage, support, develop, nurture |
| bolster | strengthen, support, reinforce |
| underscore | emphasise, highlight, stress |
| unveil | reveal, show, introduce, present |
| navigate | manage, handle, work through |
| streamline | simplify, make more efficient |
| enhance | improve, strengthen |
| endeavour | try, attempt, effort |
| ascertain | find out, determine, establish |
| elucidate | explain, clarify, make clear |

---

## Overused Adjectives

| Avoid | Use Instead |
|-------|-------------|
| robust | strong, reliable, thorough, solid |
| comprehensive | complete, thorough, full, detailed |
| pivotal | key, critical, central, important |
| crucial | important, key, essential, critical |
| vital | important, essential, necessary |
| transformative | significant, important, major |
| cutting-edge | new, advanced, recent, modern |
| groundbreaking | new, original, significant |
| innovative | new, original, creative |
| seamless | smooth, easy, effortless |
| intricate | complex, detailed, complicated |
| nuanced | subtle, complex, detailed |
| multifaceted | complex, varied, diverse |
| holistic | complete, whole, comprehensive |

### Overused Metaphorical Nouns (2025-2026)
AI models use these nouns metaphorically to inject false gravitas. Literal uses are fine.

| Avoid (metaphorical) | Acceptable (literal) |
|-------|-------------|
| tapestry ("a tapestry of regulations") | tapestry (actual woven fabric) |
| symphony ("a symphony of features") | symphony (actual musical composition) |
| beacon ("a beacon of hope") | beacon (actual light or signal device) |
| realm ("in the realm of cybersecurity") | realm (actual kingdom or territory) |
| testament ("a testament to innovation") | testament (actual legal document, e.g., last will and testament) |

---

## Overused Transitions and Connectors

| Avoid | Use Instead |
|-------|-------------|
| furthermore | also, in addition, and |
| moreover | also, and, besides |
| notwithstanding | despite, even so, still |
| that being said | however, but, still |
| at its core | essentially, fundamentally, basically |
| to put it simply | in short, simply put |
| it is worth noting that | note that, importantly |
| in the realm of | in, within, regarding |
| in the landscape of | in, within |
| in today's [anything] | currently, now, today |

---

## Phrases That Signal AI Writing

### Opening Phrases to Avoid
- "In today's fast-paced world..."
- "In today's digital age..."
- "In an era of..."
- "In the ever-evolving landscape of..."
- "In the realm of..."
- "It's important to note that..."
- "Let's delve into..."
- "Imagine a world where..."

### Transitional Phrases to Avoid
- "That being said..."
- "With that in mind..."
- "It's worth mentioning that..."
- "At its core..."
- "To put it simply..."
- "In essence..."
- "This begs the question..."

### Concluding Phrases to Avoid
- "In conclusion..."
- "To sum up..."
- "By [doing X], you can [achieve Y]..."
- "In the final analysis..."
- "All things considered..."
- "At the end of the day..."

### Structural Patterns to Avoid
- "Whether you're a [X], [Y], or [Z]..." (listing three examples after "whether")
- "It's not just [X], it's also [Y]..."
- "Think of [X] as [elaborate metaphor]..."
- Starting sentences with "By" followed by a gerund: "By understanding X, you can Y..."
- Contrasting parallelisms: "It's not X. It's Y." or "It's not about X, it's about Y." More than two of these in a 500-word block is a high-confidence AI indicator.

### Inflated Symbolism Phrases (2025-2026 AI Tells)
These multi-word phrases appear hundreds of times more frequently in AI-generated text than in human baselines (corpus analysis, isgpt.org 2025):
- "provide a valuable insight" (468x more frequent in AI text)
- "left an indelible mark" (317x)
- "play a significant role in shaping" (207x)
- "an unwavering commitment" (202x)
- "open a new avenue" (174x)
- "a stark reminder" (166x)
- "gain a comprehensive understanding" (120x)
- "serves as a testament"
- "watershed moment"
- "deeply rooted"

---

## Heading Anti-Patterns

AI-generated content frequently uses narrative, dramatic, or clickbait heading structures. All headings must describe the section content directly and technically.

### Banned Heading Structures

| Pattern | Bad Example | Good Replacement |
|---------|-------------|------------------|
| "The [Concept] Trap" | "The Initialization Trap" | "Import vs. Initialize: DDF Metadata Destruction Risk" |
| "The [Adjective] [Noun]" drama | "The Hidden Danger" | "Firmware Corruption After Sudden Power Loss" |
| "The [Noun] [Dramatic Noun]" | "The Silent Killer" | "Gradual Bad Sector Growth on Aging Platters" |
| "Why [Action] [Dramatic Verb] [Object]" | "Why Rebuilding Destroys Everything" | "How Forced Rebuilds Overwrite Parity on Degraded Arrays" |
| "[Noun]: The [Adjective] [Noun]" | "Encryption: The Hidden Trap" | "Hardware AES-256 Encryption on WD Passport Bridge Boards" |
| "The [Noun] You [Emotion Verb]" | "The Risk You Overlook" | "Unmonitored SMART Threshold Warnings" |

### How to Self-Check Headings

1. Could this heading serve as a thriller chapter title or YouTube clickbait thumbnail? If yes, rewrite it.
2. Does the heading describe what the section contains, or does it tease it? Headings describe; they do not tease.
3. Remove "The" from the beginning of any heading and check if it still uses a dramatic noun pairing. If so, rewrite.
4. A good heading reads like an entry in a technical manual index: specific, descriptive, and boring to non-specialists.

---

## Filler Words and Empty Intensifiers

These words often add nothing to meaning. Remove them or find specific alternatives:

- absolutely
- actually
- basically
- certainly
- clearly
- definitely
- essentially
- extremely
- fundamentally
- incredibly
- interestingly
- naturally
- obviously
- quite
- really
- significantly
- simply
- surely
- truly
- ultimately
- undoubtedly
- very

---

## Academic-Specific AI Tells

| Avoid | Use Instead |
|-------|-------------|
| shed light on | clarify, explain, reveal |
| pave the way for | enable, allow, make possible |
| a myriad of | many, numerous, various |
| a plethora of | many, numerous, several |
| paramount | very important, essential, critical |
| pertaining to | about, regarding, concerning |
| prior to | before |
| subsequent to | after |
| in light of | because of, given, considering |
| with respect to | about, regarding, for |
| in terms of | regarding, for, about |
| the fact that | that (or rewrite sentence) |

---

## Hallucinated Markup Artifacts

When AI generates wikitext, it sometimes hallucinates citation markup from its training data. These are 100% confidence indicators of unedited AI output:

| Artifact | Origin |
|----------|--------|
| `oaicite` | OpenAI ChatGPT citation placeholder |
| `contentReference` | OpenAI internal reference tag |
| `grok_card` | xAI Grok citation tag |
| `attributableIndex` | AI attribution tracking artifact |
| `turn0search0` | ChatGPT search result placeholder |

Any occurrence of these strings means the text was pasted from an AI tool without editing. Zero tolerance.

---

## Hedging and Epistemic Modality Overload

AI models hedge 4-7x more than human writers (ACL 2024 study, 12,000 technical documents).

### Hedging Markers
- **Epistemic modals** (45% of AI hedges): may, might, could, potentially
- **Cognitive verbs** (25%): I think, I believe, it seems, it appears
- **Adverbs of limitation** (20%): probably, generally, usually, arguably, likely
- **Explicit uncertainty markers**: unclear, remains to be seen, further research is needed

### Thresholds
- **Per-paragraph:** More than 3 hedging instances in a single paragraph warrants scrutiny
- **Per-1000-words:** More than 8 hedging markers per 1,000 words in declarative sections (Background, History, Timeline) indicates AI generation
- **Appropriate hedging:** Sections discussing pending legislation, ongoing litigation, or genuinely disputed facts should hedge. Do not flag hedging in those contexts.

### AI Hedging Phrases to Flag
- "It is worth noting that..."
- "It should be noted that..."
- "One could argue that..."
- "While X, Y remains..."
- "Though precise thresholds can vary depending on..."
- "It is widely acknowledged that..."

### Human vs. AI Hedging
Humans hedge contextually, grounding uncertainty in specific evidence: "The FTC's 2024 enforcement data suggests a 12% increase." AI hedges with blanket qualifiers on established facts: "It is widely acknowledged that repair restrictions may potentially impact consumers."

---

## Structural and Statistical Patterns

Beyond lexical tells, AI text exhibits measurable structural uniformity that human writing does not.

### Paragraph Length Uniformity
AI aims for visual symmetry. Paragraphs tend toward identical sentence counts (typically 3-4 sentences each). Human writing varies paragraph length based on sub-topic complexity.
- **Threshold:** If all paragraphs in a section are within 15% of each other in word count, the section is likely AI-generated.
- **Exception:** Bulleted lists, tables, and template fields are structurally uniform by design.

### Sentence Length Uniformity (Burstiness)
Human writing alternates between short, punchy sentences and long, clause-heavy ones. AI sentences cluster uniformly around 15-20 words.
- **Threshold:** If a 500-word block contains no sentences under 8 words or over 30 words, it lacks human burstiness.
- **Human baseline:** Human text exhibits 3+ distinct syntactic patterns per 100 words. AI text shows 1.5 or fewer.

### Transition Density
- **Threshold:** If more than 30% of paragraphs in an article begin with a transition word or adverbial clause, the text is structurally artificial.

### Opening-Word Repetition
Three or more consecutive paragraphs starting with the same word or phrase pattern indicates mechanical generation. Vary opening words.

### Segmental Entropy
AI maintains flat stylistic consistency from introduction through conclusion. Human writers naturally vary pacing, complexity, and sentence structure between sections.
- **Threshold:** Calculate sentence length variance separately for the introduction, body, and conclusion. If variance differs by less than 10% across all three segments, the text was likely generated as a single pass by AI.

### Contrasting Parallelism Overuse
2025-era models overuse sequential contrasting structures to simulate punchy emphasis:
- "It's not X, it's Y."
- "It's not about X, it's about Y."
- "The issue isn't X. The issue is Y."
- **Threshold:** More than two contrasting parallelisms in a 500-word block.

---

## Model-Family-Specific Tells

### GPT-4o / GPT-4.5 (OpenAI)
- Heavy use of bullet-point formatting and structured lists
- Staccato short-sentence contrasting: "It's not X. It's Y." used to simulate punchy copy
- Rhetorical colon abuse: "Here's the thing:", "Think about it:", "The bottom line:", "The reality:"
- Over-structures arguments into numbered steps

### Claude 3.5 / Claude 4 (Anthropic)
- Better sentence length variation than GPT, but still exhibits flat segmental entropy
- Overly polite and conciliatory transitions: "It's worth considering that", "To be fair", "That said"
- Leans toward poetic and metaphorical prose with words like "nuanced," "complexities"
- Loses thread in long documents and resorts to increasingly generic transitions
- Tends toward diplomatic hedging even when stating documented facts

### Common Across All Models
- Uniform paragraph lengths
- Predictable section ordering (Background > Details > Impact > Response)
- Citation clustering at paragraph ends rather than distributed throughout sentences
- Excessive boldface on concepts, product names, and inline headers

---

## False Positive Prevention

### Exclusion Zones
Lexical scans must NOT flag text inside:
- Direct quotes (`"..."`) from cited sources
- Titles, names, and other verbatim values taken from a source
- Code, configuration, or markup that is being shown as an example

### Context-Aware Severity
If a banned word appears immediately adjacent to specific named entities (proper nouns, statute numbers, dates, dollar amounts), it is more likely being used with technical meaning than as AI filler. Reduce flag severity.
- **Higher severity:** "a comprehensive examination of the issues" (abstract nouns, no specifics)
- **Lower severity:** "comprehensive audit by the FTC in 2024" (specific entity, specific date)

### Metaphorical vs. Literal Distinction
These words require bigram context checking. Only flag metaphorical uses:
- ecosystem: "Apple's software ecosystem" (OK) vs. "the repair ecosystem" (flag)
- landscape: "Arizona landscape" (OK) vs. "the regulatory landscape" (flag)
- navigate: "navigate the website" (OK) vs. "navigate the regulatory process" (flag)
- tapestry: "medieval tapestry" (OK) vs. "a tapestry of regulations" (flag)
- symphony: "Beethoven's symphony" (OK) vs. "a symphony of features" (flag)
- beacon: "lighthouse beacon" (OK) vs. "a beacon of hope" (flag)
- testament: "last will and testament" (OK) vs. "a testament to innovation" (flag)

---

## How to Self-Check

1. Read your text aloud. If phrases sound unnatural in speech, revise them.
2. Ask: "Would I say this in a conversation with a colleague?"
3. Check for repetitive sentence structures.
4. Look for clusters of the words listed above.
5. Ensure varied sentence lengths (not all similar length).
6. Verify each intensifier adds genuine meaning.
7. Count hedging markers per paragraph. More than 3 in a single paragraph is a red flag.
8. Check paragraph word counts within each section. If they are all similar, vary them.
9. Search for hallucinated markup: `oaicite`, `contentReference`, `turn0search0`, `grok_card`.
10. Check if your introduction, body, and conclusion have different pacing and sentence complexity.
