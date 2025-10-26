# Claude Dev Agent Toolkit - GitHub Deployment Plan

## 📋 Project Information

**Current Name:** `claude-code-agents-workflow`
**New Name:** `claude-dev-agent-toolkit`
**Target:** GitHub Marketplace deployment for Windows compatibility

---

## 🎯 Why GitHub Marketplace?

**Problem:** Windows에서 로컬 플러그인 인식 불가
**Solution:** GitHub 기반 Marketplace로 배포하여 `/plugin marketplace add` 방식으로 설치

---

## 📦 Repository Structure

```
claude-dev-agent-toolkit/
├── .claude-plugin/
│   └── marketplace.json          # Marketplace 매니페스트
├── plugins/                       # .claude/plugins에서 이동
│   ├── 01-product-design/
│   │   ├── .claude-plugin/
│   │   │   └── plugin.json
│   │   ├── agents/
│   │   ├── commands/
│   │   ├── skills/
│   │   └── README.md
│   ├── 02-development/
│   ├── 03-debugging/
│   ├── 04-language-tools/
│   └── 05-content-marketing/
├── README.md
├── README_KR.md
├── LICENSE
├── .gitignore
└── GITHUB_DEPLOYMENT_PLAN.md    # This file
```

---

## ✅ Phase 1: 프로젝트 재구성

### 1.1 디렉토리 구조 변경
```bash
# 현재: .claude/plugins/
# 변경: plugins/

- [ ] .claude/plugins/ → plugins/ 로 이동
- [ ] .claude-plugin/ 디렉토리는 루트에 유지
```

### 1.2 Marketplace 매니페스트 수정

**파일:** `.claude-plugin/marketplace.json`

```json
{
  "name": "claude-dev-agent-toolkit",
  "version": "1.0.0",
  "description": "Professional development toolkit with specialized agents for Claude Code",
  "author": "Your Name",
  "homepage": "https://github.com/username/claude-dev-agent-toolkit",
  "repository": {
    "type": "git",
    "url": "https://github.com/username/claude-dev-agent-toolkit.git"
  },
  "keywords": [
    "claude-code",
    "claude-plugin",
    "ai-agents",
    "development-workflow",
    "automation",
    "productivity"
  ],
  "license": "MIT",
  "plugins": [
    {
      "name": "product-design-toolkit",
      "path": "plugins/01-product-design",
      "version": "1.0.0",
      "description": "Product strategy, UX design, and software architecture"
    },
    {
      "name": "development-toolkit",
      "path": "plugins/02-development",
      "version": "1.0.0",
      "description": "Implementation best practices, testing, and API design"
    },
    {
      "name": "debugging-toolkit",
      "path": "plugins/03-debugging",
      "version": "1.0.0",
      "description": "Systematic debugging with specialized diagnostic agents"
    },
    {
      "name": "language-tools",
      "path": "plugins/04-language-tools",
      "version": "1.0.0",
      "description": "Python, React, TypeScript debugging and optimization"
    },
    {
      "name": "content-marketing-toolkit",
      "path": "plugins/05-content-marketing",
      "version": "1.0.0",
      "description": "Content creation and SEO-optimized marketing"
    }
  ]
}
```

### 1.3 Commands YAML Frontmatter 체크

**모든 command 파일 상단에 필수:**

```yaml
---
description: Command description here
argument-hint: [argument description]
---
```

**체크 대상 파일:**
- `plugins/01-product-design/commands/feature-workflow.md`
- `plugins/01-product-design/commands/design-workflow.md`
- `plugins/01-product-design/commands/tech-request.md`
- `plugins/03-debugging/commands/bugfix-workflow.md`

---

## ✅ Phase 2: 문서 업데이트

### 2.1 README.md 주요 변경사항

