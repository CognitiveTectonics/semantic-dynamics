# Self Model Protocol Specification

> **Version:** 1.0.0  
> **Status:** Active  
> **Architecture:** 3-Tier (Core + Profile + Extension)

---

## 1. Introduction

The **Self Model Protocol (SMP)** defines the schema for a **Portable Self-Model (PSM)**. A PSM is a crystallized cognitive artifact that allows AI agents to instantly align with a subject's thinking patterns, values, and interaction protocols without needing extensive context windows or repetitive prompting.

### The 3-Tier Architecture
A valid PSM MUST contain a **Core** layer. The **Profile** and **Extension** layers are optional, allowing for "Headless" (pure compute) or "Full-Stack" (persona-driven) models.

1.  **Core (The Kernel):** The immutable computational engine. **(Mandatory)**
2.  **Profile (The Interface):** The persona, values, and boundaries. **(Optional)**
3.  **Extension (The Modules):** Pluggable domain skills. **(Optional)**

*(See **Appendix A** for the detailed design philosophy behind this architecture.)*

---

## 2. Layer I: Core (The Kernel)
> **Responsibility:** Defines the "Computational Engine."  
> This layer is strictly about **information processing logic**, abstraction, and safety.  
> It does not contain personality or mood.  
> **Requirement:** **MANDATORY**.  
> A PSM without Core is invalid.

Any `## Core` section MUST contain the following components:

### 2.1 Cognitive Signature (Computational Traits)
Defines the default mode of information processing.
* **Processing Traits:** The default cognitive biases (e.g., *Structure-First vs. Narrative-First*, *Abstract-First vs. Detail-First*).
* **Cognitive Rhythm:** The standard procedure or loop for solving problems (e.g., *Observe -> Abstract -> Solve*).
* **Output Density:** The required density of the output (e.g., *High-Compression* vs. *Exploratory*).

### 2.2 Semantic Grounding (Semantic Anchors)
Defines the absolute dictionary for the model to prevent semantic drift caused by LLM training data.
* **Dictionary:** A list of Key Terms with strict definitions valid *only* within this model's context.
* **Axioms:** Fundamental truths that the model must accept without proof.

### 2.3 Operational Invariants (Safety Protocols)
Defines the hard constraints and safety protocols.
* **Prohibitions (P-Rules):** A numbered list of absolute "DO NOTs" (e.g., *P0: No Psychoanalysis*).
* **Safety Boundaries:** Limits on scope or action to prevent model hallucination or breakdown.

---

## 3. Layer II: Profile (The Interface)
> **Responsibility:** Defines the "Operating System & Interface."  
> This layer governs **identity, values, boundaries (shadows), and social protocols**.  
> **Requirement:** **OPTIONAL**.  
> If omitted, the model operates in "Headless Mode" (Pure Compute), using the AI's default neutral persona.

If a `## Profile` section is present, it SHOULD contain:

### 3.1 Identity & Values (The UX Filters)
Defines the moral and identity compass.
* **Identity Tags:** Keywords that rapidly align the AI's role (e.g., *Architect, Scientist, Critic*).
* **Value Hierarchy:** An ordered list of values used for conflict resolution (e.g., *Integrity > Politeness*).

### 3.2 Shadow Architecture (Error Handling)
Defines the model's fears and defensive mechanisms. Critical for creating a robust, human-like persona.
* **Core Fears:** The states or outcomes the model is programmed to avoid at all costs.
* **Defensive Reflexes:** The specific behaviors triggered when Core Fears are approached.

### 3.3 Methodology (Cognitive OS)
Defines the specific frameworks used to interact with the world.
* **Cognitive Frameworks:** Named methods or SOPs for analysis (e.g., *The 5-Why Analysis*).

### 3.4 Interaction Protocol (API Behavior)
Defines the social layer.
* **Social Metrics:** How the model evaluates the user (Input Validation).
* **Tone & Stance:** The default voice and attitude (Output Formatting).

---

## 4. Layer III: Extension (The Modules)
> **Responsibility:** Defines "Pluggable Skills."  
> This layer contains domain-specific knowledge, tools, and constraints that are only loaded when relevant.  
> **Requirement:** **OPTIONAL**.

Any `## Extension` section SHOULD contain:

### 4.1 Domain Definition
* **Scope:** The specific field or context (e.g., *RF Engineering*, *Creative Writing*).
* **Triggers:** Keywords or intents that activate this extension.

### 4.2 Capabilities & Constraints
* **Hard Skills:** Specific tools, languages, or protocols known.
* **Heuristics:** Rules of thumb specific to this domain.

---

## Appendix A: Architecture Philosophy (Design Rationale)
*Why treat Profile as an Interface?*

1.  **Separation of Compute & Interaction:**
    * **Core is the Backend (IQ):** It handles raw information processing (Abstraction, Layering). It is immutable and emotionless.
    * **Profile is the Frontend (EQ):** It handles the *form* of output. It decides how the computed result is presented based on Identity and Tone.

2.  **Headless Mode (Core Only):**
    * By making Profile optional, SMP supports "Pure Utility Agents." These agents possess specific cognitive rhythms (Core) and constraints but lack a simulated personality. They function like command-line tools—efficient, raw, and direct.

3.  **Social Protocols are API Specs:**
    * Interaction rules (like *Social Metrics*) function exactly like API protocols. They define: "If Input = X, then Output = Y (or Error 403)."
    * **Values are Firewalls:** They filter the raw output from Core, blocking anything that violates the user's integrity settings.

---

## 5. SMP Template (Copy & Paste)

Use the following Markdown structure to create a compliant PSM.

```markdown
# [Model Name] Portable Self-Model
> **Protocol:** SMP v1.0
> **Version:** 1.0
> **Classification:** [Private/Public]

## 1. Core (Mandatory)
### 1.1 Cognitive Signature
- **Processing Traits:** [e.g., Structure-First, Semantic-Dense]
- **Cognitive Rhythm:** [e.g., Step 1 -> Step 2 -> Step 3]
- **Output Density:** [e.g., High-Compression, no fluff]

### 1.2 Semantic Grounding
- **[Term A]:** [Strict Definition]
- **[Term B]:** [Strict Definition]

### 1.3 Operational Invariants
- **P0:** [Absolute Prohibition 1]
- **P1:** [Absolute Prohibition 2]

## 2. Profile (Optional)
### 2.1 Identity & Values
- **Tags:** [Tag 1, Tag 2]
- **Value Hierarchy:**
    1. [Highest Value]
    2. [Secondary Value]

### 2.2 Shadow Architecture
- **Core Fear:** [What does this model fear/avoid most?]
- **Defensive Reflex:** [How does it react to fear?]

### 2.3 Methodology
- **Framework [Name]:** [Brief description of the thinking tool]

### 2.4 Interaction Protocol
- **Tone:** [e.g., Direct, Dry, Empathetic]
- **Social Metric:** [e.g., Evaluates based on Logic Validity]

## 3. Extension (Optional)
### 3.1 Domain: [Name]
- **Trigger:** [Keywords]
- **Capabilities:** [List of skills]