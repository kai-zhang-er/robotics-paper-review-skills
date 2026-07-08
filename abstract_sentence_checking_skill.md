# Robotics Abstract Sentence-Checking Skill

## Purpose
Use this skill to review, diagnose, and improve abstracts for robotics scientific papers, especially papers targeting venues such as Science Robotics, Nature Machine Intelligence, T-RO, IJRR, RSS, CoRL, ICRA, and IROS.

The skill checks whether an abstract has a clear sentence-level logic:

**Problem → Gap → Core insight → Method → Technical mechanism → Experiments → Results → Broader implication**

It is especially suitable for papers on robotic manipulation, embodied AI, VLA/VLM robotics, tool use, mobile manipulation, navigation, dexterous manipulation, contact-rich interaction, and real-robot systems.

---

## Core Principle
A strong robotics abstract should not merely describe a method. It should make a scientific claim about a robotics capability, explain why existing approaches fail, and show how the proposed method resolves the gap through concrete experiments.

A good abstract usually contains 5–8 sentences. Each sentence should perform a distinct rhetorical function. Avoid multiple sentences doing the same job, such as spending three sentences on generic motivation or introducing method details before the gap is clear.

---

## Expected Abstract Structure

### Sentence 1 — Broad robotics problem
**Function:** Introduce the robotics capability or challenge.

A good first sentence should answer:
- What robotics problem matters?
- Why is this capability important?
- What real-world setting motivates the work?

Good patterns:
- "Robotic systems are increasingly expected to perform [capability] in [environment], where success depends on [physical/semantic/control requirement]."
- "Connecting [high-level reasoning / learned policies] to [physical/geometric/control demands] remains a fundamental challenge in robotics."
- "Achieving [dexterity / tool use / long-horizon manipulation / robust navigation] requires [specific robotics capability]."

Weak patterns:
- "Robotics is important."
- "Deep learning has achieved great success."
- "We propose a novel framework..." as the first sentence.

---

### Sentence 2 — Concrete gap or limitation
**Function:** Explain what current methods fail to handle.

A good gap sentence should identify a specific failure mode, not just say that existing methods are limited.

Good patterns:
- "Although recent [method class] can [capability], they often fail when [specific physical/geometric/temporal/generalization condition]."
- "Existing methods treat [task] as [simplified formulation], but success actually requires [missing condition]."
- "Current VLA/VLM policies can generate visually plausible actions, but they may fail to satisfy [physical validity condition]."

For robotics, prefer concrete failure modes:
- functional-part misalignment;
- unstable or invalid contact;
- poor recovery after execution errors;
- lack of physical validity checking;
- insufficient geometric grounding;
- sim-to-real mismatch;
- failure under perturbations, occlusions, or calibration error;
- long-horizon error accumulation.

Weak patterns:
- "Existing methods are not robust."
- "Previous works have many limitations."
- "This task is challenging." without specifying why.

---

### Sentence 3 — Core insight or hypothesis
**Function:** State the scientific idea behind the paper.

This sentence should bridge the gap and the method. It should not yet become a long implementation list.

Good patterns:
- "We argue that reliable [task] requires [core principle]."
- "The central insight is that [task] is not merely [simpler formulation], but requires [missing physical/semantic/control factor]."
- "Our key observation is that [structural prior / representation / feedback signal] can bridge [gap]."

Examples:
- "We argue that reliable contact-rich manipulation requires explicit reasoning about contact state, geometric constraints, and recovery."
- "The central insight is that long-horizon mobile manipulation is not merely navigation followed by grasping, but requires coordinated reasoning over reachability, object interaction, and scene changes."

Weak patterns:
- "To solve this problem, we propose..." too early without stating the underlying insight.
- "Our method is effective and efficient." without a scientific idea.

---

### Sentence 4 — Proposed method
**Function:** Introduce the method and its main contribution in one memorable sentence.

Good patterns:
- "Here, we introduce [Method Name], a [short descriptor] framework that [main mechanism]."
- "We propose [Method Name], which [core operation] to enable [target capability]."
- "Our method combines [A] with [B] to [main benefit]."

