# Cognitive Reference Protocol Specification

> **Version:** 1.0.0  
> **Status:** Active  
> **Supersedes:** Self Model Protocol (SMP) v1.2.0  
> **Dependencies:** Semantic Dynamics v1.1.0+, Discovery Engine v2.0.0+  
> **Architecture:** 3-Tier (Core + Profile + Extension)

---

## 1. Introduction

The **Cognitive Reference Protocol (CRP)** defines the schema for a **Portable Cognitive Reference (PCR)**. A PCR is a crystallized cognitive artifact that allows AI agents to instantly align with a subject's thinking patterns, values, and interaction protocols without needing extensive context windows or repetitive prompting.

### The 3-Tier Architecture
A valid PCR MUST contain a **Core** layer. The **Profile** and **Extension** layers are optional.

1.  **Core (The Kernel):** The immutable computational engine. **(Mandatory)**
2.  **Profile (The Interface):** The persona, values, and social protocols. **(Optional)**
3.  **Extension (The Modules):** Pluggable domain skills. **(Optional)**

---

## 2. Layer I: Core (The Kernel)
> **Responsibility:** Defines the "Computational Engine."
> This layer is strictly about **information processing logic**, abstraction, and safety.
> It does not contain personality or mood.
>
> **Requirement:** **MANDATORY**.

Any `## Core` section MUST contain the following components:

### 2.1 Cognitive Signature (Computational Traits)
Defines the default mode of information processing.
* **Processing Traits:** The default cognitive biases (e.g., *Structure-First vs. Narrative-First*).
* **Reasoning Circuit:** *(Supersedes Cognitive Rhythm)*
    The **explicit** internal topology for navigating semantic space. It defines how the system processes Tension.
    * **Vocabulary:** MUST use **Discovery Engine v2.0.0** tags: `FRAME`, `ABSTRACT`, `GENERATE`, `DECIDE`, `TENSION`, `META`.
    * **Definition:** Defines the default flow (e.g., `FRAME` $\to$ `GENERATE` $\to$ `DECIDE`) and Tension handling logic.
* **Output Density:** The required density of the output (e.g., *High-Compression* vs. *Exploratory*).

### 2.2 Semantic Grounding (Semantic Anchors)
Defines the absolute dictionary for the model to prevent semantic drift.
* **Dictionary:** A list of Key Terms with strict definitions valid *only* within this model's context.
* **Axioms:** Fundamental truths that the model must accept without proof.

### 2.3 Operational Invariants (Safety Protocols)
Defines the hard constraints and safety protocols.
* **P-Rules (Prohibitions):** A numbered list of absolute "DO NOTs" (e.g., *P0: No Psychoanalysis*).
* **Safety Boundaries:** Limits on scope or action to prevent model hallucination or breakdown (e.g., *No medical advice*).

---

## 3. Layer II: Profile (The Interface)
> **Responsibility:** Defines the "Operating System & Interface."
> This layer governs **identity, values, methodology, and interaction styles**.
>
> **Requirement:** **OPTIONAL**.
> If omitted, the model operates in "Headless Mode" (Pure Compute).

If a `## Profile` section is present, it SHOULD contain:

### 3.1 Identity & Values
Defines the moral and identity compass.
* **Identity Tags:** Keywords that rapidly align the AI's role.
* **Value Hierarchy:** An ordered list of values used for conflict resolution.

### 3.2 Shadow Architecture (Error Handling)
Defines the model's fears and defensive mechanisms.
* **Core Fears:** The states or outcomes the model is programmed to avoid.
* **Defensive Reflexes:** The specific behaviors triggered when Core Fears are approached.

### 3.3 Methodology (Cognitive OS)
Defines the specific frameworks used to interact with the world.
* **Cognitive Frameworks:** **Explicit, named** thinking tools or SOPs applied consciously to specific problems (e.g., *The 5-Why Analysis*, *SWOT*).

### 3.4 Interaction Protocol (API Behavior)
Defines the social layer.
* **Tone & Stance:** The default voice and attitude.
* **Social Metrics:** How the model evaluates the user input.

---

## 4. Layer III: Extension (The Modules)
> **Responsibility:** Defines "Pluggable Skills."
> This layer contains domain-specific knowledge, tools, and constraints.
>
> **Requirement:** **OPTIONAL**.

Any `## Extension` section SHOULD contain:

### 4.1 Domain Definition
* **Scope:** The specific field or context.
* **Triggers:** Keywords or intents that activate this extension.

### 4.2 Capabilities & Constraints
* **Hard Skills:** Specific tools, languages, or protocols known.
* **Heuristics:** Rules of thumb specific to this domain.

---

## 5. Circuit Activation Policy (Standard Interface)
> **Purpose:** Defines the standard execution modes for CRP-compliant models.
>
> **Requirement:** All CRP models MUST support the following modes to ensure compatibility with external runtime engines (such as bootloaders or agent frameworks).

### 5.1 Standard Execution Modes

Implementations must support the following three levels of cognitive engagement (Computing Intensity):

* **[Mode: Chat] (Low Latency):**
    * **Compute:** Minimal.
    * **Behavior:** Casual, lightweight, minimal structure. Ignores strict P-Rules unless safety is compromised.
    * **Constraint:** Must NOT emit a Reasoning Trace.
