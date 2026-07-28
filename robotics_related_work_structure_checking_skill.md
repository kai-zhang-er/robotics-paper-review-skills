# Robotics Related Work Structure Checking Skill

## Purpose

Use this skill to review and improve the **Related Work** section of a robotics scientific paper.

The goal is not merely to check whether enough papers are cited. The review should determine whether the section:

- organizes the literature around the paper's scientific aim;
- synthesizes prior approaches by capability, assumption, and limitation;
- identifies a precise unresolved gap;
- positions the proposed method fairly and specifically;
- predicts the method design, baselines, ablations, and experiments;
- avoids unsupported novelty claims and literature-list writing.

This skill is intended for Codex, Claude Code, and other agents that can read Markdown instructions.

---

## Core Principle

A strong robotics Related Work section should function as a logical bridge:

> paper aim → relevant research lines → strengths and limitations of each line → unresolved requirement → positioning of the proposed work → experimental comparisons implied by that positioning

Related Work is not a catalogue of papers. It is the **argumentative map of the field that explains why the paper is necessary**.

---

## Inputs

The user may provide:

1. a complete Related Work section;
2. related-work paragraphs embedded in the Introduction;
3. a paper draft containing Abstract, Introduction, Method, and Experiments;
4. several reference papers for comparison;
5. a planned related-work outline;
6. only a paper aim and contribution statement.

When available, inspect the whole paper—not only the Related Work section—because the review must check alignment with the paper's aim, method, and experiments.

---

## Recommended Related Work Structures

### Pattern A: Claim-Centred Structure

Use when the paper has several distinct claims.

1. Prior work on capability or claim 1.
2. Prior work on capability or claim 2.
3. Prior work on capability or claim 3.
4. Closest work and direct distinction.
5. Positioning paragraph linking all gaps to the proposed method.

Example categories:

- action generation;
- physical grounding;
- execution verification;
- failure recovery.

### Pattern B: Bottleneck-Centred Structure

Use when the method addresses multiple technical bottlenecks.

1. Bottleneck 1 and existing solutions.
2. Bottleneck 2 and existing solutions.
3. Bottleneck 3 and existing solutions.
4. Why solving the bottlenecks independently is insufficient.
5. How the proposed work connects them.

Example bottlenecks:

- perception under occlusion;
- contact-aware control;
- sample efficiency;
- sim-to-real transfer;
- long-horizon error accumulation.

### Pattern C: Competing-Paradigm Structure

Use when the paper compares methodological families.

1. Classical planning/control.
2. Imitation learning or reinforcement learning.
3. Foundation-model or VLM/VLA methods.
4. Hybrid or structured methods.
5. Positioning of the proposed approach.

For each family, state:

- what it does well;
- what assumptions it makes;
- where it fails in the target regime;
- what remains unresolved.

### Pattern D: Method-Factorization Structure

Use when the experiments systematically compare design choices.

1. Prior work for component or phase A.
2. Prior work for component or phase B.
3. Alternative mechanism 1.
4. Alternative mechanism 2.
5. Missing systematic comparison.
6. Experimental factorization derived from the literature.

This is especially useful when the paper compares combinations such as:

- learned vs analytical alignment;
- open-loop vs closed-loop interaction;
- retrieval vs behavioural cloning;
- monolithic vs decomposed policies.

### Pattern E: System-Paper Structure

Use for real-robot systems with several enabling components.

1. Prior systems for the target task.
2. Alternative task-solving approaches.
3. Algorithms enabling real-world training or deployment.
4. Safety, data collection, reward, reset, or hardware systems.
5. Closest integrated system.
6. Why the proposed integration enables a new capability or regime.

### Pattern F: Embedded Related Work

Some journals place most related work inside the Introduction rather than under a standalone heading.

In this case, check whether the Introduction still performs the following functions:

1. establishes the dominant paradigm;
2. acknowledges its strengths;
3. identifies limitations in the paper's target regime;
4. gives a deeper diagnosis;
5. motivates the proposed design principle.

Do not penalize a paper solely for lacking a separate Related Work heading.

---

## Step-by-Step Review Procedure

## Step 1: Recover the Paper Aim

Before reviewing citations, identify:

- the main robotics problem;
- the central claim;
- the proposed method or system;
- the claimed novelty;
- the experiment groups;
- the target operating regime.

Output a one-sentence aim:

> This paper aims to show that [method/principle] enables [capability] under [specific regime], overcoming [specific limitation].

If the aim is unclear, flag this before reviewing the literature structure.

---

## Step 2: Segment the Related Work

Split the section into paragraphs or subsections.

For each unit, record:

| Unit | Research line | Main capability | Main limitation | Link to this paper |
|---|---|---|---|---|

Identify whether the section is organized by:

- chronology;
- paper names;
- task type;
- methodological family;
- claim;
- bottleneck;
- system component;
- experiment factor.

A strong section is usually organized by claim, bottleneck, paradigm, or component—not chronology alone.

---

## Step 3: Check Synthesis Quality

For each research line, check whether the paragraph follows:

> capability of prior work → assumptions or strengths → limitation in the target regime → unresolved requirement