```markdown
# Claude Dev Agent Toolkit

Professional development toolkit with specialized agents for Claude Code

## Installation from GitHub

### Step 1: Add Marketplace
\`\`\`bash
/plugin marketplace add https://github.com/username/claude-dev-agent-toolkit
\`\`\`

### Step 2: Install Plugins
\`\`\`bash
# Install all plugins
/plugin install product-design-toolkit@claude-dev-agent-toolkit
/plugin install development-toolkit@claude-dev-agent-toolkit
/plugin install debugging-toolkit@claude-dev-agent-toolkit
/plugin install language-tools@claude-dev-agent-toolkit
/plugin install content-marketing-toolkit@claude-dev-agent-toolkit

# Or install only what you need
/plugin install product-design-toolkit@claude-dev-agent-toolkit
\`\`\`

### Step 3: Verify Installation
\`\`\`bash
/plugin list
\`\`\`

### Step 4: Use Commands
\`\`\`bash
/feature-workflow Add user authentication
/design-workflow Redesign dashboard
/bugfix-workflow Fix login bug
\`\`\`
```

### 2.2 각 플러그인 README 업데이트

각 플러그인의 README.md에 설치 방법 추가:

```markdown
## Installation

\`\`\`bash
/plugin marketplace add https://github.com/username/claude-dev-agent-toolkit
/plugin install product-design-toolkit@claude-dev-agent-toolkit
\`\`\`
```

---

## ✅ Phase 3: Git/GitHub 설정

### 3.1 .gitignore 생성

```gitignore
# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db
desktop.ini

# Temp
*.tmp
*.log
*.cache

# User-specific Claude directories
# (원본 .claude/agents, .claude/commands는 제외)
```

### 3.2 LICENSE 파일 (MIT)

```
MIT License

Copyright (c) 2024 [Your Name]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
```

---

## ✅ Phase 4: GitHub 배포

### 4.1 Git 초기화 및 커밋

```bash
git init
git add .
git commit -m "Initial commit: Claude Dev Agent Toolkit v1.0.0

- 5 specialized plugin collections
- 18 agents for development workflows
- 6 knowledge skills (SOLID, GoF, OORP, Testing, Code Review, API Design)
- 4 orchestrated workflow commands
- Complete documentation in English and Korean
"
```

### 4.2 GitHub 원격 저장소 연결

```bash
# GitHub에서 저장소 생성 후
git remote add origin https://github.com/username/claude-dev-agent-toolkit.git
git branch -M main
git push -u origin main
```

### 4.3 릴리스 태그 생성

```bash
git tag -a v1.0.0 -m "Release v1.0.0: Initial plugin collection

Plugins:
- Product Design Toolkit
- Development Toolkit
- Debugging Toolkit
- Language Tools
- Content Marketing Toolkit

Features:
- 18 specialized agents
- 6 knowledge skills
- 4 workflow commands
- Full documentation
"

git push origin v1.0.0
```

### 4.4 GitHub 저장소 설정

**Topics:**
- `claude-code`
- `claude-plugin`
- `ai-agents`
- `development-workflow`
- `automation`
- `productivity`
- `typescript`
- `python`
- `react`

**Description:**
```
Professional development toolkit with specialized agents for Claude Code - Product design, development, debugging, and content creation workflows
```

**Features to Enable:**
- ✅ Issues
- ✅ Discussions
- ✅ Projects (optional)

---

## ✅ Phase 5: 테스트 및 검증

### 5.1 설치 테스트 (Windows)

```bash
# Claude Code에서 실행
/plugin marketplace add https://github.com/username/claude-dev-agent-toolkit

# Marketplace 확인
/plugin marketplace list

# 플러그인 설치
/plugin install product-design-toolkit@claude-dev-agent-toolkit

# 설치 확인
/plugin list
```

### 5.2 기능 테스트

```bash
# 명령어 테스트
/feature-workflow Build a simple todo application
/design-workflow Redesign the user dashboard
/bugfix-workflow Login button not responding --type=ui --scope=file

# Help 확인
/help
```

### 5.3 검증 체크리스트

