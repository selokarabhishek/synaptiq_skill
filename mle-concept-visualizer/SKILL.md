---
name: mle-concept-visualizer
description: "Interactive visualizer for MAANG MLE interview concepts like self-attention, multi-head attention, FlashAttention, and KV cache. Use when the user wants a visual explanation instead of plain text."
metadata:
  homepage: https://github.com/selokarabhishek/synaptiq_skill/tree/main/mle-concept-visualizer
---

# MLE Concept Visualizer

## Instructions

When the user asks for a visual explanation of an MLE interview concept, system design concept, optimization, architecture idea, or model behavior, call the `run_js` tool.

Use the following exact parameters:

- script name: index.html
- data: A JSON string with these fields:
  - concept: String. Required. The concept to visualize. It can be a specific known concept like `self-attention`, `multi-head-attention`, `flash-attention`, or `kv-cache`, or a broader topic such as `rag`, `recommendation systems`, or `feature stores`.
  - focus: String. Optional. Short phrase describing what the user wants emphasized, such as `memory`, `latency`, `tradeoffs`, `intuition`, or `interview framing`.

Concept selection rules:
- Map `attention`, `attention visualization`, or `attention visualisation` to `self-attention` unless the user clearly means a different variant.
- Map `mha` to `multi-head-attention`.
- Map `flash attention` or `flashattention` to `flash-attention`.
- Map `key value cache`, `key-value cache`, or `kv cache` to `kv-cache`.
- Map `qkv cache` or `qkv-cache` to `kv-cache`.

Response rules:
- Use the visualizer first when the user explicitly asks for a visual explanation.
- If the concept is unfamiliar, still call the visualizer and let it render the generic interview breakdown instead of skipping the tool.
- After the tool returns, summarize the concept in 3 to 6 concise bullets.
- Emphasize interview language: bottleneck, tradeoff, scale, memory, latency, and what changes between naive and optimized versions.
