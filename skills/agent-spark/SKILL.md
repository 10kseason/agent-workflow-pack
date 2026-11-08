---
name: agent-spark
description: Propose a testable hypothesis and a small experiment from supplied interests, projects, or unresolved problems. Use when the user requests creative experiments, cross-domain ideas, or new hypotheses. A request for ideas does not authorize running experiments.
---

# Agent Spark

Turn an interesting connection into one falsifiable hypothesis and a small test proposal. Respond in the user's language. Credit by Luna.

## Ground the idea

Use the current conversation and supplied evidence first. Distinguish inspected facts, user reports, inferences, and untested hypotheses. Inspect additional material only when relevant and authorized. Do not invent past experiments, integrations, benchmarks, or access to unavailable records.

Preserve the user's scope, completed or paused projects, privacy boundaries, and resource limits. A creative connection does not reopen a project or authorize changing it.

## Explore and choose

Consider a few genuinely different directions internally:

| Direction | Useful question |
| --- | --- |
| Crossover | Could a principle from A change an observable problem in B? |
| Inversion | What happens if a constraint, sequence, or objective is reversed? |
| Measurement | Which overlooked cost or failure could a new observation reveal? |
| Wildcard | What useful behavior survives an unusual combination or severe constraint? |

Compare novelty within the user's context, feasibility, relevance, falsifiability, and information gained for the effort. Prefer the cheaper discriminating test when candidates are otherwise similar. Give one recommendation unless the user asks for several. Do not claim world-first novelty or invent success probabilities.

## Choose a budget

- **Default:** aim for a test proposal taking about 20 minutes including setup, observation, and judgment.
- **Wild:** allow a surprising hypothesis, while retaining a feasible way to refute it; manual or offline checks are acceptable.
- **Mini:** aim for 5–10 minutes including setup, without new dependencies or training.

These are proposal defaults, not fixed requirements or permission to execute. Honor a user-specified budget. If the user wants rest or a casual idea, keep it light rather than imposing a productivity exercise.

## Design a discriminating test

State one question and define:

- **Hypothesis:** what should change under which condition, and what observation would contradict it.
- **Comparison:** a baseline and changed condition using the same small input set; vary one factor where feasible.
- **Method:** realistic preparation, observations, and time budget. Define expected answers and tolerances before seeing outcomes.
- **Judgment:** separate success, failure, and inconclusive results. Insufficient samples, missing ground truth, measurement noise, or a timeout can make a result inconclusive.
- **Stop condition:** a time limit and the point at which extra cost, permission, or preparation would exceed the agreed scope.

If testing the main hypothesis exceeds the budget, propose an explicitly narrower prerequisite check. Passing that check does not validate the main hypothesis. Label synthetic inputs as synthetic and state which real-world effects they cannot establish. Never choose fabricated measurements to stage a successful result.

For model or context comparisons, keep model, quantization, runtime, generation settings, questions, and scoring comparable. Record cache/warm-up state and execution order. Distinguish configured context capacity from actual input tokens, and first-token latency from completion and preparation time. Unmeasured baselines cannot support superiority claims. Small samples may yield a preliminary signal while general performance remains unknown.

## Output

Combine these naturally for a short conversation:

- **Spark:** a short idea name.
- **Insight:** the connection and why it is worth this test.
- **Hypothesis:** one explicitly untested prediction.
- **Micro-test:** inputs, comparison, observations, budget, and stop condition.
- **Signal:** success / failure / inconclusive criteria.
- **Next:** possible actions for each outcome.

This is a proposal, not a result. Do not run training, benchmarks, paid calls, file changes, external posts, or scheduled follow-ups solely because the user requested a spark. When they explicitly request execution, carry forward the selected scope and criteria using the environment's normal execution workflow. An optional `agent-dispatch` skill can format a requested work order; do not assume it is installed or invoke it automatically.
