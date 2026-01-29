# conners-market

> **Built with Claude Code** — `ai-ml-toolkit` 플러그인(by Daniel Avila)의 5개 에이전트를
> **하나의 스킬 커맨드**로 재설계한 Claude Code 플러그인입니다.

```
ai-ml-toolkit (agents)          →    ai-ml-skill (skill)
┌─────────────────────────┐          ┌──────────────────────────┐
│  ai-engineer agent      │          │                          │
│  ml-engineer agent      │   ──→    │  /ai-ml-skill <domain>   │
│  nlp-engineer agent     │          │                          │
│  cv-engineer agent      │          │  단일 커맨드로 도메인    │
│  mlops-engineer agent   │          │  자동 감지 & 전문가 적용 │
└─────────────────────────┘          └──────────────────────────┘
```

## What Changed

| | ai-ml-toolkit (원본) | ai-ml-skill (스킬) |
|---|---|---|
| **구조** | 5개 개별 에이전트 | 1개 통합 스킬 커맨드 |
| **호출** | Task 에이전트 선택 | `/ai-ml-skill rag ...` |
| **도메인 선택** | 수동 에이전트 지정 | 키워드 기반 자동 감지 |
| **도구** | Read, Write, Edit, Bash | + WebSearch, WebFetch, Grep, Glob, Task |
| **출처** | davila7/claude-code-templates | hjp7461/conners-market |

## 지원 도메인

| 키워드 | 전문 분야 |
|---|---|
| `rag`, `llm`, `ai`, `embedding`, `vector`, `prompt`, `agent` | AI Engineer (LLM/RAG) |
| `ml`, `model`, `serving`, `pipeline`, `feature`, `inference` | ML Engineer |
| `nlp`, `text`, `sentiment`, `ner`, `classification`, `language` | NLP Engineer |
| `cv`, `vision`, `image`, `detection`, `ocr`, `face`, `video` | Computer Vision Engineer |
| `mlops`, `infra`, `deploy`, `registry`, `experiment`, `retraining` | MLOps Engineer |
| *(키워드 없음)* | General AI/ML Engineer (전체 도메인 통합) |

## 설치

```bash
# 1. 마켓플레이스 등록 (최초 1회)
/plugin marketplace add hjp7461/conners-market

# 2. 플러그인 설치
/plugin install ai-ml-skill@conners-market
```

## 사용법

```bash
# RAG 시스템 구축
/ai-ml-skill rag PDF 문서 기반 RAG 파이프라인 구현

# ML 모델 서빙
/ai-ml-skill ml ONNX 모델 서빙 API 구축

# NLP 텍스트 분류
/ai-ml-skill nlp 고객 리뷰 감성 분석 파이프라인

# 컴퓨터 비전
/ai-ml-skill cv YOLOv8 기반 실시간 객체 탐지

# MLOps 인프라
/ai-ml-skill mlops MLflow 실험 추적 + SageMaker 배포 파이프라인

# 도메인 자동 감지 (키워드 없이)
/ai-ml-skill 추천 시스템 설계해줘
```

## 디렉토리 구조

```
conners-market/
├── .claude-plugin/
│   └── marketplace.json          ← 마켓플레이스 메타데이터
├── plugins/
│   └── ai-ml-skill/
│       ├── .claude-plugin/
│       │   └── plugin.json       ← 플러그인 메타데이터
│       └── commands/
│           └── ai-ml-skill.md    ← 스킬 커맨드 정의
├── .gitignore
└── README.md
```

## 플러그인 추가 방법

새로운 스킬을 이 마켓플레이스에 추가하려면:

1. `plugins/<skill-name>/` 디렉토리 생성
2. `.claude-plugin/plugin.json` 및 `commands/<skill-name>.md` 작성
3. `.claude-plugin/marketplace.json`의 `plugins` 배열에 항목 추가
4. 커밋 & 푸시 → 사용자는 `/plugin update`로 반영

## Credits

- 원본: [davila7/claude-code-templates](https://github.com/davila7/claude-code-templates) — `ai-ml-toolkit` 플러그인 (MIT License)
- 스킬 변환 및 재설계: [hjp7461](https://github.com/hjp7461), Claude Code 활용
