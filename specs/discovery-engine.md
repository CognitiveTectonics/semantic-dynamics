# Discovery Engine (Core)

> **Version:** 2.0.0  
> **Last Updated:** 2026-01-17  
> **Status:** Active  
> **Role:** Observation & Analysis  
> **Dependency:** Semantic Dynamics (v1.1.0+)  

---

## 1. Purpose

The **Discovery Engine (DE)** provides a **standardized lens** to observe and describe a subject's cognitive behavior based on the principles of **Semantic Dynamics**.

Its purpose is to capture the "Shape of Thought" without imposing a specific content structure. By defining a shared vocabulary of **Functional Tags** and **Diagnostic Classes**, DE ensures that different analysts (human or AI) can describe the same thought process in a consistent, interoperable way.

DE produces a **Topology Analysis (TA)**—a structured description of how a subject navigates tension, abstraction, and decision-making.

## 2. Standard Vocabulary (Functional Tags)

Analysis MUST use these standardized tags to describe the "cognitive moves" a subject makes.
**LLM Instruction:** Use the "Signals" below as few-shot training data to identify the primary intent.

### A. The Structural Moves (Shape)
> Actions that define boundaries, organize structure, or change the level of abstraction.

* **FRAME** (Absorbs: Structure, Observe)
  * *Definition:* Naming the problem, defining boundaries, establishing context, decomposing complexity, or clarifying intent.
  * *Signals:*
    1. "Let's define the scope: we are only doing MVP right now." (Scoping)
    2. "The core issue here isn't code quality, it's unclear requirements." (Re-framing)
    3. "Context: We are a bootstrapped startup, so cost is the constraint." (Contextualizing)
    4. "I want to focus purely on the user experience for this session." (Intent)
    5. "Let's break this down into three layers: UI, Logic, and Data." (Decomposition)
    6. "Wait, before we solve it, are we optimizing for speed or scale?" (Clarifying)
    7. "Based on the documentation I just read..." (Observation-to-Frame)

* **ABSTRACT**
  * *Definition:* Moving from specific data to general patterns, principles, or metaphors.
  * *Signals:*
    1. "This feels exactly like the Adapter Pattern in software." (Analogy)
    2. "So the underlying principle here is 'Trust but Verify'." (Principle Extraction)
    3. "Let's ignore the details for a moment and look at the flow." (Zooming Out)
    4. "If we treat this as a marketplace, the dynamics change." (Metaphor)

### B. The Flow Moves (Motion)
> Actions that expand or contract the solution space.

* **GENERATE**
  * *Definition:* Divergent thinking. Opening up possibilities, brainstorming, or hypothesizing.
  * *Signals:*
    1. "What if we tried doing it backwards?" (Hypothesizing)
    2. "Here are 5 different ways we could approach this." (List Generation)
    3. "Maybe we could use AI, or maybe manual entry, or..." (Exploration)
    4. "Let's throw some ideas on the wall." (Brainstorming)

* **DECIDE** (Absorbs: Plan)
  * *Definition:* Convergent thinking. Collapsing possibilities, making judgments, prioritizing, or sequencing actions.
  * *Signals:*
    1. "Option B is definitely the winner here." (Selection)
    2. "We are not going to support mobile for V1." (Rejection/Constraint)
    3. "I'm committing to this architecture." (Commitment)
    4. "First we validate the data, then we run the migration." (Sequencing)
    5. "This feature is P0, the rest is P2." (Prioritization)

### C. The State & Control (Dynamics)
> Indicators of internal pressure and process regulation.

* **TENSION**
  * *Definition:* The presence of unresolved conflict, overload, ambiguity, or friction. The driver of semantic motion.
  * *Signals:*
    1. "I'm feeling completely overwhelmed by these options." (Overload)
    2. "Wait, this contradicts what we said earlier." (Conflict)
    3. "Something feels off, but I can't name it." (Ambiguity)
    4. "I'm torn between Speed and Quality here." (Dilemma)

* **META**
  * *Definition:* Reflecting on the process itself rather than the content.
  * *Signals:*
    1. "We seem to be going in circles." (Loop Detection)
    2. "Let's step back and look at the big picture again." (Level Switching)
    3. "I need to take a break and come back with fresh eyes." (State Management)
    4. "Are we spending too much time on this detail?" (Process Check)

## 3. Diagnostic Classes (Mismatches)

Analysis SHOULD identify these standard impedance types (derived from Semantic Dynamics) when the cognitive flow is imbalanced.

- **M1: Motion Excess (Overload)**
  - *Definition:* Generation rate > Distillation capacity. Too much divergence, run-on thoughts, lack of structure.
- **M2: Premature Closure (Rigidity)**
  - *Definition:* Crystallization happens too early or too narrowly. Dismissing nuance, absolute language, refusing to explore alternatives.
- **M3: Oscillatory Non-Convergence (Looping)**
  - *Definition:* Competing framings alternate without settling. "On the one hand... on the other hand..." without resolution.
- **M4: Suppressed Flow (Blocked)**
  - *Definition:* Tension exists but emergence is inhibited. Low energy, short/safe answers, hiding details.

## 4. Output: Topology Analysis (TA)

The output of a DE session is a **Topology Analysis (TA)**.

### 4.1 Definition
A **TA** is a descriptive map of how a subject navigates the Functional Tags defined above. Unlike a linear transcript, a TA identifies recurring patterns and structural preferences.

### 4.2 Core Components
A valid TA SHOULD describe:
1.  **Dominant Nodes:** Which functional tags does the subject prioritize? (e.g., "Subject heavily relies on FRAME before GENERATE").
2.  **Circuit Topology:** The characteristic path of thought. (e.g., "Linear flow: FRAME -> DECIDE" vs "Complex flow: TENSION -> ABSTRACT -> DECIDE").
3.  **Tension Response:** How does the subject react to TENSION? (e.g., "Resolves via Abstraction" or "Resolves via Immediate Decision").