- [ ] Marketplace 추가 성공
- [ ] 플러그인 설치 성공
- [ ] 명령어 자동완성 작동
- [ ] 명령어 실행 성공
- [ ] Agent 호출 성공
- [ ] Skills 접근 가능
- [ ] Windows 경로 처리 정상
- [ ] 한글 문서 정상 표시

---

## 📊 필수 파일 체크리스트

### 루트 디렉토리
- [ ] `.claude-plugin/marketplace.json` - Marketplace 매니페스트
- [ ] `README.md` - 영문 문서
- [ ] `README_KR.md` - 한글 문서
- [ ] `LICENSE` - MIT 라이선스
- [ ] `.gitignore` - Git 무시 파일
- [ ] `GITHUB_DEPLOYMENT_PLAN.md` - 이 문서

### 각 플러그인 (5개)
- [ ] `.claude-plugin/plugin.json` - 플러그인 메타데이터
- [ ] `README.md` - 플러그인 문서
- [ ] `agents/*.md` - 에이전트 정의
- [ ] `commands/*.md` - 명령어 (YAML frontmatter 필수!)
- [ ] `skills/*/SKILL.md` - 스킬 (해당되는 플러그인만)

---

## 🎯 배포 완료 후 사용법

### 사용자 설치 가이드

```bash
# 1. Marketplace 추가 (1회만)
/plugin marketplace add https://github.com/username/claude-dev-agent-toolkit

# 2. 원하는 플러그인 설치
/plugin install product-design-toolkit@claude-dev-agent-toolkit
/plugin install debugging-toolkit@claude-dev-agent-toolkit

# 3. 사용
/feature-workflow Create user authentication system
/bugfix-workflow Memory leak in data processing --type=runtime
```

### 플러그인 업데이트

```bash
# Marketplace 업데이트
/plugin marketplace update claude-dev-agent-toolkit

# 플러그인 재설치
/plugin install product-design-toolkit@claude-dev-agent-toolkit --force
```

---

## 🔧 트러블슈팅

### 문제: 명령어가 인식되지 않음
**해결:**
1. Commands 파일에 YAML frontmatter 있는지 확인
2. Claude Code 재시작
3. 플러그인 재설치

### 문제: Agent가 호출되지 않음
**해결:**
1. agent 파일 경로 확인
2. agent 파일 YAML frontmatter 확인
3. plugin.json에 agent가 등록되어 있는지 확인

### 문제: Skills가 접근되지 않음
**해결:**
1. skills/skill-name/SKILL.md 구조 확인
2. SKILL.md YAML frontmatter 확인
3. 플러그인 재설치

---

## 📝 추가 작업 (선택)

### GitHub Pages 문서 사이트
- [ ] docs/ 폴더 생성
- [ ] MkDocs 또는 Docusaurus 설정
- [ ] 사용 예시 스크린샷/GIF 추가
- [ ] 비디오 튜토리얼 제작

### 커뮤니티
- [ ] CONTRIBUTING.md 작성
- [ ] CODE_OF_CONDUCT.md 작성
- [ ] Issue 템플릿 추가
- [ ] PR 템플릿 추가

---

## 🎉 성공 기준

배포가 성공하면:

✅ 사용자가 단 3단계로 설치 가능
✅ Windows에서 정상 작동
✅ 모든 명령어 인식
✅ Agent와 Skills 정상 작동
✅ 문서가 명확하고 따라하기 쉬움

---

## 📅 타임라인

| 단계 | 작업 | 예상 시간 |
|------|------|-----------|
| 1 | 프로젝트 재구성 | 1-2시간 |
| 2 | 문서 업데이트 | 1시간 |
| 3 | Git/GitHub 설정 | 30분 |
| 4 | GitHub 배포 | 30분 |
| 5 | 테스트 및 검증 | 30분 |
| **총계** | | **4-5시간** |

---

**Last Updated:** 2024-10-26
**Version:** 1.0
**Status:** Planning Complete - Ready for Execution
