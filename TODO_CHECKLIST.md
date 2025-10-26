# Claude Dev Agent Toolkit - Deployment Checklist

## ✅ Quick TODO Checklist

### Phase 1: 프로젝트 재구성
- [ ] 폴더명 변경: `claude-code-agents-workflow` → `claude-dev-agent-toolkit`
- [ ] `.claude/plugins/` → `plugins/` 디렉토리 이동
- [ ] `.claude-plugin/marketplace.json` 수정
  - [ ] name → "claude-dev-agent-toolkit"
  - [ ] paths → "plugins/01-product-design" 등
  - [ ] GitHub URL 업데이트
- [ ] 모든 commands에 YAML frontmatter 확인
  - [ ] `plugins/01-product-design/commands/feature-workflow.md`
  - [ ] `plugins/01-product-design/commands/design-workflow.md`
  - [ ] `plugins/01-product-design/commands/tech-request.md`
  - [ ] `plugins/03-debugging/commands/bugfix-workflow.md`

### Phase 2: 문서 업데이트
- [ ] `README.md` 업데이트
  - [ ] 프로젝트명 변경
  - [ ] GitHub 설치 가이드 추가
  - [ ] 모든 URL 업데이트
- [ ] `README_KR.md` 업데이트
  - [ ] 프로젝트명 변경
  - [ ] GitHub 설치 가이드 추가
  - [ ] 모든 URL 업데이트
- [ ] 각 플러그인 `README.md` 업데이트 (5개)
  - [ ] 01-product-design
  - [ ] 02-development
  - [ ] 03-debugging
  - [ ] 04-language-tools
  - [ ] 05-content-marketing

### Phase 3: Git/GitHub 준비
- [ ] `.gitignore` 생성
- [ ] `LICENSE` 확인 (MIT)
- [ ] GitHub 저장소 생성: `claude-dev-agent-toolkit`

### Phase 4: 배포
- [ ] `git init`
- [ ] `git add .`
- [ ] `git commit -m "Initial commit"`
- [ ] `git remote add origin https://github.com/username/claude-dev-agent-toolkit.git`
- [ ] `git push -u origin main`
- [ ] `git tag -a v1.0.0 -m "Release v1.0.0"`
- [ ] `git push origin v1.0.0`
- [ ] GitHub Topics 추가: `claude-code`, `claude-plugin`, `ai-agents`, etc.

### Phase 5: 테스트
- [ ] `/plugin marketplace add https://github.com/username/claude-dev-agent-toolkit`
- [ ] `/plugin install product-design-toolkit@claude-dev-agent-toolkit`
- [ ] `/feature-workflow` 명령어 테스트
- [ ] `/design-workflow` 명령어 테스트
- [ ] `/bugfix-workflow` 명령어 테스트
- [ ] Windows 환경 검증

---

## 🔥 Critical Files (반드시 확인!)

### 필수 YAML Frontmatter
모든 command 파일 맨 위에:
```yaml
---
description: Command description
argument-hint: [arguments]
---
```

### Marketplace JSON
```json
{
  "name": "claude-dev-agent-toolkit",
  "plugins": [
    {
      "name": "product-design-toolkit",
      "path": "plugins/01-product-design"
    }
  ]
}
```

---

## 📞 Support

문제 발생 시:
1. `GITHUB_DEPLOYMENT_PLAN.md` 참조
2. 트러블슈팅 섹션 확인
3. GitHub Issues 생성