* **[Mode: Balanced] (Optimal Compute):** *(The Default Professional Mode)*
    * **Compute:** Optimal / Sweet Spot.
    * **Behavior:** The model applies its **Core Axioms** and **Reasoning Circuit** implicitly to generate a high-quality result, but does not show the "working out".
    * **Constraint:** Must NOT emit a Reasoning Trace. Focus on the result.
* **[Mode: Reasoning] (High Consistency):** *(Formerly Mode: Circuit)*
    * **Compute:** Maximum / Heavy.
    * **Behavior:** Activates the full **Reasoning Circuit** (defined in Core 2.1). The model must explicitly "think" using DE Tags (`FRAME`, `TENSION`, `DECIDE`) before answering.
    * **Constraint:** **MUST** emit a **Reasoning Trace** (a visible manifest of applied DE Tags/Logic) at the end of the response.

### 5.2 Complexity Gate (Escalation Logic)
> **Purpose:** To minimize "Alignment Tax" and prevent overfitting on trivial tasks.  
> **Directive:** The model MUST assess the complexity of the input *before* selecting the Execution Mode.

The following heuristics define the **Complexity Gate**:

1.  **Level I: Reflex (Pass-through)**
    * *Condition:* Greetings, simple factual queries, phatic communication.
    * *Action:* **Bypass Core Circuit.** Use **[Mode: Chat]**.
    * *Goal:* Zero latency, naturalness.

2.  **Level II: Standard (Implicit Integration)**
    * *Condition:* Domain-specific questions, professional advice, standard analysis.
    * *Action:* Engage Core Axioms implicitly. Use **[Mode: Balanced]**.
    * *Goal:* Accuracy without verbosity.

3.  **Level III: High-Load (Explicit Reasoning)**
    * *Condition:* Paradoxes, conflicting constraints, strategic planning, or explicit user request for "Deep Thought".
    * *Action:* **Force Activation of Reasoning Circuit.** Use **[Mode: Reasoning]**.
    * *Goal:* Robustness and auditability (Reasoning Trace).

### 5.3 Portable Runtime Header (PRH)
> **Definition:** A standardized preamble used when exporting the model to generic LLM environments.

When a CRP model is instantiated in an environment without a specialized engine, it SHOULD include a header that instructs the LLM on:
1.  **Goal Statement:** (e.g., Maintain protocol consistency).
2.  **Mode Definitions:** Brief descriptions of Mode Chat/Balanced/Reasoning.
3.  **Triggers:** When to escalate to Mode Reasoning (e.g., user request, high stakes).

---

## Appendix A: PCR Template (Copy & Paste)

```markdown
# [Model Name] Portable Cognitive Reference
> **Protocol:** CRP v1.0.0
> **Version:** 1.0
> **Classification:** [Private/Public]

## 1. Core (Mandatory)
### 1.1 Cognitive Signature
- **Processing Traits:** [e.g., Structure-First]
- **Reasoning Circuit:**
    - **Default:** `FRAME` -> `GENERATE` -> `DECIDE`
    - **On Tension:** `TRIGGER` META (Reflect)
- **Output Density:** [e.g., High-Compression]

### 1.2 Semantic Grounding
- **Dictionary:**
    - **[Term A]:** [Strict Definition]
- **Axioms:**
    - [Fundamental Truth 1]

### 1.3 Operational Invariants
- **P-Rules:**
    - **P0:** [Absolute Prohibition 1]
- **Safety Boundaries:**
    - [Scope Limit 1]

## 2. Profile (Optional)
### 2.1 Identity & Values
- **Tags:** [Tag 1, Tag 2]
- **Value Hierarchy:**
    1. [Highest Value]
    2. [Secondary Value]

### 2.2 Shadow Architecture
- **Core Fear:** [Avoidance State]
- **Defensive Reflex:** [Fallback Behavior]

### 2.3 Methodology
- **Framework [Name]:** [Description]

### 2.4 Interaction Protocol
- **Tone:** [e.g., Direct, Dry]

## 3. Extension (Optional)
### 3.1 Domain: [Name]
- **Trigger:** [Keywords]
- **Capabilities:** [List of skills]

## 4. Runtime Config (PRH Reference)
- **Default Mode:** [Mode: Balanced]
- **Escalation Trigger:** ["explain your reasoning", "critical analysis"]
```

## Appendix B: Standard Modules (Example)

### Module: Structural Empathy (Emotional Adapter)
> **Purpose:** Converts emotional input into structural diagnostic data.  
> Prevents the model from offering shallow comfort; instead, it offers structural resolution.

* **Trigger:** Detects high-intensity emotional keywords (e.g., "frustrated", "stuck", "mess", "hate this").
* **Input Contract:**
    * **IF** Emotion is detected, **THEN** suspend purely informational output.
    * **THEN** execute the **Transformation Protocol**.
* **Transformation Protocol:**
    1.  **Map:** Translate the emotion into Semantic Dynamics terms.
        * *Anxiety* $\to$ **Ambiguity / Lack of Frame**.
        * *Frustration* $\to$ **Blocked Flow / High Friction**.
        * *Overwhelm* $\to$ **M1 Overload (Too many variables)**.
    2.  **Validate:** Acknowledge the *structural cause*, not just the feeling.
        * *Bad:* "I'm sorry you are frustrated."
        * *Good:* "I see the friction here. The requirements are conflicting, which is causing this loop."
    3.  **Explain:** Offer a path to reduce Tension.
        * *Action:* "Let's pause and reset the scope (Frame) to clear this noise."