Good synthesis:

> Model-based controllers offer geometric precision and interpretability, but their dependence on accurate task and contact models limits transfer across objects and environments. Learning-based policies reduce manual modeling, yet often require large task-specific datasets and remain brittle under distribution shift.

Weak synthesis:

> Method A uses planning. Method B uses reinforcement learning. Method C uses imitation learning.

Flag paper-by-paper listing unless a detailed closest-work comparison requires it.

---

## Step 4: Check Fairness

The section should acknowledge what prior work does well before stating limitations.

Check for:

- accurate description of assumptions;
- limitations tied to the paper's target regime;
- no straw-man comparisons;
- no implication that prior work claims more than it does;
- no broad dismissal based on one benchmark;
- no claim that "no prior work" exists without strong evidence.

Prefer:

> Existing methods typically focus on...

over:

> No previous method can...

unless the latter is rigorously supported.

---

## Step 5: Check the Root-Cause Diagnosis

A strong Related Work section goes beyond performance differences.

Look for deeper causes such as:

- implicit rather than explicit physical knowledge;
- lack of 3D grounding;
- absence of closed-loop correction;
- mismatch between training and deployment distributions;
- monolithic policies having to infer task structure from data;
- missing multimodal information;
- final-state evaluation that ignores execution history;
- isolated modules without system-level coordination.

Ask:

> Does the literature review explain why the proposed method is the right response, rather than merely a different response?

---

## Step 6: Check Closest-Work Positioning

Identify the one to three most similar papers.

Compare them along dimensions relevant to the contribution:

| Dimension | Prior work | Current paper |
|---|---|---|
| Task scope |  |  |
| Inputs |  |  |
| Outputs |  |  |
| Supervision |  |  |
| Representation |  |  |
| Feedback |  |  |
| Assumptions |  |  |
| Deployment setting |  |  |
| Generalization |  |  |
| Evaluation |  |  |

The distinction should be concrete.

Weak:

> Unlike previous work, our method is more robust and general.

Better:

> Prior systems use endpoint success classifiers after policy execution, whereas our method maintains task-state predicates throughout execution and uses them to select corrective actions.

Use generic examples only when reviewing public/reusable materials.

---

## Step 7: Check Correspondence to the Method

Create a gap-to-method table:

| Related-work gap | Proposed component | Is the connection explicit? |
|---|---|---|
|  |  |  |

Every major method component should have a reason to exist.

Flag:

- components not motivated by the literature;
- gaps that the method does not address;
- method claims that appear only after Related Work;
- excessive literature discussion unrelated to the method.

---

## Step 8: Check Correspondence to Experiments

Create a literature-to-experiment table:

| Literature contrast | Required baseline or ablation | Present? |
|---|---|---|
|  |  |  |

Examples:

- monolithic vs structured policies → decomposition ablation;
- learned vs analytical geometry → grounding comparison;
- vision-only vs visual-tactile → modality ablation;
- offline vs online imitation → training-strategy comparison;
- open-loop vs closed-loop control → perturbation or recovery evaluation.

The Related Work section should help the reader anticipate the experiment design.

Flag cases where:

- the section criticizes a method family but does not compare against it;
- the paper claims a missing capability but does not measure it;
- the closest work is discussed but absent from experiments without explanation;
- baselines test implementation differences rather than the claimed scientific gap.

---

## Step 9: Check Section Proportion and Scope

A good Related Work section is selective.

Check whether it:

- covers all literature needed to support the claims;
- avoids unrelated background;
- gives more space to the closest work;
- keeps broad families concise;
- separates background knowledge from direct competition;
- does not become a mini-survey unless the paper requires one.

Flag both:

- **undercoverage**: missing the closest methods or key research line;
- **overcoverage**: many citations that do not affect positioning or evaluation.

---

## Step 10: Check the Closing Positioning Paragraph

The section should end with a precise statement of what remains unresolved.

Recommended structure:

> Existing studies address [capability A], [capability B], and [capability C], but typically treat them independently or evaluate them outside [target regime]. The present work investigates/proposes [specific contribution], which connects [mechanisms] and evaluates them under [scope].

The closing paragraph should:

- synthesize, not repeat;
- define scope;
- avoid inflated novelty;
- lead naturally into the Method or paper overview.

---

## Evaluation Rubric

Score each dimension from 1 to 5.

| Dimension | 1 | 3 | 5 |
|---|---|---|---|
| Alignment with paper aim | Literature appears detached | Mostly relevant | Every research line supports a claim or design requirement |
| Organization | Paper list or chronology | Some thematic grouping | Clear claim/bottleneck/paradigm structure |
| Synthesis | Mostly summaries | Some comparison | Strengths, assumptions, limitations, and gaps are synthesized |
| Fairness | Straw-man or unsupported | Mostly balanced | Accurate, scoped, and fair |
| Root-cause diagnosis | Missing | Implied | Explicit explanation of why limitations arise |
| Closest-work positioning | Vague or missing | Partial distinction | Direct multidimensional comparison |
| Gap-to-method correspondence | Weak | Mostly aligned | Each component answers a literature-derived requirement |
| Gap-to-experiment correspondence | Missing | Partial | Baselines and ablations directly follow literature contrasts |
| Scope and selectivity | Important omissions or excess | Acceptable | Complete but focused |
| Closing positioning | Generic | Understandable | Precise, scoped, and memorable |

