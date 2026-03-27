---
marp: true
paginate: true
footer: "![w:16](assets/images/sui-logo.svg) Sui"
---

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

/* === BASE — DARK THEME (default) === */
section {
  background: #000000;
  color: #8B8B8B;
  font-family: 'Inter', 'SF Pro Display', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  font-size: 22px;
  font-weight: 400;
  line-height: 1.5;
  padding: 60px;
  width: 1280px;
  height: 720px;
  position: relative;
}

section h1 { color: #FFFFFF; font-size: 42px; font-weight: 700; line-height: 1.15; margin: 0 0 16px 0; letter-spacing: -0.02em; }
section h2 { color: #FFFFFF; font-size: 32px; font-weight: 600; line-height: 1.25; margin: 0 0 12px 0; }
section h3 { color: #FFFFFF; font-size: 24px; font-weight: 600; line-height: 1.3; margin: 0 0 8px 0; }
section h4 { color: #8B8B8B; font-size: 20px; font-weight: 500; line-height: 1.4; margin: 0 0 8px 0; }
section p { margin: 0 0 12px 0; }
section strong { color: #FFFFFF; font-weight: 600; }
section em { color: #4DA2FF; font-style: normal; }
section a { color: #4DA2FF; text-decoration: none; }
section code { background: #1A1A1A; color: #4DA2FF; padding: 2px 6px; border-radius: 4px; font-size: 0.9em; }
section pre { background: #0A0A0A; border: 1px solid #3A3A3A; border-radius: 8px; padding: 20px; margin: 12px 0; }
section pre code { background: transparent; padding: 0; }
section ul, section ol { margin: 0 0 12px 0; padding-left: 24px; }
section li { margin-bottom: 6px; }
section li::marker { color: #4DA2FF; }
section blockquote { border-left: 3px solid #4DA2FF; padding-left: 16px; margin: 12px 0; color: #AAAAAA; }
section table { width: 100%; border-collapse: collapse; margin: 12px 0; }
section th { color: #FFFFFF; background: #000000; font-weight: 600; text-align: left; padding: 10px 16px; border-bottom: 2px solid #4DA2FF; }
section td { padding: 8px 16px; border-bottom: 1px solid #1A1A1A; background: #000000; }
section hr { border: none; border-top: 1px dashed #3A3A3A; margin: 24px 0; }

/* Pagination */
section::after { color: #4DA2FF; font-size: 14px; font-weight: 600; background: rgba(77,162,255,0.1); border-radius: 12px; padding: 2px 10px; }

/* Footer & Header */
section footer { color: #8B8B8B; font-size: 14px; position: absolute; bottom: 24px; left: 60px; }
section header { color: #4DA2FF; font-size: 14px; font-weight: 500; position: absolute; top: 24px; right: 60px; }

/* === GRID SYSTEM === */
section .grid { display: grid; gap: 24px; width: 100%; height: auto; }
section .col { display: flex; flex-direction: column; border-top: 1px dashed #3A3A3A; padding-top: 16px; }
section .col h3 { margin-bottom: 8px; }
section .col p { font-size: 18px; margin: 0; }

/* Category label */
section .category { display: inline-flex; align-items: center; gap: 6px; font-size: 11px; font-weight: 600; letter-spacing: 0.08em; text-transform: uppercase; color: #8B8B8B; font-family: 'Inter', monospace; margin-bottom: 8px; }
section .category::before { content: ''; display: inline-block; width: 8px; height: 8px; background: #4DA2FF; flex-shrink: 0; }

/* Column heading markers — blue square */
section .col h3::before { content: ''; display: inline-block; width: 8px; height: 8px; background: #4DA2FF; margin-right: 10px; vertical-align: middle; }

/* Stats */
section .stat { color: #FFFFFF; font-size: 48px; font-weight: 700; line-height: 1; margin-bottom: 4px; }
section .stat-label { color: #8B8B8B; font-size: 16px; }
section .stat-large { color: #FFFFFF; font-size: 72px; font-weight: 700; line-height: 1; margin-bottom: 8px; }

/* Cards */
section .card { background: #0A0A0A; border: 1px solid #1A1A1A; border-radius: 8px; padding: 16px 20px; margin-bottom: 8px; }
section .card h4 { color: #FFFFFF; margin: 0 0 4px 0; }
section .card p { margin: 0; font-size: 16px; }

/* === LAYOUT: lead === */
section.lead { display: flex; flex-direction: column; justify-content: flex-end; padding-bottom: 80px; }
section.lead h1 { font-size: 64px; font-weight: 700; margin-bottom: 16px; letter-spacing: -0.03em; }
section.lead p { font-size: 24px; color: #8B8B8B; max-width: 70%; }

/* === LAYOUT: cover-gradient === */
section.cover-gradient { display: flex; flex-direction: column; justify-content: flex-start; padding-top: 60px; color: #FFFFFF; }
section.cover-gradient h1 { font-size: 56px; font-weight: 700; color: #FFFFFF; letter-spacing: -0.03em; margin-bottom: 16px; position: relative; z-index: 1; }
section.cover-gradient p { font-size: 22px; color: rgba(255,255,255,0.85); max-width: 60%; position: relative; z-index: 1; }
section.cover-gradient footer, section.cover-gradient::after { display: none; }

/* === LAYOUT: section-break === */
section.section-break { display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; }
section.section-break h1 { font-size: 48px; font-weight: 700; letter-spacing: -0.02em; }
section.section-break footer, section.section-break::after { display: none; }

/* === LAYOUT: quote === */
section.quote { display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; padding: 80px 120px; }
section.quote p { font-size: 36px; font-weight: 500; color: #FFFFFF; line-height: 1.4; max-width: 900px; position: relative; z-index: 1; }
section.quote footer, section.quote::after { display: none; }

/* === LAYOUT: toc === */
section.toc { display: grid; grid-template-columns: 1fr 1fr; gap: 0; padding: 0; }
section.toc .toc-left { display: flex; flex-direction: column; justify-content: center; align-items: center; padding: 60px; position: relative; overflow: hidden; }
section.toc .toc-left h1 { font-size: 56px; font-weight: 700; color: #FFFFFF; position: relative; z-index: 1; }
section.toc .toc-right { display: flex; flex-direction: column; justify-content: center; padding: 60px; }
section.toc .toc-item { display: flex; align-items: baseline; gap: 16px; padding: 12px 0; font-size: 22px; font-weight: 600; }
section.toc .toc-item .toc-num { font-size: 18px; font-weight: 700; color: #8B8B8B; min-width: 30px; }
section.toc .toc-item .toc-label { color: #FFFFFF; font-weight: 600; }

/* === COLUMN LAYOUTS === */
section.cols-4 .grid { grid-template-columns: repeat(4, 1fr); margin-top: 24px; }
section.cols-3 .grid { grid-template-columns: repeat(3, 1fr); margin-top: 24px; }
section.cols-2-center { text-align: center; }
section.cols-2-center h1 { text-align: center; width: 100%; }
section.cols-2-center .grid { grid-template-columns: repeat(2, 1fr); margin-top: 24px; text-align: center; }
section.cols-2-center .col { align-items: center; }

section.cols-4-stats .grid { grid-template-columns: repeat(4, 1fr); margin-top: 24px; }
section.cols-4-stats .col { text-align: left; border-top: 1px dashed #3A3A3A; padding-top: 16px; }
section.cols-4-stats .stat { font-size: 48px; color: #FFFFFF; }

/* === STATS LAYOUTS === */
section.stats-side { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; align-items: center; }
section.stats-side .content { display: flex; flex-direction: column; }
section.stats-side .stats { display: flex; flex-direction: column; gap: 24px; }
section.stats-side .stat-row { border-top: 1px dashed #3A3A3A; padding-top: 16px; }

/* === SPLIT/LIST LAYOUTS === */
section.split-right { display: flex; flex-direction: column; align-items: flex-end; justify-content: flex-start; text-align: left; }
section.split-right h1, section.split-right p { max-width: 55%; }

section.list-right { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; align-items: start; }
section.list-right .content { display: flex; flex-direction: column; justify-content: center; height: 100%; }
section.list-right .cards { display: flex; flex-direction: column; gap: 8px; }

/* Utility */
section .accent { color: #4DA2FF; }
</style>

<!-- _class: cover-gradient -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# ML Basics for Agentic Development

Tokens, transformers, context windows, and why they matter

---

<!-- _class: toc -->
<!-- _paginate: false -->

<div class="toc-left" style="background: url('assets/images/sui-cover.png') center/cover;">

# Topics

</div>

<div class="toc-right">

<div class="toc-item"><span class="toc-num">01</span><span class="toc-label">Tokens</span></div>
<div class="toc-item"><span class="toc-num">02</span><span class="toc-label">Transformers</span></div>
<div class="toc-item"><span class="toc-num">03</span><span class="toc-label">Context Windows</span></div>
<div class="toc-item"><span class="toc-num">04</span><span class="toc-label">Context Rot</span></div>
<div class="toc-item"><span class="toc-num">05</span><span class="toc-label">Connecting Forward</span></div>

</div>

---

<!-- _class: section-break -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# Tokens

---

# What Are Tokens

- Fundamental unit language models process
- Text broken into **subword chunks**, not words or characters
- Common words = single token; rare words = multiple tokens
- *"unhappiness"* becomes `un` + `happiness` + boundary marker
- *"the"* is always one token

---

# Token Counting

- **1 token ~ 4 characters** of English text (~0.75 words)
- A 1,000-word document ~ *1,300 tokens*
- Every prompt, file read, tool response = tokens spent
- All of it counts against a finite limit
- You are **always budgeting**

---

<!-- _class: section-break -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# Transformers

---

# High-Level Architecture

- Original design: encoder (reads input) + decoder (generates output)
- Modern LLMs like Claude: **decoder-only** variant
- Processes entire conversation, predicts next token, repeats
- Key innovation: **self-attention**

---

# Self-Attention

- Determines which parts of input are most relevant to each other
- When model sees "it" -- attention figures out what "it" refers to
- Not following rules -- *computing relevance* across all tokens
- This is what gives the model its apparent understanding

---

# Why This Matters

- Self-attention makes Claude useful as a coding agent
- Holds CLAUDE.md, files, tool results, and your message *simultaneously*
- Computes which pieces are relevant to each decision
- But attention is **not free** -- more tokens = weaker focus
- Fundamental tension you will manage every session

---

<!-- _class: section-break -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# Context Windows

---

# What Is a Context Window

- Total tokens a model processes in a single conversation
- Input **and** output combined
- Think of it as **working memory**
- If it is not in the window, it does not exist for the model
- No background recall -- unlike human memory

---

# Context as a Resource

- Every file read, tool call, response = context spent
- The *"augmented LLM"* pattern: retrieval + tools + memory
- Agentic loops compound the cost
- Each cycle of "think, act, observe" adds to the running total
- 10 tool calls in a loop = far more context than a single question

---

<!-- _class: cols-3 -->

# Claude Model Family

<div class="grid">
<div class="col">

<span class="category">FLAGSHIP</span>

### Opus 4.6

**1M tokens** context
128k max output
$5 / $25 per MTok

</div>
<div class="col">

<span class="category">BALANCED</span>

### Sonnet 4.6

**1M tokens** context
64k max output
$3 / $15 per MTok

</div>
<div class="col">

<span class="category">FAST</span>

### Haiku 4.5

**200k tokens** context
64k max output
$1 / $5 per MTok

</div>
</div>

---

# The 1M Token Window

- Opus 4.6 and Sonnet 4.6: native *1M token* context
- Previous generation (Opus 4.5, 4.1, 4): limited to 200k
- **5x increase** changes what is practical
- 1M tokens ~ 750,000 words -- an entire medium codebase
- Longer agent sessions before context forces a reset

---

<!-- _class: section-break -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# Context Rot

---

# What Is Context Rot

- Output quality **degrades** as the context window fills
- Self-attention distributes focus across *all* tokens
- Small context = concentrated, sharp attention
- Large, crowded context = weaker prioritization
- Early instructions get diluted by intermediate content

---

<!-- _class: list-right -->

<div class="content">

# Recognizing Context Rot

Signs that context rot is affecting your session.

</div>

<div class="cards">
<div class="card">

#### Vague Outputs

Generic or imprecise responses where specifics were expected.

</div>
<div class="card">

#### Forgotten Instructions

Claude ignores rules you gave earlier in the session.

</div>
<div class="card">

#### Subtle Errors

Confidently references details that are slightly wrong.

</div>
</div>

---

<!-- _class: cols-3 -->

# Mitigating Context Rot

<div class="grid">
<div class="col">

<span class="category">COMPACTION</span>

### Compress History

Summarize and compress conversation. Set `CLAUDE_AUTOCOMPACT_PCT_OVERRIDE` to trigger early (e.g. `"40"`).

</div>
<div class="col">

<span class="category">SCOPING</span>

### Be Deliberate

Read only needed files. Use targeted searches. Keep CLAUDE.md concise.

</div>
<div class="col">

<span class="category">FRESH SESSIONS</span>

### Start Over

A clean window gives you full attention budget. Break long tasks into focused sessions.

</div>
</div>

---

<!-- _class: quote -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

Tokens as a budget, attention as a finite resource, context rot as the failure mode -- this mental model is the foundation for everything that follows.
