# Agent Workflow Pack

**근거를 연결하고, 가설을 세우고, 검증 가능한 작업 주문서로 정리합니다.**

Credit by Luna

[English](README.md) · [사용 예제](examples/workflow.md) · [검증 사례](docs/validation.md)

흩어진 맥락에서 다음 작업을 정리하는 세 가지 Agent Skill입니다. 확인된 사실, 시험해 볼 가설, 실제 허용된 행동을 구분합니다.

| 스킬 | 용도 | 결과 |
| --- | --- | --- |
| `agent-connection` | 프로젝트·문서·코드·결정 사이의 관계 검토 | 출처와 근거 수준, 누락된 확인 사항을 포함한 연결 지도 |
| `agent-spark` | 새로운 가설과 작은 실험 발굴 | 비교 기준·성공/실패/판단 불가 기준·중단 조건이 있는 제안 |
| `agent-dispatch` | 선택한 과제를 다른 에이전트가 수행할 주문서로 정리 | 작업 범위·수용 기준·권한 경계가 명확한 지시서 |

각 스킬을 독립적으로 사용할 수 있습니다. `Connection → Spark → Dispatch`는 필요할 때 명시적으로 요청하는 흐름이며, 자동 실행 파이프라인은 아닙니다.

## 사용 예시

```text
$agent-connection 이 두 설계 메모의 공통 구조와 충돌을 찾아줘.
직접 확인한 내용과 추론을 구분하고, 빠진 근거도 알려줘.
```

```text
$agent-spark 미니 모드로 이 문제를 살펴볼 작은 실험 하나를 제안해줘.
비교 기준과 판단 불가 조건도 넣어줘. 지금 실행하지는 마.
```

```text
$agent-dispatch 선택한 아이디어를 조사 전용 작업 주문서로 정리해줘.
확인할 사항과 완료 기준을 넣고, 구현은 범위에서 제외해줘.
```

스킬 본문은 영문이며, 결과는 사용자의 언어로 작성하도록 안내합니다. [전체 예제](examples/workflow.md)의 자료와 결과는 모두 가상입니다.

## Codex 프로젝트에 설치

저장소를 내려받거나 복제합니다.

```bash
git clone https://github.com/10kseason/agent-workflow-pack.git
```

`skills/` 안에서 필요한 스킬 폴더를 대상 프로젝트의 `.agents/skills/`로 복사합니다. `SKILL.md`와 `agents/openai.yaml`을 함께 복사하고, 같은 이름의 기존 폴더가 있다면 내용을 먼저 비교합니다.

```text
your-project/.agents/skills/
├── agent-connection/
├── agent-spark/
└── agent-dispatch/
```

대상 프로젝트에서 새 Codex 세션을 열고 `$agent-connection`, `$agent-spark`, `$agent-dispatch`로 호출합니다. 요청에 맞는 일반적인 자동 선택도 허용하며, 명시 호출 전용 설정을 추가하지 않았습니다.

다른 에이전트의 설치 위치와 UI 메타데이터 지원은 다를 수 있습니다. 이번 배포는 여러 에이전트 환경에서의 실행 호환성을 검증했다는 뜻이 아닙니다.

## 동작 범위와 개인정보

이 패키지는 지침 파일로 구성됩니다. 실행 도구, API 클라이언트, 원격 수집, 인증 정보, 기억 데이터베이스, 백그라운드 서비스를 포함하지 않습니다. 패키지 자체에 필요한 API 키나 추가 의존성도 없습니다.

실제 도구와 데이터 접근은 호스트 에이전트가 담당합니다. 스킬 지침은 행동 가이드이며 강제되는 샌드박스가 아닙니다. 제공 자료와 호스트 권한을 확인해야 합니다. 스킬은 관련 있고 허용된 근거를 사용하고, 제안·작성 요청을 실행·게시 권한으로 확대하지 않도록 안내합니다.

개인 대화, 개인 경로, 실제 프로젝트 기록, 생성된 캐시는 배포에 포함하지 않습니다. 기억 자동 저장이나 외부 전송도 시작하지 않습니다.

정확성, 모델 성능 향상, 모든 지침의 준수를 보장하지는 않습니다. 파일 구조와 메타데이터 검증은 실제 에이전트 행동 검증과 다릅니다. [검증 사례](docs/validation.md)를 이용해 자신의 환경에서 확인할 수 있습니다.

## 크레딧과 라이선스

**Credit by Luna**

관리: [10kseason](https://github.com/10kseason). Luna Connection, Luna Spark, Luna Dispatch의 흐름을 범용 이름과 가상 사례로 정리한 공개용 패키지입니다.

[Apache License 2.0](LICENSE) · [NOTICE](NOTICE)