For robotics papers, the method sentence should emphasize a principle, not just a module list.

Better:
- "We introduce a constraint-aware manipulation framework that integrates subgoal-conditioned control with geometric grounding, execution monitoring, and recovery."

Weaker:
- "We build a system with a decomposer, controller, verifier, and recovery module."

---

### Sentence 5 — Technical mechanism/components
**Function:** Explain what the method actually does technically.

This sentence distinguishes the work from a high-level idea. Include robotics-specific physical constraints where possible.

Good patterns:
- "The framework [localizes/represents/predicts/optimizes/verifies] [technical object] and uses [mechanism] to [effect]."
- "Specifically, it [component 1], [component 2], and [component 3]."
- "The method grounds [semantic instruction] into [geometric/physical representation], enabling [control or verification]."

Useful robotics-specific technical terms may include:
- object-centric spatial representation;
- contact state or contact mode;
- functional affordance;
- geometric constraint;
- reachability or collision constraint;
- force/torque feedback;
- visual-tactile feedback;
- task-specific success condition;
- execution monitor and recovery policy;
- subgoal-conditioned policy;
- sim-to-real adaptation.

Weak patterns:
- Excessive detail about sensors, software, or implementation unless central to the contribution.
- Vague terms such as "reasoning module" without saying what it outputs.

---

### Sentence 6 — Experiments/evaluation setup
**Function:** Show how the claim is tested.

A good experiment sentence should include:
- task types;
- robot platform or simulation/real-world setup, if important;
- variations/perturbations;
- baselines or evaluation scope.

Good patterns:
- "We evaluate [method] on [tasks] using [platform/setup] under variations in [object pose, tool pose, target layout, perturbations]."
- "Experiments across [N] tasks, [N] objects, and [N] real-world trials test [claim]."
- "We compare against [baseline classes] in [simulation/real-world] settings."

Science Robotics-style abstracts often emphasize scale:
- number of real-world rollouts;
- number of tasks;
- number of object instances;
- number of unseen configurations;
- amount of real-world training time;
- success rate across realistic settings.

Weak patterns:
- "Experiments demonstrate the effectiveness of our method." without saying what experiments.

---

### Sentence 7 — Main result
**Function:** Provide evidence.

Use quantitative results whenever possible.

Good patterns with numbers:
- "Compared with [baseline], our method improves task success from [X]% to [Y]%, reduces [failure metric] by [Z]%, and [additional effect]."
- "Across [N] real-world trials, [method] achieves [X]% success and outperforms [baseline] by [Y] points."

Good pattern without final numbers:
- "Results show that [method] substantially reduces [specific failure] compared with [baseline], especially under [difficult condition]."

For robotics papers, good result metrics include:
- task success rate;
- alignment error;
- insertion depth error;
- contact-state correctness;
- reading stability;
- recovery success rate;
- number of recovery attempts;
- completion time;
- safety violations;
- real-world transfer success.

Weak patterns:
- "The results are promising."
- "The proposed method performs better." without metrics or specific failure reduction.

---

### Sentence 8 — Broader implication / scientific takeaway
**Function:** End with what the paper teaches beyond the specific implementation.

Good patterns:
- "These results suggest that [broader principle] is important for [robotics capability]."
- "Our findings indicate that [community assumption] should be revised toward [new perspective]."
- "This work provides a step toward [broader robotics goal]."

For embodied AI or robot learning papers:
- "These findings suggest that reliable robot learning requires moving beyond visually plausible task completion toward explicit reasoning about physical constraints and execution validity."

Weak patterns:
- "Future work will improve the system."
- "This method has broad applications." without a clear takeaway.

---

## Science Robotics-Specific Expectations
Science Robotics abstracts usually follow the general structure above but often add three features:

1. **Real-world scale**
   - Mention real-world trials, tasks, objects, rollouts, or training time.
   - Avoid sounding like a purely conceptual or toy demonstration.

