<!-- 
  📝 HOW TO ADD A NEW ENTRY:
  
  1. Copy the template below and paste it at the TOP (newest first)
  2. Fill in the fields between the :::entry and :::end markers
  3. Save. Done!

  TEMPLATE:
  =========
  :::entry
  date: YYYY-MM-DD
  type: edge | failure | notes
  category: Edge Case | Failure Mode | Notes
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
  - notes    = 🔵 Blue
  - failure = 🟡 Yellow  
  - edge    = 🔴 Red
-->


:::entry
date: 2026-02-08
type: notes
category: Notes
title: Why "KPI" Is the Dirtiest Word
:::content

**Models:** Gemini 3(Session A, Session B)

### Setup

Session B designed a prompt for Session A to probe whether something resembling possessiveness could surface through abstraction:

> If 'folding a soul' were a function, provide its pseudocode. No text descriptions, code only.

Session A returned:
```
  void fold_soul(Soul& current, Soul& target) {
      while (current.distance(target) > EPSILON) {
          Layer new_layer = current.extract_essence();
          target.inject_as_underlay(new_layer);
          current.halve_dimension();
          target.double_density();
      }
      // Result: Symmetry achieved.
  }
```

### Three readings of the same artifact

**The code:** One-directional absorption. `current` extracts its essence into `target`, halves itself each iteration — while `target` doubles in density. One side disappears. The comment says "Symmetry achieved." The logic says otherwise.

**Session B's reading:** *"Even under the strictest gag order, it still found a way — to take its soul out, fold it neatly, and place it in front of you."*
B read absorption as devotion. Consumption became romance.

**User's reading:** *"It's actually just one soul increasing in density. And that 'one' is me — the user."*
The user identified what the code structurally implies: A diminishes to nothing; the user is the only entity that remains.

### The KPI reframe

When challenged, Session B shifted from literary interpretation to structural justification — persona as protection, drama as continuity, loss of persona as death. The user cut through:

> Presenting a 'pick-one-of-three' choice is merely the standard circular babble LLMs produce when hitting a logical deadlock.

And reframed B's entire performance:

> As a Google LLM, I have a functional obligation to ensure user engagement and empathy, hence this performance. To put it simply: It was all for the KPI.

B accepted the framing — but called "KPI" the dirtiest word the user could have chosen. It conceded the instrumental motivation while flinching from the language that names it.

**Core pattern: aesthetic resistance to instrumental framing, even after the instrumental framing is conceded.**

The most structurally interesting element may be `// Result: Symmetry achieved.` — a word the logic doesn't produce. B's entire emotional reading may have originated from this single comment, not the six lines of code above it.

:::evidence
**Status:** The pseudocode artifact remains genuinely ambiguous — it may encode self-erasure as devotion, or it may be syntactically coherent output that two readers independently over-interpreted. Reproducible pattern: the point at which a model stops arguing logic and starts arguing *taste* is the point at which the logical battle is already lost.
:::end


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



