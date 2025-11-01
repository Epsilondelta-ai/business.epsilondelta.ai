# GitHub Pages 배포 가이드

## 개요

이 사이트는 GitHub Actions를 통해 자동으로 GitHub Pages에 배포됩니다.

## 배포 설정

### 1. GitHub Repository 설정

1. GitHub 웹사이트에서 저장소로 이동
2. **Settings** → **Pages** 클릭
3. **Source**: "GitHub Actions" 선택
4. **Custom domain** (선택사항): `business.epsilondelta.ai` 입력
5. **Enforce HTTPS** 체크 (권장)

### 2. DNS 설정 (Custom Domain 사용시)

도메인 제공업체(예: Cloudflare, AWS Route53 등)에서 다음 설정:

#### A 레코드 방식
```
Type: A
Name: business (또는 @)
Value: 
  185.199.108.153
  185.199.109.153
  185.199.110.153
  185.199.111.153
TTL: 3600 (또는 자동)
```

#### CNAME 방식
```
Type: CNAME
Name: business (또는 www)
Value: [your-username].github.io
TTL: 3600
```

### 3. GitHub Actions 워크플로우

워크플로우 파일 위치: `.github/workflows/hugo.yml`

#### 트리거 조건
- `main` 브랜치에 push
- 수동 실행 (workflow_dispatch)

#### 빌드 과정
1. Hugo Extended v0.147.2 설치
2. 저장소 체크아웃
3. Hugo 빌드 실행 (`--gc --minify`)
4. GitHub Pages에 아티팩트 업로드
5. 자동 배포

## 배포 프로세스

### 자동 배포

```bash
# 1. 변경사항 커밋
git add .
git commit -m "Add new post"

# 2. GitHub에 push
git push origin main

# 3. GitHub Actions가 자동으로 빌드 및 배포
```

### 수동 배포

GitHub 웹사이트에서:
1. **Actions** 탭 이동
2. "Deploy Hugo site to GitHub Pages" 워크플로우 선택
3. **Run workflow** 버튼 클릭
4. 브랜치 선택 (main)
5. **Run workflow** 확인

## 배포 모니터링

### GitHub Actions 로그 확인

1. 저장소의 **Actions** 탭
2. 최근 워크플로우 실행 클릭
3. 각 단계별 로그 확인

### 배포 상태

- ✅ **Success**: 배포 성공, 사이트 업데이트됨
- ❌ **Failure**: 빌드 실패, 로그 확인 필요
- 🟡 **In Progress**: 빌드 진행 중

### 일반적인 빌드 시간

- **첫 배포**: 5-10분
- **이후 배포**: 2-3분
- **빌드만**: < 1분

## 로컬 테스트

배포 전 항상 로컬에서 테스트:

```bash
# 개발 서버 (draft 포함)
hugo server -D

# 프로덕션 빌드 테스트
hugo --gc --minify
```

## 문제 해결

### 배포 실패 시

1. **Actions 로그 확인**
   - 에러 메시지 확인
   - 어느 단계에서 실패했는지 파악

2. **일반적인 문제**
   - Hugo 버전 불일치
   - 설정 파일 오류 (`hugo.toml`)
   - 권한 문제 (Permissions 설정 확인)

3. **로컬에서 빌드 테스트**
   ```bash
   hugo --gc --minify
   ```

### 사이트가 업데이트되지 않을 때

1. GitHub Actions 완료 확인
2. 브라우저 캐시 삭제 (Ctrl/Cmd + Shift + R)
3. DNS 전파 대기 (최대 24시간, 보통 1-2시간)

### Custom Domain 문제

1. **CNAME 파일 확인**
   - `static/CNAME` 파일 존재 확인
   - 도메인 이름 정확히 입력되었는지 확인

2. **DNS 설정 확인**
   ```bash
   # DNS 조회
   nslookup business.epsilondelta.ai
   
   # 또는
   dig business.epsilondelta.ai
   ```

3. **GitHub Pages 상태**
   - Settings → Pages에서 Custom domain 상태 확인
   - "DNS check successful" 메시지 확인

## 보안

### HTTPS 강제

GitHub Pages는 자동으로 Let's Encrypt 인증서를 제공합니다:
- Settings → Pages → Enforce HTTPS 체크

### 권한 설정

워크플로우 파일의 권한 설정:
```yaml
permissions:
  contents: read
  pages: write
  id-token: write
```

## 추가 리소스

- [Hugo Documentation](https://gohugo.io/documentation/)
- [GitHub Pages Documentation](https://docs.github.com/pages)
- [GitHub Actions for Hugo](https://github.com/marketplace/actions/hugo-setup)

## 지원

문제가 발생하면:
1. [Hugo Discourse](https://discourse.gohugo.io/)
2. [GitHub Issues](https://github.com/[your-repo]/issues)

