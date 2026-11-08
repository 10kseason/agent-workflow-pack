# Agent Workflow Pack

**Connect evidence. Shape a hypothesis. Write a verifiable work order.**

Credit by Luna

[한국어 안내](README.ko.md) · [Worked example](examples/workflow.md) · [Validation cases](docs/validation.md)

Three independently usable Agent Skills for moving from scattered context to a clear next task. They help an agent separate what is known, what is worth testing, and what is actually authorized.

| Skill | Use it when you want… | Result |
| --- | --- | --- |
| `agent-connection` | Relationships among supplied projects, notes, code, or decisions | A small map with sources, evidence levels, and missing checks |
| `agent-spark` | A new hypothesis or creative experiment | One test proposal with a baseline, outcome criteria, and a stop condition |
| `agent-dispatch` | A selected idea turned into an agent brief | A self-contained work order with scope and acceptance criteria |

Use one skill or explicitly request a sequence. Connection → Spark → Dispatch is an optional workflow, not an automatic execution pipeline. Each skill works without its siblings.

## Quick examples

```text
Use $agent-connection to compare these two design notes. Which relationships
are directly supported, which are inferred, and what evidence is missing?
```

```text
Use $agent-spark in mini mode to propose one small experiment for this
unresolved problem. Include a baseline and an inconclusive outcome.
```

```text
Use $agent-dispatch to turn the selected idea into an investigation-only
work order. Include acceptance criteria; implementation is out of scope.
```

The instructions are written in English and direct the agent to answer in the user's language. See the [worked example](examples/workflow.md) for a synthetic input, a sample result, and a Korean invocation.

## Install in a Codex project

Download this repository or clone it:

```bash
git clone https://github.com/10kseason/agent-workflow-pack.git
```

Copy the desired folders from `skills/` into your target project's `.agents/skills/`. Copy the complete folder, including `agents/openai.yaml`. Inspect any existing same-named folder before replacing it.

```text
your-project/
└── .agents/
    └── skills/
        ├── agent-connection/
        │   ├── SKILL.md
        │   └── agents/openai.yaml
        ├── agent-spark/
        │   ├── SKILL.md
        │   └── agents/openai.yaml
        └── agent-dispatch/
            ├── SKILL.md
            └── agents/openai.yaml
```

Start a new Codex session in the target project and explicitly invoke a skill with `$agent-connection`, `$agent-spark`, or `$agent-dispatch`. Each description also supports normal discovery for relevant requests; this pack does not disable implicit invocation.

Other agents may support the same skill format, but their installation and UI metadata handling vary. This release does not claim cross-agent runtime compatibility testing.

## Scope and privacy

This is an instruction-only pack. It ships no executable helpers, API clients, telemetry, credentials, memory database, or background service. It needs no pack-specific API key or dependency installation.

The host agent still controls tools and data access. Skill instructions are behavioral guidance, not an enforced sandbox. Review the host's permissions and the material you provide. The skills direct the agent to use relevant authorized sources, keep evidence levels distinct, and avoid expanding a proposal into execution or publication.

Repository examples are synthetic. Private chats, personal paths, project records, and generated caches are not included. The installed skills do not automatically save memory or post work orders elsewhere.

## What to expect

- Connection labels claims as verified, user-reported, inferred, or unknown.
- Spark separates a proposed experiment from a completed result and a prerequisite check from proof of the main hypothesis.
- Dispatch preserves the difference between investigation, implementation, and publication permissions.

The pack cannot guarantee factual accuracy, improved model performance, or obedience to every boundary. Structure and metadata checks do not prove real-world agent behavior. The [validation guide](docs/validation.md) includes scenarios for evaluating those boundaries in your own environment.

## Credit and license

**Credit by Luna**

Maintained by [10kseason](https://github.com/10kseason). Adapted from the Luna Connection, Luna Spark, and Luna Dispatch workflows, with generic examples and portable skill names.

[Apache License 2.0](LICENSE). See [NOTICE](NOTICE) for attribution.