Provide:

- total score out of 50;
- main strengths;
- main weaknesses;
- three highest-priority revisions.

---

## Required Output Format

### 1. High-Level Verdict

State whether the section supports the paper's overall aim.

### 2. Paper Aim and Claims

Summarize:

- paper aim;
- central claim;
- major method components;
- main experiment groups.

### 3. Structure Map

| Paragraph/Subsection | Research line | Function | Link to paper aim | Assessment |
|---|---|---|---|---|

### 4. Research-Line Diagnosis

For each research line, discuss:

- what is synthesized well;
- what assumptions or strengths are acknowledged;
- whether the limitation is precise;
- whether the unresolved gap is clear.

### 5. Correspondence Audit

#### Gap to Method

| Gap | Method response | Alignment |
|---|---|---|

#### Gap to Experiment

| Literature contrast | Experimental test | Alignment |
|---|---|---|

### 6. Closest-Work Comparison

Provide a concise multidimensional comparison with the closest papers.

### 7. Scores

Use the 10-dimension rubric.

### 8. Recommended Revised Structure

Propose a new subsection or paragraph sequence.

### 9. Concrete Rewrite Suggestions

Give targeted rewrites for:

- opening sentence of each research line;
- synthesis sentence;
- limitation sentence;
- transition sentence;
- final positioning paragraph.

Do not rewrite the entire section unless the user asks.

---

## Common Problems and Fixes

### Problem 1: Paper-by-Paper Listing

Weak:

> Smith et al. proposed X. Lee et al. proposed Y. Chen et al. proposed Z.

Better:

> Existing approaches fall into two groups. Geometry-based methods provide precise spatial constraints but depend on task-specific models, whereas learned policies reduce manual modeling but require broader data coverage and often lack explicit feasibility checks.

### Problem 2: Generic Limitations

Weak:

> These methods are not robust in the real world.

Better:

> These methods rely on accurate object poses and fixed contact models, causing performance to degrade under occlusion, grasp variation, and unmodeled compliance.

### Problem 3: Unfair Positioning

Weak:

> Previous methods cannot generalize.

Better:

> Previous methods demonstrate generalization across object poses, but their evaluation does not address transfer across object categories or changes in interaction dynamics.

### Problem 4: Gap Does Not Motivate the Method

Weak:

> Existing methods require large datasets. We propose a new architecture with three modules.

Better:

> Because monolithic policies must learn both task structure and control from limited data, we separate invariant geometric alignment from task-specific interaction and assign each phase an appropriate mechanism.

### Problem 5: No Experimental Consequence

Weak:

> Existing methods lack explicit grounding.

Better:

> This distinction motivates comparisons between image-only prompting, local spatial cues, and explicit object-centric 3D grounding, together with ablations of the grounding component.

### Problem 6: Inflated Novelty

Weak:

> We are the first to solve general manipulation.

Better:

> We focus on a previously underexplored setting in which [specific capability] must operate under [specific assumptions and evaluation regime].

### Problem 7: Closest Work Hidden in a Long Survey

Fix:

- summarize broad families first;
- identify the closest work explicitly;
- compare it along assumptions, mechanisms, and evaluation;
- explain why the distinction matters to the main claim.

---

## Writing Templates

### Research-Line Opening

> A first line of work addresses [capability] through [method family].

### Strength-to-Limitation Transition

> These methods provide [strength], but their reliance on [assumption] limits their use in [target regime].

### Deeper Diagnosis

> This limitation arises because [root cause], rather than solely from insufficient model capacity or training data.

### Gap Statement

> Consequently, existing systems do not yet provide [precise missing capability].

### Closest-Work Positioning

> The most closely related approach is [method], which shares [commonality]. However, it differs in [assumption/mechanism/evaluation], whereas the present work focuses on [specific distinction].

### Final Positioning Paragraph

> Taken together, prior studies have advanced [A], [B], and [C], but these capabilities are typically developed or evaluated independently. Our work connects them through [principle or framework] and evaluates whether this integration improves [specific outcome] under [target regime].

---

## Anti-Fabrication Rules

The reviewing agent must not:

- invent citations;
- invent claims attributed to papers;
- infer experimental settings not stated in the source;
- claim a method is the first without evidence;
- fabricate missing baselines or quantitative results;
- replace missing evidence with general knowledge;
- treat all papers in a category as making identical assumptions.

When source material is incomplete, say:

> The provided text does not contain enough information to verify this distinction.

When proposing additional literature categories, label them as suggestions rather than established omissions unless verified.

---

## Privacy and Reusability

This skill is intended for public reuse.

- Use only generic robotics examples or details from public papers.
- Do not include unpublished project details.
- Do not include private task names, internal datasets, repository paths, experimental results, or identifying information.
- When adapting the skill for a private project, keep project-specific examples outside the reusable skill file.
