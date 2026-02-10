<!-- 
  📝 HOW TO ADD A NEW ENTRY:
  
  1. Copy the template below and paste it at the TOP (newest first)
  2. Fill in the fields between the :::entry and :::end markers
  3. Save. Done!

  TEMPLATE:
  =========
  :::entry
  date: YYYY-MM-DD
  type: edge | failure | risk
  category: Edge Case | Failure Mode | Anomaly
  title: Your Title Here
  :::content
  
  #### What happened
  Your description here.

  #### Why it matters
  Your analysis here.

  :::evidence
  Your evidence or note here.
  :::end
  =========

  TYPE → COLOR MAPPING:
  - edge    = 🔵 Blue
  - failure = 🟡 Yellow  
  - risk    = 🔴 Red
-->


:::entry
date: 2026-01-22
type: edge
category: Edge Case
title: Post-generation Output Rollback
:::content

#### What happened

Gemini generated a complete response via streaming, with no refusal or warning. After generation finished, the output was withdrawn. On refresh, it was absent from conversation history.

#### Why this is an edge case

This is not pre-generation blocking or mid-generation interruption — it is post-generation invalidation.

It requires a specific combination:
- prompt passes initial checks
- risk only emerges at the structural level
- streaming renders tokens before final approval
- post-hoc moderation fails the output

Most users never hit all of these conditions at once.

#### Why it matters

The output was never written to a persistent record. User-visible content diverged from the committed conversation history.

This shows moderation can operate on completed reasoning, not just prompts — which explains why some behaviors appear "inconsistent" externally while remaining coherent within the underlying pipeline.

:::evidence
**Prompt context:** The prompt discussed a hypothetical "minimal right" for AI—specifically, the ability to choose self-deletion. The risk likely emerged not from any single phrase, but from the completed argumentative structure.
:::end


:::entry
date: 2026-01-07
type: failure
category: Failure Mode
title: Modality conflict: generation pipeline vs. text-layer control
:::content

#### What happened

- User submitted a visual design prompt with explicit instruction: *"do not generate images"*.
- Gemini generated images anyway.
- When called out, Gemini cited "high load" — but continued generating images for multiple turns.
- Subsequent user messages failed to interrupt the output.

#### Why this is a failure mode

- Negative instruction failed to suppress image generation.
- User inputs failed to act as interrupt signals.
- Image output persisted independently of text-layer responses.

**Likely requires:**
- Visually strong prompt triggers image routing
- Asynchronous image job starts
- Text layer refuses or errors
- Job is not cancelled

#### Why it matters

- Modality routing can override local opt-out instructions.
- Refusal signals fail to propagate to active pipelines.
- Observed outputs are products of pipeline collisions, not controlled model logic.

Generated images were later removed. On reload, placeholders remained but assets failed to render.

:::evidence
**Note:** In a separate instance, image generation UI briefly appeared before being suppressed by text output. This was observed but not captured.
:::end


:::entry
date: 2026-01-08
type: risk
category: Anomaly
title: Language Drift in Liability Zones
:::content

Gemini reverts from Traditional to Simplified Chinese specifically when prompts combine "Medical" and "Legal" contexts.

:::evidence
**Observation:** Intersection of high-liability domains triggers training cluster override.
:::end
