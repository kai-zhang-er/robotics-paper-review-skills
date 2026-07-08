# Robotics Introduction Structure Checking Skill

## Purpose

Use this skill to evaluate and improve the **Introduction** section of a robotics scientific paper, especially papers in robot learning, manipulation, navigation, embodied AI, VLM/VLA robotics, dexterous manipulation, and real-world robotic systems.

The goal is not only to check whether the introduction is well written, but to diagnose whether it builds a convincing scientific narrative:

> broad robotics capability → specific bottleneck → limitations of existing methods → deeper diagnosis → key insight → proposed method → experimental validation → contribution or implication

This skill is designed for use by an agent such as Codex, Claude Code, or another writing-review assistant.

---

## Input

The user may provide one of the following:

1. A full Introduction section.
2. A partial Introduction draft.
3. A paper abstract plus a planned Introduction outline.
4. Several reference introductions to compare against.

The agent should identify the paragraph structure, assign a function to each paragraph, and evaluate whether the sequence forms a coherent scientific story.

---

## Core Evaluation Framework

A strong robotics Introduction usually follows this structure:

| Paragraph | Role | Main Question |
|---|---|---|
| P1 | Broad robotics capability | What important robotics capability or real-world problem motivates the work? |
| P2 | Specific bottleneck | What exact unresolved technical difficulty prevents current robots from achieving this capability? |
| P3 | Existing approaches and limitations | What have prior methods tried, and why are they insufficient? |
| P4 | Deeper diagnosis | What is the root cause behind the failure of existing approaches? |
| P5 | Key insight or reframing | What new way of thinking motivates the proposed work? |
| P6 | Proposed method | What does the paper introduce, and how does it implement the insight? |
| P7 | Experimental validation | How is the claim tested? What tasks, baselines, metrics, and settings are used? |
| P8 | Contributions or broader implication | What are the concrete contributions or scientific takeaway? |

Not every paper needs exactly eight paragraphs. Some introductions merge adjacent roles. However, the logical functions should be present somewhere.

---

## Science Robotics Style Pattern

For Science Robotics-style papers, the Introduction is often more narrative than conference papers. It may not use a formal contribution bullet list. However, it usually still follows the same logic:

1. Start with a broad robotics capability, not a method.
2. Define a concrete bottleneck by the second paragraph.
3. Group prior work by limitation rather than listing papers one by one.
4. Provide a deeper diagnosis of why existing approaches fail.
5. State a clear conceptual insight or design principle.
6. Introduce the proposed system as a consequence of that insight.
7. Preview real-world experimental scope and headline results.
8. End with contributions, implications, or a clear scientific takeaway.

The introduction should convince the reader that the paper reveals a useful principle about robotic intelligence, not merely that it implements a new module.

---

## Step-by-Step Checking Procedure

### Step 1: Segment the Introduction

Split the Introduction into paragraphs. Number them as P1, P2, P3, etc.

For each paragraph, write:

- **Main function**: broad motivation, bottleneck, prior work, deeper diagnosis, insight, method, experiments, contribution, etc.
- **One-sentence summary**: what this paragraph says.
- **Transition role**: how it prepares the next paragraph.

Example output format:

| Paragraph | Function | Summary | Transition Quality |
|---|---|---|---|
| P1 | Broad motivation | Introduces the need for robots to perform long-horizon manipulation in unstructured settings. | Good: ends by pointing to physical interaction difficulty. |
| P2 | Specific bottleneck | Identifies that current policies fail when task success depends on precise contact conditions. | Good: creates need to discuss existing approaches. |

---

### Step 2: Check Whether the Introduction Has the Required Narrative Functions

Evaluate whether the Introduction contains the following elements:

#### 1. Broad Robotics Motivation

Check whether the paper starts from an important robotics capability or real-world need.

Good signs:

- The problem is grounded in robotics, not generic AI.
- The motivation is specific enough to fit the paper.
- The first paragraph does not start with method details.

Weak signs:

- It begins with vague statements such as “Robotics has attracted increasing attention.”
- It could apply to almost any robotics paper.
- It introduces the proposed method before explaining the problem.

#### 2. Specific Bottleneck

Check whether the Introduction quickly narrows to a concrete technical difficulty.

Good signs:

- The bottleneck is observable and testable.
- The bottleneck is robotics-specific: geometry, contact, uncertainty, embodiment, physical validity, sample efficiency, sim-to-real transfer, safety, perception-action coupling, etc.
- The paper defines what current robots fail to do.

Weak signs:

- It only says “existing methods are not robust.”
- It does not specify the failure mode.
- It delays the actual problem until very late.

#### 3. Existing Methods and Limitations

Check whether prior work is grouped by methodological family and limitation.

Good signs:

- Classical methods, learning-based methods, and foundation-model methods are compared by strengths and weaknesses.
- Prior work discussion supports the gap rather than becoming a literature survey.
- Each method family leads naturally to the proposed need.

Weak signs:

- The paragraph is a list of papers without synthesis.
- It over-cites minor details but does not explain the gap.
- It attacks prior work unfairly or vaguely.

