# Discovery Engine (Core)

> **Version:** 1.0.0  
> **Last Updated:** 2026-01-01  
> **Status:** Active  

---

## 1. Purpose
The Discovery Engine (DE) provides a **standardized lens** to observe and describe a subject's cognitive behavior. By defining a shared vocabulary of **Functional Tags** and **Diagnostic Classes**, DE ensures that different analysts (human or AI) can describe the same thought process in a compatible way, without prescribing *how* that analysis is stored or implemented.

## 2. Standard Vocabulary (Functional Tags)
Analysis MUST use these standardized tags to describe the "cognitive moves" a subject makes.
**LLM Instruction:** Use the "Signals" below as few-shot training data to identify the primary intent.

### A. The Structural Moves

* **FRAME**
  * *Definition:* Naming the problem, defining boundaries, clarifying intent, or asking "what are we really solving?".
  * *Signals:*
    1. "Let's define the scope: we are only doing MVP right now." (Scoping)
    2. "The core issue here isn't code quality, it's unclear requirements." (Re-framing)
    3. "I want to focus purely on the user experience for this session." (Intent)
    4. "Context: We are a bootstrapped startup with limited runway." (Contextualizing)
    5. "Wait, are we solving for speed or for scalability?" (Clarifying Question)
    6. "Let's park that topic for later; it's out of bounds." (Boundary setting)

* **ABSTRACT**
  * *Definition:* Moving from specific to general; extracting invariants, schemas, patterns, analogies, or underlying principles.
  * *Signals:*
    1. "This feels exactly like the 'Adapter Pattern' in software design." (Analogy)
    2. "If we generalize this rule, it applies to all user types." (Generalization)
    3. "The underlying principle here is 'Trust but Verify'." (Principle extraction)
    4. "It's basically a supply and demand problem." (Model matching)
    5. "Let's ignore the implementation details and look at the topology." (Abstraction)
    6. "Conceptually, this is just a pipe-and-filter architecture." (Schema)

* **STRUCTURE**
  * *Definition:* Decomposing complexity into parts, layers, steps, lists, or interfaces.
  * *Signals:*
    1. "I'll break this down into three phases: Discovery, Build, Ship." (Phasing)
    2. "Step 1: Fix the bug. Step 2: Write tests. Step 3: Deploy." (Sequencing)
    3. "We have the UI layer, the Logic layer, and the Data layer." (Layering)
    4. "Here is the checklist of things we need." (Listing)
    5. "Let's decouple module A from module B." (Decomposition)
    6. "First, second, third..." (Ordering)

### B. The Flow Moves

* **OBSERVE**
  * *Definition:* Gathering data, reading carefully, retrieving facts, or revisiting inputs.
  * *Signals:*
    1. "Let me check the logs to see what actually happened." (Data retrieval)
    2. "Reading through the documentation now..." (Information intake)
    3. "Based on the email the client sent yesterday..." (Fact referencing)
    4. "I notice that the latency spikes every morning at 9 AM." (Observation)
    5. "Let's review what we wrote in the last session." (Recall)
    6. "The error message says 'NullReferenceException'." (Evidence citation)

* **DECIDE**
  * *Definition:* Forcing convergence, committing to a direction, choosing a path, or cutting off debate.
  * *Signals:*
    1. "I'm going with Option B." (Selection)
    2. "Decision: We will use Python for this backend." (Commitment)
    3. "Let's kill this feature. It's not worth the effort." (Cut)
    4. "Enough discussion, let's ship it." (Forcing action)
    5. "I am confident this is the right path." (Convergence)
    6. "The verdict is: No go." (Judgment)

* **TENSION**
  * *Definition:* Surfacing conflict, overload, confusion, ambiguity, or misalignment.
  * *Signals:*
    1. "I'm feeling completely overwhelmed by these tasks." (Overload)
    2. "This code is a mess; I hate touching it." (Friction)
    3. "I'm torn between doing it fast vs. doing it right." (Dilemma/Conflict)
    4. "Something feels off about this plan, but I can't name it." (Ambiguity)
    5. "I have too many ideas and don't know where to start." (Fog)
    6. "This requirements document contradicts itself." (Misalignment)

### C. The Meta Moves

* **META**
  * *Definition:* Reflecting on the process itself; checking rhythm or adjusting the approach.
  * *Signals:*
    1. "Are we bike-shedding on minor details?" (Process check)
    2. "I think we are going too fast; let's slow down." (Pacing)
    3. "This brainstorming method isn't working for me." (Method adjustment)
    4. "I need to take a break and come back with fresh eyes." (State management)
    5. "Let's zoom out and look at the big picture again." (Level switching)
    6. "I feel like I'm repeating myself." (Loop detection)

## 3. Diagnostic Classes (Mismatches)
Analysis SHOULD identify these standard impedance types (derived from Semantic Dynamics) when the cognitive flow is imbalanced.

- **M1: Motion Excess (Overload)**
  - *Definition:* Generation rate > Compression capacity. Too much divergence, run-on thoughts, lack of structure, high anxiety.
- **M2: Premature Closure (Lock-in)**
  - *Definition:* Crystallization happens too early or too narrowly. Dismissing nuance, absolute language, refusing to explore alternatives.
- **M3: Oscillatory Non-Convergence (Looping)**
  - *Definition:* Competing framings alternate without settling. "On the one hand... on the other hand..." without resolution.
- **M4: Suppressed Flow (Blocked)**
  - *Definition:* Tension exists but emergence is inhibited. Low energy, extremely short/safe answers, hiding details.

## 4. The Rhythm Descriptor (RD)
An **RD** is a descriptive summary of a subject’s cognitive pattern using the vocabulary above.
- It is **Descriptive**, not prescriptive.
- It does **not** require a specific file format (it can be a paragraph, a list, or a JSON object).
- **Core Requirement:** An RD MUST explicitly reference the subject's usage of Functional Tags and presence of Mismatches.
