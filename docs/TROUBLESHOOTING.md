# Troubleshooting Guide - Claude Dev Agent Toolkit

이 문서는 Claude Dev Agent Toolkit 개발 및 배포 과정에서 발생한 문제와 해결 방법을 기록합니다.

## 📋 목차
- [Marketplace JSON 스키마 문제](#marketplace-json-스키마-문제)
- [Plugin JSON 스키마 문제](#plugin-json-스키마-문제)
- [일반적인 디버깅 팁](#일반적인-디버깅-팁)
- [베스트 프랙티스](#베스트-프랙티스)

---

## Marketplace JSON 스키마 문제

### 문제 1: `owner` 필드 누락
**에러 메시지:**
```
Error: Invalid schema: owner: Required
```

**원인:**
`.claude-plugin/marketplace.json`에 `owner` 필드가 없음

**해결 방법:**
```json
{
  "owner": {
    "name": "your-github-username"
  }
}
```

**주의사항:**
- `owner`는 **객체 형식**이어야 함 (문자열 X)
- `name` 속성에 GitHub username을 입력

---

### 문제 2: `path` vs `source` 키 문제
**에러 메시지:**
```
Error: plugins.0: Unrecognized key(s) in object: 'path'
```

**원인:**
플러그인 경로를 `path`로 지정했으나, 올바른 키는 `source`

**잘못된 예:**
```json
{
  "plugins": [
    {
      "name": "my-plugin",
      "path": "plugins/my-plugin"  // ❌ 잘못됨
    }
  ]
}
```

**올바른 예:**
```json
{
  "plugins": [
    {
      "name": "my-plugin",
      "source": "./plugins/my-plugin"  // ✅ 올바름
    }
  ]
}
```

**주의사항:**
- 키 이름은 `source` 사용
- 경로는 반드시 `./`로 시작해야 함
- 상대 경로 사용 (저장소 루트 기준)

---

### 문제 3: `source` 경로 형식 오류
**에러 메시지:**
```
Error: plugins.0.source: Invalid input: must start with "./"
```

**원인:**
`source` 경로가 `./`로 시작하지 않음

**잘못된 예:**
```json
"source": "plugins/my-plugin"  // ❌
```

**올바른 예:**
```json
"source": "./plugins/my-plugin"  // ✅
```

---

### 완벽한 marketplace.json 예제

```json
{
  "name": "my-plugin-collection",
  "version": "1.0.0",
  "description": "Description of your plugin collection",
  "owner": {
    "name": "your-github-username"
  },
  "author": "Your Name or Organization",
  "homepage": "https://github.com/your-username/your-repo",
  "repository": {
    "type": "git",
    "url": "https://github.com/your-username/your-repo.git"
  },
  "keywords": [
    "claude-code",
    "claude-plugin"
  ],
  "license": "MIT",
  "plugins": [
    {
      "name": "my-plugin",
      "source": "./plugins/my-plugin",
      "description": "Plugin description",
      "version": "1.0.0"
    }
  ]
}
```

---

## Plugin JSON 스키마 문제

### 문제 4: `author` 필드 타입 오류
**에러 메시지:**
```
Validation errors: author: Expected object, received string
```

**원인:**
각 플러그인의 `plugin.json`에서 `author`를 문자열로 지정

**잘못된 예:**
```json
{
  "name": "my-plugin",
  "author": "My Name"  // ❌ 문자열
}
```

**올바른 예:**
```json
{
  "name": "my-plugin",
  "author": {
    "name": "My Name"  // ✅ 객체
  }
}
```

---

### 문제 5: 인식되지 않는 `tags` 필드
**에러 메시지:**
```
Validation errors: Unrecognized key(s) in object: 'tags'
```

**원인:**
`plugin.json`에 `tags` 필드가 지원되지 않음

**잘못된 예:**
```json
{
  "name": "my-plugin",
  "tags": ["tag1", "tag2"]  // ❌ 지원되지 않는 필드
}
```

**해결 방법:**
`tags` 필드를 제거하고 `keywords`는 marketplace.json에서만 사용

---

### 완벽한 plugin.json 예제

```json
{
  "name": "my-plugin",
  "version": "1.0.0",
  "description": "Detailed plugin description",
  "author": {
    "name": "Your Name"
  },
  "homepage": "https://github.com/your-username/your-repo"
}
```

**필수 필드:**
- `name`: 플러그인 이름 (marketplace.json의 plugins.name과 일치)
- `version`: 버전 (semantic versioning)
- `description`: 플러그인 설명
- `author`: 작성자 정보 (객체 형식)

**선택 필드:**
- `homepage`: 프로젝트 홈페이지 URL
- `repository`: 저장소 정보

---

## Commands 파일 스키마 문제

### 문제 6: YAML Frontmatter 누락
**증상:**
명령어가 Claude Code에서 인식되지 않음

**원인:**
`.md` 명령어 파일 상단에 YAML frontmatter가 없음

**해결 방법:**
모든 command 파일 상단에 다음 형식의 frontmatter 추가:

```yaml
---
description: Command description here
argument-hint: [argument description]
---
```

**예제:**
```markdown
---
description: Complete feature development workflow from idea to production
argument-hint: [feature description]
---

# Feature Workflow Command

Command content here...
```

**주의사항:**
- `---`로 시작하고 `---`로 끝나야 함
- `description`: 필수 (명령어 설명)
- `argument-hint`: 선택 (인자 힌트)
- frontmatter와 본문 사이에 빈 줄 필요

---

## 일반적인 디버깅 팁

### 1. 스키마 검증 오류 읽기
Claude Code의 에러 메시지는 매우 명확합니다:
- `Required`: 필수 필드 누락
- `Expected object, received string`: 타입 불일치
- `Unrecognized key(s)`: 지원되지 않는 필드
- `Invalid input`: 형식 오류

### 2. 캐시 문제 해결
플러그인을 수정한 후 변경사항이 반영되지 않을 때:

```bash
# Marketplace 캐시 업데이트
/plugin marketplace update your-marketplace-name

# 또는 제거 후 재추가
/plugin marketplace remove your-marketplace-name
/plugin marketplace add https://github.com/username/repo
```

### 3. 로컬 테스트
GitHub에 푸시하기 전에 로컬에서 JSON 파일 검증:

```bash
# JSON 형식 검증
cat .claude-plugin/marketplace.json | jq .

# 각 플러그인 검증
cat plugins/*/. claude-plugin/plugin.json | jq .
```

### 4. Git 커밋 전 체크리스트
- [ ] marketplace.json의 모든 `source` 경로가 `./`로 시작
- [ ] marketplace.json에 `owner` 객체 포함
- [ ] 모든 plugin.json의 `author`가 객체 형식
- [ ] plugin.json에 `tags` 필드 없음
- [ ] 모든 command 파일에 YAML frontmatter 포함
- [ ] GitHub URL이 실제 username/repo로 업데이트됨

---

## 베스트 프랙티스

### 1. 프로젝트 구조
```
your-repo/
├── .claude-plugin/
│   └── marketplace.json          # Marketplace 설정
├── docs/                          # 문서 폴더
│   ├── TROUBLESHOOTING.md        # 이 문서
│   └── ...
├── plugins/                       # 플러그인들
│   └── plugin-name/
│       ├── .claude-plugin/
│       │   └── plugin.json       # 플러그인 메타데이터
│       ├── agents/               # 에이전트들
│       ├── commands/             # 명령어들 (YAML frontmatter 필수!)
│       └── skills/               # 스킬들
├── .gitignore
├── LICENSE
├── README.md
└── README_KR.md
```

### 2. 버전 관리
- Semantic Versioning 사용: `MAJOR.MINOR.PATCH`
- marketplace.json과 각 plugin.json의 버전을 일치시킴
- Git 태그로 릴리스 관리: `v1.0.0`

### 3. 문서화
- README에 명확한 설치 가이드 포함
- 각 플러그인별 README 작성
- Troubleshooting 가이드 유지보수
- 변경 사항은 CHANGELOG에 기록

### 4. 테스트 워크플로
1. 로컬에서 JSON 검증
2. Git 커밋
3. GitHub 푸시
4. Marketplace 업데이트 또는 재추가
5. 플러그인 설치 테스트
6. 명령어 실행 테스트

### 5. 에러 발생 시 접근 방법
1. 에러 메시지를 **정확히** 읽기
2. 해당 파일 열어서 스키마 확인
3. 이 문서에서 유사한 문제 찾기
4. 수정 → 커밋 → 푸시 → 테스트
5. 새로운 문제면 이 문서에 추가

---

## 자주 발생하는 실수 요약

| 실수 | 올바른 방법 |
|------|------------|
| `"owner": "username"` | `"owner": {"name": "username"}` |
| `"path": "plugins/..."` | `"source": "./plugins/..."` |
| `"source": "plugins/..."` | `"source": "./plugins/..."` |
| `"author": "Name"` | `"author": {"name": "Name"}` |
| `"tags": [...]` 사용 | `tags` 필드 제거 |
| Command 파일에 frontmatter 없음 | YAML frontmatter 추가 |
| `your-username` 그대로 남김 | 실제 GitHub username으로 변경 |

---

## 도움이 필요할 때

1. **이 문서 먼저 확인**: 대부분의 문제가 여기 기록되어 있음
2. **에러 메시지 읽기**: Claude Code는 명확한 에러 메시지 제공
3. **공식 문서**: [Claude Code Plugin Documentation](https://docs.claude.com/en/docs/claude-code/plugins)
4. **GitHub Issues**: 새로운 문제면 이슈 생성

---

**Last Updated**: 2024-10-26
**Version**: 1.0
**Maintainer**: Claude Dev Agent Toolkit Team

## 변경 이력

### 2024-10-26
- 초기 문서 작성
- Marketplace JSON 스키마 문제 6건 기록
- Plugin JSON 스키마 문제 2건 기록
- Commands YAML frontmatter 문제 기록
- 베스트 프랙티스 추가