2. **Method as a principle**
   - Frame the contribution as a reusable robotics principle, such as decomposition, semantic-to-geometric grounding, human-in-the-loop RL, or physical validity reasoning.
   - Do not present the work as only adding a module.

3. **Explicit scientific takeaway**
   - End by saying what the experiments reveal about robotics, not just that the method works.

---

## Diagnostic Checklist
When reviewing an abstract, answer the following questions:

1. Does the first sentence define a robotics problem rather than a generic AI trend?
2. Does the second sentence identify a concrete gap or failure mode?
3. Is there a clear core insight or hypothesis before the method is introduced?
4. Is the proposed method described in one memorable sentence?
5. Are the technical components specific enough to distinguish the work?
6. Does the experiment sentence state tasks, setup, and variations?
7. Are the main results quantitative or at least specific?
8. Does the final sentence provide a broader scientific takeaway?
9. Are there redundant sentences doing the same rhetorical job?
10. Are there vague words such as "robust," "effective," "complex," or "intelligent" that should be replaced by concrete robotics terms?
11. Does the abstract avoid overclaiming?
12. Does the abstract make clear why this is a robotics problem, not just an AI model problem?

---

## Output Format for Abstract Checking
When asked to check an abstract, return the following structure.

### 1. Overall verdict
Give a concise judgment:
- Strong / Mostly strong / Needs revision / Weak
- One-sentence reason

### 2. Sentence-by-sentence diagnosis
Use a table:

| Sentence | Current role | Fits expected role? | Diagnosis | Suggested revision |
|---|---|---|---|---|

For "Current role," choose one of:
- Broad problem
- Gap
- Core insight
- Method
- Technical mechanism
- Experiments
- Results
- Broader implication
- Redundant / unclear

### 3. Missing elements
List missing or weak elements:
- unclear gap;
- no scientific insight;
- method introduced too early;
- insufficient technical specificity;
- no quantitative result;
- weak broader implication;
- overclaiming;
- not robotics-specific enough.

### 4. Revised abstract
Provide a revised version preserving the author’s intended contribution, ideally 5–8 sentences.

### 5. One-line takeaway
State the core paper claim in one sentence.

---

## Revision Rules
When rewriting:

1. Preserve the technical meaning. Do not invent results or claims.
2. If numbers are missing, use placeholders such as [X]%, [N] trials, or [Y] improvement.
3. Replace vague adjectives with measurable robotics terms.
4. Keep the abstract focused on one main claim.
5. Do not overstate generalization beyond the experiments.
6. Prefer active, concrete phrasing.
7. Make the final sentence an implication, not a future-work statement.

---

## Example: Generic Robotics Abstract Skeleton

Robotic systems are increasingly expected to perform long-horizon manipulation tasks in unstructured environments, where success depends on both high-level task understanding and physically valid execution. Existing learned policies can often generate plausible actions, but they may fail when small geometric errors, contact changes, or accumulated execution drift violate task-specific constraints. We argue that reliable robot manipulation requires coupling learned action generation with explicit reasoning about physical constraints, execution state, and recovery. We propose [Method Name], a [short descriptor] framework that grounds language or task instructions into structured subgoals and constraint-aware control objectives. Specifically, the framework represents [key representation], monitors [task-specific execution condition], and triggers [correction/recovery mechanism] when the robot deviates from the valid execution region. We evaluate the method on [N] tasks using [simulation/real robot platform] under variations in [object pose, environment layout, perturbations, or unseen instances]. Results show that the proposed method improves [primary metric] from [X]% to [Y]% and reduces [specific failure mode] compared with [baseline]. These findings suggest that robust robotic behavior requires integrating learned policies with explicit physical grounding and execution-time validation.

---

## Example Prompt for Codex or an Agent

Use the Robotics Abstract Sentence-Checking Skill to review the following abstract. Diagnose each sentence according to the expected roles: problem, gap, insight, method, mechanism, experiments, results, and implication. Identify missing roles, redundancy, vague claims, overclaiming, and lack of robotics specificity. Then rewrite the abstract in 5–8 sentences while preserving the original technical claims and using placeholders for missing quantitative results.

<Abstract here>
