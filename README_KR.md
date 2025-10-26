# Claude Code Agents Workflow - 플러그인 컬렉션

제품 개발, 소프트웨어 아키텍처, 디버깅 및 콘텐츠 제작을 위한 포괄적인 Claude Code 플러그인 컬렉션입니다. 이 저장소는 특화된 에이전트, 명령어 및 지식 스킬을 사용한 고급 워크플로 오케스트레이션을 시연합니다.

**[English Documentation](README.md)**

## 🙏 크레딧

이 프로젝트는 [omersaraf/claude-code-agents-workflow](https://github.com/omersaraf/claude-code-agents-workflow)의 원본 작업에서 영감을 받고 기반으로 합니다. 이 저장소는 플러그인 컬렉션으로 구조화되어 있지만, 핵심 아이디어와 워크플로 개념은 원본 프로젝트에서 가져왔습니다.

## 🎯 개요

이 저장소는 소프트웨어 개발의 특정 측면에 집중한 모듈식 플러그인으로 구성된 완전한 툴킷을 제공합니다:

- **제품 디자인 & 아키텍처** - 전략 기획 및 시스템 설계
- **개발 & 품질** - 구현 및 코드 품질 관행
- **디버깅 & 진단** - 체계적인 버그 수정 워크플로
- **언어별 도구** - Python, React, TypeScript 최적화
- **콘텐츠 마케팅** - 기술 콘텐츠 및 마케팅 자료

## 📦 플러그인 아키텍처

저장소는 함께 또는 개별적으로 설치할 수 있는 5개의 독립적인 플러그인으로 구성되어 있습니다:

```
plugins/
├── 01-product-design/        # 제품 전략, UX, 아키텍처
├── 02-development/            # 구현, 테스팅, API 설계
├── 03-debugging/              # 체계적 디버깅 워크플로
├── 04-language-tools/         # Python, React, TypeScript 도구
└── 05-content-marketing/      # 콘텐츠 제작 및 SEO
```

각 플러그인은 Claude Code 플러그인 구조를 따릅니다:
```
plugin-name/
├── .claude-plugin/
│   └── plugin.json           # 플러그인 메타데이터
├── agents/                   # 특화 에이전트
│   └── agent-name.md
├── commands/                 # 슬래시 명령어
│   └── command-name.md
├── skills/                   # 지식 베이스
│   └── skill-name/
│       └── SKILL.md
└── README.md                 # 플러그인 문서
```

## 🚀 빠른 시작

### GitHub Marketplace에서 설치

Windows 사용자에게 특히 권장되는 설치 방법입니다.

#### Step 1: Marketplace 추가
```bash
/plugin marketplace add https://github.com/your-username/claude-dev-agent-toolkit
```

#### Step 2: 플러그인 설치
필요한 플러그인만 선택하거나 모두 설치할 수 있습니다:

```bash
# 모든 플러그인 설치 (권장)
/plugin install product-design-toolkit@claude-dev-agent-toolkit
/plugin install development-toolkit@claude-dev-agent-toolkit
/plugin install debugging-toolkit@claude-dev-agent-toolkit
/plugin install language-tools@claude-dev-agent-toolkit
/plugin install content-marketing-toolkit@claude-dev-agent-toolkit

# 또는 필요한 것만 설치
/plugin install product-design-toolkit@claude-dev-agent-toolkit
/plugin install debugging-toolkit@claude-dev-agent-toolkit
```

#### Step 3: 설치 확인
```bash
# 설치된 플러그인 확인
/plugin list

# 사용 가능한 명령어:
# - /feature-workflow
# - /design-workflow
# - /tech-request
# - /bugfix-workflow
```

#### Step 4: 사용 시작
```bash
# 기능 워크플로 실행
/feature-workflow OAuth2를 사용한 사용자 인증 추가

# 디자인 워크플로 실행
/design-workflow 분석 대시보드 재설계

# 디버깅 워크플로 실행
/bugfix-workflow 로그인 버튼이 반응하지 않음 --type=ui --scope=file
```

### 대안: 수동 설치 (고급 사용자)

수동으로 설치하려면:

1. **저장소 클론**
   ```bash
   git clone https://github.com/your-username/claude-dev-agent-toolkit.git
   cd claude-dev-agent-toolkit
   ```

2. **Claude Code 디렉토리로 플러그인 복사**
   ```bash
   # Windows (PowerShell)
   Copy-Item -Recurse -Force plugins\* ~\.claude\plugins\

   # macOS/Linux
   cp -r plugins/* ~/.claude/plugins/
   ```

3. **Claude Code 재시작**하여 플러그인 로드

## 📚 플러그인 개요

### 1. 제품 디자인 툴킷 (`01-product-design`)

**목적:** 디자인 패턴 지식을 갖춘 제품 전략, UX 디자인 및 소프트웨어 아키텍처

**에이전트:**
- `agile-product-strategist` - 제품 기획, 사용자 스토리, MVP 정의
- `software-architect-designer` - SOLID 원칙을 따르는 기술 아키텍처
- `ux-design-specialist` - UI/UX 디자인, 와이어프레임, 접근성

**명령어:**
- `/feature-workflow` - 완전한 기능 개발 라이프사이클
- `/design-workflow` - UI/UX 디자인 구현 워크플로
- `/tech-request` - 기술 요청 처리

**스킬:**
- **SOLID 원칙** - 5가지 핵심 OOP 디자인 원칙
- **Gang of Four 패턴** - 23가지 클래식 디자인 패턴
- **OORP 패턴** - 레거시 시스템 개선을 위한 리엔지니어링 패턴

**사용 예시:**
```
/feature-workflow OAuth2와 JWT 토큰을 사용한 사용자 인증 추가
```

---

### 2. 개발 툴킷 (`02-development`)

**목적:** 구현 모범 사례, 테스팅 전략 및 API 설계

**에이전트:**
- `implementation-engineer` - 디자인 패턴을 활용한 깨끗한 코드 구현
- `code-quality-inspector` - 종합적인 코드 리뷰 및 품질 검사
- `qa-test-engineer` - 테스팅, QA 및 테스트 자동화

**스킬:**
- **테스팅 모범 사례** - 단위, 통합, E2E 테스팅 전략
- **코드 리뷰 체크리스트** - 모든 품질 측면을 다루는 체계적 리뷰
- **API 디자인 원칙** - RESTful API 설계 및 모범 사례

**사용 예시:**
```
# implementation engineer 에이전트 사용
SOLID 원칙과 Strategy 패턴을 따라 다양한 결제 방법을
지원하는 결제 처리 서비스 구현
```

---

### 3. 디버깅 툴킷 (`03-debugging`)

**목적:** 특화된 진단 에이전트를 통한 체계적 디버깅

**에이전트:**
- `bug-analyst` - 이슈 분류 및 분석
- `error-detective` - 로그 분석 및 에러 추적
- `code-diagnostician` - 코드 품질 및 패턴 분석
- `fix-architect` - 부작용을 최소화한 솔루션 설계
- `bugfix-implementer` - 수정 구현
- `fix-validator` - 테스팅 및 검증
- `bug-documenter` - 문서화 및 지식 관리

**명령어:**
- `/bugfix-workflow` - 분석부터 문서화까지 완전한 디버깅 워크플로

**사용 예시:**
```bash
/bugfix-workflow "버튼이 클릭에 반응하지 않음" --type=ui --scope=file

/bugfix-workflow "POST /api/users에서 500 에러" --severity=critical --type=runtime
```

---

### 4. 언어 도구 (`04-language-tools`)

**목적:** 언어별 디버깅 및 최적화

**에이전트:**
- `python-debugger` - Python 전용 디버깅 및 프로파일링
- `react-debugger` - React 컴포넌트 및 상태 디버깅
- `typescript-analyzer` - TypeScript 타입 에러 분석
- `performance-profiler` - 성능 병목 현상 식별

**사용 예시:**
```
# 파일 타입에 따라 자동으로 호출됨
/bugfix-workflow "데이터 처리 중 메모리 누수" --type=runtime
```

---

### 5. 콘텐츠 마케팅 툴킷 (`05-content-marketing`)

**목적:** 콘텐츠 제작 및 마케팅 자료

**에이전트:**
- `content-marketer` - 블로그 포스트, 소셜 미디어, SEO 최적화 콘텐츠

**사용 예시:**
```
시니어 개발자를 대상으로 마이크로서비스 아키텍처에 대한
기술 블로그 포스트 작성, 1500 단어,
"microservices best practices"로 SEO 최적화
```

## 🎓 스킬 시스템

스킬은 에이전트가 자동으로 액세스할 수 있는 재사용 가능한 지식을 제공합니다. 각 스킬은 집중된 지식 도메인입니다:

### 디자인 & 아키텍처 스킬
- **SOLID 원칙** - 단일 책임, 개방-폐쇄, 리스코프 치환, 인터페이스 분리, 의존성 역전
- **Gang of Four 패턴** - 생성, 구조, 행동 패턴
- **OORP 패턴** - 첫 접촉, 분석, 계획, 테스팅, 마이그레이션, 변환

### 개발 스킬
- **테스팅 모범 사례** - 테스팅 피라미드, AAA 패턴, 픽스처, 모킹, 커버리지
- **코드 리뷰 체크리스트** - 기능성, 보안, 성능, 테스팅 리뷰 가이드라인
- **API 디자인 원칙** - RESTful 규칙, HTTP 메서드, 상태 코드, 버전 관리

## 🔄 워크플로 예시

### 완전한 기능 개발

```
/feature-workflow 썸네일 생성 기능을 포함한 사용자 프로필 이미지 업로드 추가
```

**오케스트레이션:**
1. **제품 전략가**가 사용자 스토리로 사양서 작성
2. **아키텍트**가 기술 솔루션을 설계하고 작업으로 분해
3. **구현 엔지니어**가 각 컴포넌트 구축
4. **코드 품질 검사자**가 각 구현 리뷰
5. **QA 엔지니어**가 기능성 검증 및 테스트 실행

### UI/UX 디자인 구현

```
/design-workflow 개선된 데이터 시각화로 분석 대시보드 재설계
```

**오케스트레이션:**
1. **UX 디자이너**가 와이어프레임으로 디자인 솔루션 생성
2. **아키텍트**가 기술 구현 계획 작성
3. **구현 엔지니어**가 UI 컴포넌트 구축
4. **코드 품질 검사자**가 구현 리뷰
5. **QA 엔지니어**가 다양한 디바이스 및 브라우저에서 테스트
6. **UX 디자이너**가 최종 디자인이 사양과 일치하는지 검증

### 체계적 디버깅

```
/bugfix-workflow "대용량 데이터셋 처리 시 앱 크래시" --severity=high --type=runtime --scope=module
```

**오케스트레이션:**
1. **버그 분석가**가 이슈 분석 및 분류
2. **에러 탐정**이 로그 및 스택 트레이스 조사
3. **코드 진단가**가 코드 패턴 검사
4. **수정 아키텍트**가 최적 솔루션 설계
5. **버그 수정 구현자**가 수정 구현
6. **수정 검증자**가 수정 검증 및 회귀 테스트 실행
7. **버그 문서화자**가 솔루션 및 예방책 문서화

## 🛠️ 커스터마이제이션

### 새 스킬 추가

1. 스킬 디렉토리 생성: `.claude/plugins/{plugin-name}/skills/{skill-name}/`
2. 프론트매터와 함께 `SKILL.md` 추가:
   ```yaml
   ---
   name: my-skill
   description: 이 스킬을 언제, 어떻게 사용하는지
   ---
   # 스킬 내용
   ```

### 새 에이전트 생성

1. 에이전트 파일 추가: `.claude/plugins/{plugin-name}/agents/my-agent.md`
2. YAML 프론트매터와 프롬프트로 에이전트 정의

### 슬래시 명령어 추가

1. 명령어 파일 생성: `.claude/plugins/{plugin-name}/commands/my-command.md`
2. 워크플로 오케스트레이션 로직 정의

## 📊 플러그인 비교

| 플러그인 | 에이전트 | 명령어 | 스킬 | 주요 사용 사례 |
|--------|--------|----------|--------|------------------|
| 제품 디자인 | 3 | 3 | 3 | 전략, 아키텍처, UX |
| 개발 | 3 | 0 | 3 | 구현, 테스팅, API |
| 디버깅 | 7 | 1 | 0 | 버그 수정, 진단 |
| 언어 도구 | 4 | 0 | 0 | 언어별 디버깅 |
| 콘텐츠 마케팅 | 1 | 0 | 0 | 콘텐츠 제작, SEO |

## 🎯 토큰 최적화 이점

플러그인 아키텍처는 다음과 같이 토큰 사용을 최적화합니다:

1. **모듈식 로딩**: 활성 플러그인 콘텐츠만 로드
2. **스킬 참조**: 에이전트가 지식을 임베드하는 대신 스킬 참조
3. **점진적 공개**: 스킬이 필요할 때만 상세 정보 로드
4. **집중된 컨텍스트**: 각 플러그인이 타겟 도메인 지식 보유

**토큰 절약**: 모놀리식 에이전트 파일 대비 최대 60-70% 감소.

## 💡 모범 사례

### 어떤 플러그인을 사용할지

- **새 기능 계획?** → 제품 디자인 (feature-workflow)
- **코드 구현?** → 개발 (에이전트 + 스킬)
- **프로덕션 버그?** → 디버깅 (bugfix-workflow)
- **언어별 이슈?** → 언어 도구 (자동 호출)
- **콘텐츠 작성?** → 콘텐츠 마케팅 (content-marketer)

### 플러그인 결합

플러그인은 원활하게 함께 작동합니다:
```
# 제품 디자인으로 시작
/feature-workflow 실시간 알림 추가

# 개발 플러그인이 구현 처리
# 디버깅 플러그인이 이슈 처리
# 언어 도구가 언어별 코드 최적화
```

## 📖 문서

- [제품 디자인 플러그인](.claude/plugins/01-product-design/README.md)
- [개발 플러그인](.claude/plugins/02-development/README.md)
- [디버깅 플러그인](.claude/plugins/03-debugging/README.md)
- [언어 도구 플러그인](.claude/plugins/04-language-tools/README.md)
- [콘텐츠 마케팅 플러그인](.claude/plugins/05-content-marketing/README.md)

## 🤝 기여하기

기여를 환영합니다! 다음을 따라주세요:

1. 저장소 포크
2. 기능 브랜치 생성 (`git checkout -b feature/new-skill`)
3. 플러그인 구조를 따라 스킬/에이전트/명령어 추가
4. 철저히 테스트
5. 풀 리퀘스트 제출

### 기여 아이디어

- 새 스킬 추가 (예: 보안 모범 사례, 성능 최적화)
- 언어별 스킬 생성 (Go, Rust, Java)
- 도메인별 에이전트 추가 (DevOps, 데이터 사이언스, 모바일)
- 기존 워크플로 개선
- 더 포괄적인 예시 추가

## 📋 로드맵 & TODO

### 계획된 스킬 (향후 추가 예정)

#### 보안 & 모범 사례
- [ ] **보안 모범 사례** - OWASP Top 10, 안전한 코딩 가이드라인, 취약점 예방
- [ ] **인증 & 권한 부여** - OAuth, JWT, 세션 관리 모범 사례
- [ ] **데이터 보호** - 암호화, GDPR 준수, 개인정보 처리

#### 성능 & 최적화
- [ ] **성능 최적화** - 프로파일링, 캐싱 전략, 쿼리 최적화
- [ ] **데이터베이스 설계** - 정규화, 인덱싱 전략, 쿼리 성능
- [ ] **확장성 패턴** - 로드 밸런싱, 캐싱, 수평 확장

#### 코드 품질 & 유지보수
- [ ] **Clean Code 원칙** - Robert C. Martin의 원칙, 네이밍 규칙, 코드 스멜
- [ ] **리팩토링 카탈로그** - Martin Fowler의 리팩토링 패턴, 언제 어떻게 리팩토링
- [ ] **기술 부채 관리** - 기술 부채 식별, 추적 및 해결

#### 언어별 스킬
- [ ] **Go 모범 사례** - 관용적 Go, 동시성 패턴, 에러 처리
- [ ] **Rust 패턴** - 소유권, 차용, 생명주기 관리
- [ ] **Java 디자인 패턴** - 엔터프라이즈 패턴, Spring 프레임워크 모범 사례

#### 도메인별
- [ ] **DevOps 관행** - CI/CD 파이프라인, 코드형 인프라, 모니터링
- [ ] **마이크로서비스 패턴** - 서비스 통신, 데이터 일관성, 배포
- [ ] **이벤트 기반 아키텍처** - 이벤트 소싱, CQRS, 메시지 큐

### 계획된 에이전트
- [ ] **보안 전문가** - 보안 취약점 분석 및 권장사항
- [ ] **데이터베이스 최적화자** - 쿼리 최적화 및 스키마 설계
- [ ] **DevOps 엔지니어** - CI/CD 설정 및 인프라 자동화
- [ ] **모바일 개발자** - iOS/Android 개발 모범 사례

### 계획된 명령어
- [ ] `/security-audit` - 종합 보안 감사 워크플로
- [ ] `/performance-optimization` - 성능 분석 및 최적화 워크플로
- [ ] `/refactoring-workflow` - 체계적 리팩토링 워크플로

## 📦 Claude Code Marketplace에 배포하기

### Marketplace 제출 전제 조건

이 플러그인들을 Claude Code Marketplace에 배포하려면:

1. **GitHub 저장소 설정**
   - 공개 GitHub 저장소에 플러그인 호스팅
   - 각 플러그인에 적절한 문서 포함
   - 명확한 설치 지침 포함
   - LICENSE 파일 추가 (MIT 권장)

2. **플러그인 구조 요구사항**
   ```
   your-repo/
   ├── .claude-plugin/
   │   └── marketplace.json    # Marketplace 메타데이터
   ├── plugins/
   │   ├── plugin-1/
   │   │   ├── .claude-plugin/
   │   │   │   └── plugin.json
   │   │   ├── agents/
   │   │   ├── commands/
   │   │   └── skills/
   │   └── plugin-2/
   └── README.md
   ```

3. **Marketplace 매니페스트** (`.claude-plugin/marketplace.json`)
   ```json
   {
     "name": "claude-code-agents-workflow",
     "description": "종합 개발 워크플로 플러그인",
     "author": "Your Name",
     "homepage": "https://github.com/your-username/claude-code-agents-workflow",
     "plugins": [
       {
         "name": "product-design-toolkit",
         "path": ".claude/plugins/01-product-design"
       },
       {
         "name": "development-toolkit",
         "path": ".claude/plugins/02-development"
       },
       {
         "name": "debugging-toolkit",
         "path": ".claude/plugins/03-debugging"
       },
       {
         "name": "language-tools",
         "path": ".claude/plugins/04-language-tools"
       },
       {
         "name": "content-marketing-toolkit",
         "path": ".claude/plugins/05-content-marketing"
       }
     ]
   }
   ```

4. **배포 옵션**

   **옵션 A: 개별 플러그인 저장소** (Marketplace에 권장)
   - 각 플러그인별로 별도 저장소 생성
   - 각 저장소에 하나의 집중된 플러그인 포함
   - 사용자가 필요한 것만 설치하기 쉬움
   - 예시:
     - `claude-code-product-design-toolkit`
     - `claude-code-development-toolkit`
     - `claude-code-debugging-toolkit`

   **옵션 B: 멀티 플러그인 모노레포**
   - 모든 플러그인이 포함된 단일 저장소
   - 사용자가 설치할 플러그인 선택 가능
   - 관련 플러그인을 함께 유지관리하기 좋음
   - marketplace.json으로 사용 가능한 모든 플러그인 나열

5. **제출 프로세스**
   - 모든 플러그인이 Claude Code 플러그인 표준을 따르는지 확인
   - 로컬 환경에서 플러그인을 철저히 테스트
   - 예시가 포함된 적절한 문서 작성
   - Claude Code Marketplace에 제출 (출시 시)
   - 커뮤니티는 다음과 같이 설치: `claude plugin install your-username/repo-name`

### 현재 상태

**✅ GitHub 준비 완료**: 플러그인이 적절하게 구조화되고 문서화됨
**⏳ Marketplace**: 공식 Claude Code Marketplace 출시 대기 중

현재는 다음과 같이 설치 가능:
```bash
git clone https://github.com/your-username/claude-code-agents-workflow.git
cp -r claude-code-agents-workflow/.claude/plugins/* ~/.claude/plugins/
```

### 배포 체크리스트

- [ ] 공개 GitHub 저장소 생성
- [ ] 예시가 포함된 포괄적인 README 추가
- [ ] LICENSE 파일 포함 (MIT)
- [ ] `.claude-plugin/marketplace.json` 추가
- [ ] 새로운 Claude Code 설치에서 모든 플러그인 테스트
- [ ] 버전 관리를 위한 릴리스 태그 생성
- [ ] GitHub 토픽 추가: `claude-code`, `claude-plugin`, `ai-agents`
- [ ] 사용 예시 비디오/GIF 생성
- [ ] 커뮤니티 지원을 위한 GitHub Discussions 설정

## 📝 라이선스

MIT License - 자세한 내용은 [LICENSE](LICENSE) 참조

## 🔗 리소스

- [Claude Code 문서](https://docs.anthropic.com/claude-code)
- [Claude Code 플러그인 가이드](https://docs.claude.com/en/docs/claude-code/plugins)
- [에이전트 스킬 개요](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview)

## 💬 지원

- **이슈**: [GitHub Issues](https://github.com/your-username/claude-code-agents-workflow/issues)
- **토론**: [GitHub Discussions](https://github.com/your-username/claude-code-agents-workflow/discussions)

---

**Claude Code 커뮤니티를 위해 ❤️로 만들었습니다**
