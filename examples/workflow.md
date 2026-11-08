# A small workflow, from evidence to a work order

All project names, paths, inputs, and outputs below are synthetic illustrations. They are not records of an executed experiment or a benchmark.

## Supplied material

Assume the user supplies these two notes:

```text
Note A: document-preview
The design note describes a preview cache keyed by document ID.
No implementation or measurements are supplied.

Note B: thumbnail-gallery
The design note describes a cache key containing item ID and a version marker.
No implementation or measurements are supplied.
```

## 1. Connection

Request:

```text
Use $agent-connection to compare these notes. Do they establish that the
projects share an implementation? What reuse opportunity is worth checking?
```

Illustrative answer:

| Claim | Evidence level | Basis |
| --- | --- | --- |
| Both notes describe caches | Verified about the documents | Notes A and B |
| The projects could share an invalidation design | Inferred | Both need a way to identify reusable cached output |
| Both implementations use the described keys | Unknown | No source code was supplied |
| The projects share cache code | Unknown | Shared terminology does not establish shared code |

Next check: inspect each current key construction and invalidation path before proposing implementation reuse. Do not invent source filenames.

## 2. Spark

Request:

```text
Use $agent-spark in mini mode. Propose an offline check for the risk of using
only an item ID as a cache key. Do not modify either project or execute a test.
```

Illustrative proposal:

- **Question:** can a model of an ID-only cache return an outdated value after the same ID's content changes?
- **Hypothesis:** in a model with no separate invalidation, adding a version marker to the key prevents that specific collision.
- **Inputs:** one synthetic item, two content versions, and one repeated unchanged lookup.
- **Comparison:** use the same inputs with an ID-only key and an ID-plus-version key. Hold all other modeled behavior constant.
- **Method:** trace the lookups manually, including the lookup after the version changes. Budget: 5–10 minutes.
- **Success:** the model exposes the outdated ID-only lookup and separates the changed version while still reusing the unchanged one.
- **Failure:** the proposed key still collides for those distinct versions or fails to reuse the unchanged version in the model.
- **Inconclusive:** version identity or lookup behavior is insufficiently specified.
- **Stop:** stop at ten minutes or when real project access is needed.

This only examines the specified synthetic cache model. A separate invalidation mechanism could make a real ID-only cache correct. The check cannot establish a real bug, a speedup, or either project's current behavior. No outcome has been observed here.

## 3. Dispatch

Request:

```text
Use $agent-dispatch to write a follow-up investigation order. Source reading
is authorized for the two projects I will supply. No edits or uploads.
```

Illustrative work order:

> **Goal:** determine how the two supplied projects prevent outdated cache results.
>
> **Known context:** the supplied design notes describe different key schemes. Current implementation and performance are unverified. The synthetic test above is only a proposal.
>
> **Scope:** inspect key construction, invalidation, and existing relevant test evidence in the supplied projects. Do not change files, run training, upload source, or publish findings.
>
> **Guidance:** establish the current revision, locate the relevant code without assuming filenames, and trace changed-item and unchanged-item behavior. Treat missing access as an evidence gap.
>
> **Acceptance:** report source-backed behavior for each project; separate document claims from implementation findings; identify whether a concrete failure is established or remains hypothetical; suggest the smallest follow-up validation where needed.
>
> **Stop:** pause dependent investigation if a necessary project is unavailable or the task would require new permissions. Report available evidence without inventing the missing part.
>
> **Report:** findings, source references, unverified assumptions, and a scoped next action. Implementation requires a separate request.

## Korean invocation

```text
$agent-dispatch 위 자료를 바탕으로 두 프로젝트의 캐시 무효화 방식을
조사하는 주문서만 작성해줘. 제공할 소스 읽기만 허용하고,
파일 수정이나 외부 업로드는 제외해줘.
```

The skills should preserve the same evidence and permission boundaries regardless of the response language.
