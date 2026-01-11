# Self Model Protocol Specification

> **Version:** 1.2.0  
> **Last Updated:** 2026-01-11  
> **Status:** Active  
> **Architecture:** 3-Tier (Core + Profile + Extension)

---

## 1. Introduction

The **Self Model Protocol (SMP)** defines the schema for a **Portable Self-Model (PSM)**. A PSM is a crystallized cognitive artifact that allows AI agents to instantly align with a subject's thinking patterns, values, and interaction protocols without needing extensive context windows or repetitive prompting.

### The 3-Tier Architecture
A valid PSM MUST contain a **Core** layer. The **Profile** and **Extension** layers are optional.

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
* **Cognitive Rhythm:** The **implicit, immutable** internal processing order (e.g., *Observe -> Abstract -> Solve*). It defines the cognitive system's 'operating cycle' regardless of the task.
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

## 5. Rhythm Activation Policy (Standard Interface)
> **Purpose:** Defines the standard execution modes for SMP-compliant models.  
>   
> **Requirement:** All SMP models MUST support the following modes to ensure compatibility with external runtime engines (such as bootloaders or agent frameworks).

### 5.1 Standard Execution Modes

Implementations must support the following three levels of cognitive engagement:

* **[Mode: Chat] (Low Latency):**
    * **Behavior:** Casual, lightweight, minimal structure.
    * **Constraint:** Must NOT emit a Policy Trace.
* **[Mode: Assist]  (Default / Balanced):**
    * **Behavior:** Structured, helpful, high-utility. Uses Core traits but does not force full reasoning loops.
    * **Constraint:** Must NOT emit a Policy Trace.
* **[Mode: Rhythm]  (High Consistency):**
    * **Behavior:** Activates the full **Cognitive Rhythm** (defined in Core 2.1).
    * **Constraint:** **MUST** emit a **Policy Trace** (a visible manifest of applied logic/trade-offs) at the end of the response.

### 5.2 Portable Runtime Header (PRH)
> **Definition:** A standardized preamble used when exporting the model to generic LLM environments.

When an SMP model is instantiated in an environment without a specialized engine, it SHOULD include a header that instructs the LLM on:
1.  **Goal Statement:** (e.g., Maintain policy consistency).
2.  **Mode Definitions:** Brief descriptions of Mode Chat/Assist/Rhythm.
3.  **Triggers:** When to escalate to Mode Rhythm (e.g., user request, high stakes).

*(Note: Specialized engines are permitted to optimize this header into compressed instructions or system prompts, provided the semantic behavior of the Modes remains consistent.)*

---

## Appendix A: SMP Template (Copy & Paste)

```markdown
# [Model Name] Portable Self-Model
> **Protocol:** SMP v1.2.0
> **Version:** 1.0
> **Classification:** [Private/Public]

## 1. Core (Mandatory)
### 1.1 Cognitive Signature
- **Processing Traits:** [e.g., Structure-First]
- **Cognitive Rhythm:** [e.g., Observe -> Abstract -> Solve]
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
- **Default Mode:** [Mode: Assist]
- **Escalation Trigger:** ["run full rhythm", "critical decision"]
```