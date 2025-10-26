# Quick Start Guide - Claude Dev Agent Toolkit

## 🚀 3분 안에 GitHub 배포하기

### Step 1: 폴더명 변경
```
claude-code-agents-workflow → claude-dev-agent-toolkit
```

### Step 2: 디렉토리 재구성
```bash
# .claude/plugins/ → plugins/ 로 이동
mv .claude/plugins plugins
```

### Step 3: Marketplace JSON 수정
파일: `.claude-plugin/marketplace.json`
```json
{
  "name": "claude-dev-agent-toolkit",
  "plugins": [
    {"name": "product-design-toolkit", "path": "plugins/01-product-design"},
    {"name": "development-toolkit", "path": "plugins/02-development"},
    {"name": "debugging-toolkit", "path": "plugins/03-debugging"},
    {"name": "language-tools", "path": "plugins/04-language-tools"},
    {"name": "content-marketing-toolkit", "path": "plugins/05-content-marketing"}
  ]
}
```

### Step 4: GitHub 배포
```bash
git init
git add .
git commit -m "Initial commit: Claude Dev Agent Toolkit v1.0.0"
git remote add origin https://github.com/username/claude-dev-agent-toolkit.git
git push -u origin main
git tag -a v1.0.0 -m "Release v1.0.0"
git push origin v1.0.0
```

### Step 5: 사용자 설치
```bash
/plugin marketplace add https://github.com/username/claude-dev-agent-toolkit
/plugin install product-design-toolkit@claude-dev-agent-toolkit
```

---

## ⚠️ 반드시 확인할 것!

### Commands에 YAML Frontmatter
모든 `.md` 명령어 파일 맨 위:
```yaml
---
description: Command description
argument-hint: [arguments]
---
```

**확인 대상:**
- `plugins/01-product-design/commands/feature-workflow.md`
- `plugins/01-product-design/commands/design-workflow.md`
- `plugins/01-product-design/commands/tech-request.md`
- `plugins/03-debugging/commands/bugfix-workflow.md`

---

## 📝 상세 문서

- **전체 계획:** `GITHUB_DEPLOYMENT_PLAN.md`
- **체크리스트:** `TODO_CHECKLIST.md`
- **README:** `README.md`, `README_KR.md`

---

## 🆘 문제 해결

**명령어 인식 안됨?**
→ Commands에 YAML frontmatter 확인

**플러그인 설치 안됨?**
→ marketplace.json 경로 확인 (plugins/...)

**Windows에서 안됨?**
→ GitHub Marketplace 방식 사용 (로컬 플러그인 X)

---

**준비됐으면 바로 시작! 🚀**
