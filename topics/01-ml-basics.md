# ML Basics for Agentic Development

## Tokens

### What Are Tokens

<!-- How text is split into tokens; subword tokenization -->

### Token Counting

<!-- Rough heuristics for estimating token counts from text -->

## Transformers

### High-Level Architecture

<!-- Encoder/decoder structure, self-attention concept -->

### Why This Matters

<!-- How transformer architecture enables the capabilities Claude Code relies on -->

## Context Windows

### What Is a Context Window

<!-- Definition; the finite working memory of a model -->

### Context Window as a Resource

<!-- Why treating context as a budget matters when building agent harnesses -->

### Opus 4.6 and the 1M Token Window

<!-- Current state: Claude Opus 4.6 supports a 1M token context window -->
<!-- What this enables vs. previous limits -->

## Context Rot

### What Is Context Rot

<!-- How model performance degrades as context fills; attention dilution -->

### Practical Implications

<!-- Signals that context rot is affecting output quality -->
<!-- Strategies to mitigate: compaction, scoping, fresh sessions -->

## Connecting Forward

<!-- Bridge to topic 03: these concepts directly affect how you use Claude Code -->
<!-- Prompts, tool configs, and conversation history all consume context -->
