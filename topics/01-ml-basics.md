# ML Basics for Agentic Development

## Tokens

### What Are Tokens

Tokens are the fundamental unit of text that language models actually process. Rather than reading words or characters, models break text into subword chunks -- common words become single tokens, while rare or long words get split into multiple pieces. The word "unhappiness" might become three tokens (`un`, `happiness`, and a boundary marker), while "the" is always one. This subword tokenization is how models handle any text without needing an impossibly large vocabulary.

### Token Counting

The practical heuristic: **1 token is roughly 4 characters of English text**, or about 0.75 words. A 1,000-word document is approximately 1,300 tokens. This matters because you are always budgeting. Every prompt you send, every file Claude reads, every tool response that comes back -- all of it is measured in tokens, and all of it counts against a finite limit.

## Transformers

### High-Level Architecture

The transformer is the architecture behind every modern large language model, including Claude. At a high level, the original design has two parts: an encoder that reads and comprehends input, and a decoder that generates output one token at a time. Modern LLMs like Claude use a decoder-only variant -- they process the entire conversation so far and predict what comes next, repeatedly, until the response is complete.

The key innovation is **self-attention**: the mechanism that lets the model decide which parts of its input are most relevant to each other. When the model encounters the word "it" in a sentence, self-attention figures out whether "it" refers to "the server" or "the error" by examining relationships between all tokens in the context. This is what gives the model its apparent understanding -- it is not following rules, it is computing relevance across everything it can see.

### Why This Matters

This matters for agentic development because self-attention is what makes Claude useful as a coding agent. It can hold your CLAUDE.md instructions, the file it just read, the tool result it got back, and your latest message -- all at once -- and compute which pieces are relevant to the current decision. But attention is not free. The more tokens in the context, the more relationships the model must evaluate. As context grows, the model's ability to attend sharply to any single detail degrades. This is a fundamental tension you will manage every time you work with Claude Code.

## Context Windows

### What Is a Context Window

The context window is the total number of tokens a model can process in a single conversation -- input and output combined. Think of it as working memory: everything the model knows about your current session must fit inside this window. Once it is full, the oldest content must be dropped or summarized to make room. Unlike human memory, there is no background recall -- if it is not in the window, it does not exist for the model.

### Context Window as a Resource

When you build with Claude Code, context is a resource you spend. Every file read, every tool call, every response -- it all accumulates. The "augmented LLM" pattern described by Anthropic -- an LLM enhanced with retrieval, tools, and memory -- is powerful precisely because those augmentations feed information into the context window. But agentic loops compound the cost: each cycle of "think, act, observe" adds the previous tool results and reasoning to the running total. An agent that calls ten tools in a loop has consumed far more context than a single-turn question.

Current context windows across the Claude model family:

| Model | Context Window | Max Output | Input Price | Output Price | Knowledge Cutoff |
|:------|:--------------|:-----------|:------------|:-------------|:-----------------|
| Claude Opus 4.6 | 1,000,000 tokens | 128,000 tokens | $5 / MTok | $25 / MTok | May 2025 |
| Claude Sonnet 4.6 | 1,000,000 tokens | 64,000 tokens | $3 / MTok | $15 / MTok | Aug 2025 |
| Claude Haiku 4.5 | 200,000 tokens | 64,000 tokens | $1 / MTok | $5 / MTok | Feb 2025 |

The difference is significant: 1M tokens is roughly 750,000 words -- enough to hold an entire medium-sized codebase in a single conversation. Haiku's 200k window is still substantial but fills up faster in agent workflows.

### Opus 4.6 and the 1M Token Window

Claude Opus 4.6 and Sonnet 4.6 both support a 1M token context window natively. Previous-generation models like Opus 4.5, Opus 4.1, and Opus 4 were limited to 200k tokens. This 5x increase changes what is practical: where a 200k window might hold a handful of source files and a short conversation history, a 1M window can accommodate an entire repository's worth of code, extended multi-step agent sessions, and long reference documents -- all simultaneously. For Claude Code specifically, this means longer agentic sessions before context pressure forces a reset, and the ability to work across more files without losing track of earlier reads.

## Context Rot

### What Is Context Rot

Context rot is the observable degradation in model output quality as the context window fills up. It happens because self-attention must distribute its focus across all tokens in the window. With a small context, attention is concentrated and sharp. With a large, crowded context, the model's ability to find and prioritize the most relevant information weakens. The instructions you gave at the start of the session get diluted by thousands of tokens of intermediate tool results, file contents, and prior responses.

### Practical Implications

You will recognize context rot when it happens: the model starts producing vague or generic outputs, forgets instructions you gave earlier, repeats itself, or loses track of which files it has already read. It may confidently reference details that are subtly wrong -- it is not hallucinating from nothing, it is blending information that has become noisy in a crowded context.

Mitigation strategies:

- **Compaction**: Claude Code can automatically summarize and compress the conversation history to reclaim context space. The `CLAUDE_AUTOCOMPACT_PCT_OVERRIDE` environment variable controls when this triggers -- for example, setting it to `"40"` triggers compaction when the context reaches 40% capacity, more aggressively than the default. This is a real configuration option you set in your `settings.json`.
- **Scoping**: Be deliberate about what enters the context. Read only the files you need. Use targeted grep searches instead of reading entire directories. Keep CLAUDE.md instructions concise.
- **Fresh sessions**: Sometimes the best fix is starting over. A new session gives you a clean context window with full attention budget. For long-running tasks, break work into focused sessions rather than one marathon conversation.

## Connecting Forward

Everything in this topic has a direct operational consequence in Claude Code. Your CLAUDE.md files, your tool configurations, your conversation history, the files Claude reads, the results of every bash command and grep search -- all of it is tokens, and all of it lives in the context window. In Topic 03, we will look at how Claude Code actually works: how it structures conversations, when it reads files, how tool calls accumulate, and what levers you have to manage context consumption in practice. The mental model from this topic -- tokens as a budget, attention as a finite resource, context rot as the failure mode -- is the foundation for everything that follows.

---

## References

- [Anthropic Models Documentation](https://platform.claude.com/docs/en/about-claude/models/overview) -- Model specifications, context windows, and pricing.
- [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/) -- Visual explanation of transformer architecture and self-attention.
- [Building Effective Agents (Anthropic)](https://www.anthropic.com/research/building-effective-agents) -- Agentic design patterns, the augmented LLM concept, and practical agent architecture.
- [Claude 4 Announcement](https://www.anthropic.com/news/claude-4) -- Capabilities overview for the Claude 4 model family.