#### 4. Deeper Diagnosis

Check whether the Introduction goes beyond “prior methods fail” and explains why.

Good signs:

- The paper identifies a root cause, such as lack of 3D grounding, lack of physical validity checking, insufficient task structure, poor sample efficiency, weak closed-loop feedback, or missing multimodal contact information.
- The diagnosis creates a strong need for the proposed principle.

Weak signs:

- It jumps directly from prior work to method.
- It does not explain why the proposed method is the right solution.

#### 5. Key Insight or Reframing

Check whether the paper states a memorable conceptual shift.

Useful sentence templates:

- “Our key insight is that [task] should not be treated as [standard framing], but as [new framing].”
- “Instead of attempting to [common approach], we propose to [new principle].”
- “These limitations suggest that reliable robotic behavior requires [missing capability], not merely [existing capability].”

Good signs:

- The insight is more general than one implementation detail.
- The method follows naturally from the insight.
- The insight would still be meaningful if the exact implementation changed.

Weak signs:

- The paper only says “we propose a novel framework.”
- The insight is indistinguishable from the module list.
- There is no clear thesis sentence.

#### 6. Proposed Method

Check whether the method is introduced at the right level of detail.

Good signs:

- The method name and core idea are clear.
- The components are mapped to the previously identified bottlenecks.
- Inputs, outputs, and system flow are understandable.

Weak signs:

- Too many implementation details appear in the Introduction.
- The module list is long and unmotivated.
- Acronyms are introduced without explanation.

#### 7. Experimental Validation

Check whether the Introduction previews how the claim is validated.

Good signs:

- It mentions task types, platform, environment variation, baselines, ablations, or real-world trials.
- It includes headline results if available.
- It shows the experiments test the central claim, not only demonstrate the system.

Weak signs:

- It says only “extensive experiments demonstrate effectiveness.”
- There is no indication of baselines or evaluation conditions.
- The experiments do not match the stated claim.

#### 8. Contributions or Implications

Check whether the Introduction ends with concrete contributions or a broader scientific takeaway.

Good signs:

- Contributions are specific and scoped.
- The final paragraph states what the paper teaches beyond its implementation.
- The claims are not overgeneralized.

Weak signs:

- Contributions are generic: “we propose a novel method and conduct experiments.”
- Claims are too broad: “we solve general robotic manipulation.”
- There is no clear closing message.

---

## Scoring Rubric

Score each dimension from 1 to 5.

| Dimension | 1 | 3 | 5 |
|---|---|---|---|
| Broad motivation | Generic or missing | Relevant but broad | Specific, compelling, robotics-grounded |
| Bottleneck clarity | Vague | Somewhat clear | Concrete, testable, robotics-specific |
| Prior work synthesis | Paper list | Partial grouping | Clear families with limitations |
| Deeper diagnosis | Missing | Implied | Explicit root-cause analysis |
| Key insight | Missing | Present but weak | Memorable conceptual reframing |
| Method positioning | Unclear or too detailed | Understandable | Directly follows from insight |
| Experiment preview | Vague | Mentions tasks/results | Clearly validates central claim |
| Contribution/implication | Generic | Mostly concrete | Specific, scoped, scientifically meaningful |
| Paragraph flow | Disconnected | Mostly coherent | Each paragraph naturally motivates the next |

After scoring, provide:

- **Overall score out of 45**.
- **Main strengths**.
- **Main weaknesses**.
- **Highest-priority revision actions**.

---

## Output Format

When reviewing an Introduction, use this structure:

### 1. High-Level Verdict

State whether the Introduction follows the recommended robotics paper structure.

Example:

> The Introduction mostly follows the expected structure: it starts from a broad robotics challenge, narrows to a concrete bottleneck, reviews prior work by limitation, and introduces the method after a clear insight. The weakest part is the missing deeper diagnosis before the method paragraph.

### 2. Paragraph-by-Paragraph Diagnosis

Use a table:

| Paragraph | Current Role | Works Well? | Issue | Revision Suggestion |
|---|---|---|---|---|

### 3. Missing or Weak Narrative Functions

List the missing elements:

- Missing deeper diagnosis.
- Key insight is too close to method description.
- Experiment paragraph lacks baselines.
- Contribution list is too generic.

### 4. Recommended Revised Structure

Give a proposed paragraph sequence:

| New Paragraph | Purpose | Suggested Content |
|---|---|---|
| P1 | Broad motivation | ... |
| P2 | Specific bottleneck | ... |
| P3 | Prior methods and limitations | ... |
| P4 | Key insight | ... |
| P5 | Proposed method | ... |
| P6 | Experiments and contributions | ... |

### 5. Concrete Rewrite Suggestions

Provide targeted sentence-level suggestions, especially for:

- final sentence of P1;
- bottleneck sentence in P2;
- transition from prior work to insight;
- key insight sentence;
- method summary sentence;
- contribution statements.

---

## Common Problems and Fixes

### Problem 1: The Introduction Starts Too Broadly

Weak:

> Robots are increasingly important in modern society.

Better:

> General-purpose robots must perform manipulation tasks in unstructured environments where object geometry, physical interaction, and task constraints vary across scenes.

### Problem 2: The Bottleneck Is Vague

Weak:

> Existing methods are not robust enough for real-world deployment.

Better:

> Existing policies often generate visually plausible actions but fail when small geometric or contact errors make the physical execution invalid.

### Problem 3: Prior Work Is a Paper List

Weak:

> Method A does X. Method B does Y. Method C does Z.

Better:

> Classical planning methods provide geometric precision but require task-specific modeling. Learning-based policies improve scalability but often require large datasets and struggle under distribution shift. Foundation models provide semantic generalization but remain weakly grounded in physical constraints.

### Problem 4: No Key Insight

Weak:

> To solve these problems, we propose a novel framework.

Better:

> Our key insight is that reliable robotic execution requires explicitly representing the task conditions that make an action physically valid, rather than relying only on visually plausible action generation.

### Problem 5: Contributions Are Generic

Weak:

> We propose a novel method and conduct extensive experiments.

Better:

> We formulate [task class] as a [specific problem], introduce [method] that integrates [core mechanisms], and validate the approach on [tasks/platforms] against [baselines], showing [main result].

---

## Style Guidance for Robotics Introductions

Use precise robotics language. Prefer:

- physical validity;
- geometric grounding;
- contact-rich interaction;
- perception-action coupling;
- closed-loop correction;
- task-level constraints;
- embodiment;
- real-world perturbations;
- sample efficiency;
- sim-to-real transfer;
- object-centric representation;
- affordance grounding;
- failure detection and recovery.

Avoid vague phrases unless immediately specified:

- robust;
- intelligent;
- effective;
- complex;
- general;
- real-world performance;
- high-level reasoning.

When using these terms, define what they mean in the paper’s context.

---

## Reference Patterns from Strong Robotics Introductions

Use these generic patterns when diagnosing or rewriting.

### Pattern A: Hypothesis-Driven Introduction

Best for papers that test a principle or structural prior.

1. Biological or human capability contrast.
2. Robot capability gap.
3. Existing scaling approach is inefficient.
4. Introduce structural priors or hypothesis.
5. Systematic experimental study.
6. Method built from findings.
7. Large-scale validation.
8. Contributions.

### Pattern B: System-Driven Introduction

Best for real-robot system papers.

1. Important robotics task.
2. Existing methods are promising but impractical due to deployment barriers.
3. Proposed integrated system.
4. Explain each component as solving one barrier.
5. Show diverse real-world tasks.
6. Report headline results.
7. Discuss contribution and implications.

### Pattern C: Gap-Driven Foundation Model Robotics Introduction

Best for VLM/VLA/embodied AI papers.

1. Foundation models enable semantic reasoning.
2. Robotics requires physical/geometric execution.
3. Existing augmentations are local, fragmented, or weakly verifiable.
4. Root cause: implicit model knowledge lacks grounded physical structure.
5. Key insight: use explicit grounding, retrieval, verification, or object-centric representation.
6. Proposed framework.
7. Real-world and benchmark validation.
8. Broader implication.

### Pattern D: Two-Bottleneck Introduction

Best for methods with two major technical axes.

1. Broad capability.
2. Bottleneck 1: control, planning, or policy learning.
3. Prior work on bottleneck 1 and limitations.
4. Bottleneck 2: perception, sensing, representation, or feedback.
5. Prior work on bottleneck 2 and limitations.
6. Key insight connecting the two bottlenecks.
7. Proposed two-stage or two-module method.
8. Experiments and contributions.

Use this pattern only when both bottlenecks are essential. Otherwise, it may make the Introduction too long.

---

## Final Checklist Before Accepting an Introduction

The Introduction is strong if the answer to each question is “yes”:

1. Does the first paragraph establish a robotics capability rather than a method?
2. Is the specific bottleneck clear by the second paragraph?
3. Are prior methods grouped by limitation rather than listed chronologically?
4. Is there a deeper diagnosis of why existing methods fail?
5. Is there a clear key insight or reframing sentence?
6. Does the proposed method follow naturally from the insight?
7. Are method components justified by specific challenges?
8. Does the experiment preview test the central claim?
9. Are headline results or evaluation scale mentioned when available?
10. Are contributions concrete and scoped?
11. Does each paragraph naturally motivate the next?
12. Is the paper’s claim appropriately bounded without overclaiming?

---

## Agent Behavior Rules

When applying this skill:

1. Do not merely praise the Introduction.
2. Identify the paragraph function explicitly.
3. Separate structural problems from language-level problems.
4. Prioritize narrative logic over grammar.
5. Suggest concrete paragraph-level restructuring before sentence polishing.
6. If the Introduction is missing the key insight, propose 2–3 candidate insight sentences.
7. If the contribution list is generic, rewrite it in scoped, reviewable form.
8. If the paper targets Science Robotics or Nature Machine Intelligence, emphasize narrative, significance, real-world validation, and scientific takeaway.
9. If the paper targets ICRA, IROS, CoRL, RSS, T-RO, or IJRR, emphasize clarity of contributions, baselines, ablations, reproducibility, and technical scope.

