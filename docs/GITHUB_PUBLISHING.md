# GitHub Publishing Guide

## 1. Recommended Repository Name

```text
relay-ai-talent-platform
```

추천 설명:

```text
AI-powered recruitment and personalized onboarding platform built with Next.js, NestJS, PostgreSQL, and RAG.
```

추천 Topics:

```text
nextjs nestjs typescript postgresql typeorm openai rag ai-recruitment onboarding fullstack
```

## 2. Before Publishing

다음 항목을 반드시 확인합니다.

- `.env`와 실제 API 키가 포함되지 않았는지
- DB 비밀번호, JWT 비밀키, 암호화 키가 포함되지 않았는지
- 관리자·신입사원 데모 비밀번호를 README에 적지 않았는지
- 실제 지원자의 이름, 전화번호, 이메일, 이력서가 포함되지 않았는지
- 업로드된 PDF·포트폴리오 파일이 포함되지 않았는지
- 로컬 DB dump가 포함되지 않았는지
- 이미지와 로고를 공개할 권한이 있는지

검색 예시:

```bash
rg -n "API_KEY|SECRET|PASSWORD|DATABASE_URL|BEGIN PRIVATE KEY" . \
  --glob '!node_modules/**' \
  --glob '!.git/**'
```

검색 결과가 모두 유출이라는 뜻은 아닙니다. `.env.example`의 빈 예시인지, 실제 값인지 직접 확인해야 합니다.

## 3. Suggested Screenshots

`assets/screenshots` 폴더를 추가하고 아래 화면을 개인정보가 없는 데모 데이터로 캡처하면 README의 전달력이 좋아집니다.

1. 기업 상세 랜딩
2. 지원서 작성
3. 관리자 지원자 분석
4. 실무 시험 문제
5. 과목별 시험 분석
6. 신입사원 오늘의 여정
7. 온보딩 관리자 진행 현황

권장 폭은 1600px 이상이며, 브라우저 탭·북마크·개인 계정 정보는 잘라냅니다.

## 4. Initialize and Push

```bash
cd relay-ai-talent-platform-portfolio
git init
git add .
git commit -m "docs: add Relay portfolio"
git branch -M main
git remote add origin https://github.com/<YOUR_ID>/relay-ai-talent-platform.git
git push -u origin main
```

이미 원격 저장소가 연결되어 있다면 `git remote add origin`은 다시 실행하지 않습니다.

## 5. If Publishing the Source Code Too

현재 제품 소스는 여러 프로젝트 폴더로 나뉘어 있습니다. 공개용 단일 저장소로 합칠 때 각 폴더 내부의 `.git` 디렉터리를 그대로 복사하면 중첩 저장소가 되어 파일이 정상적으로 올라가지 않을 수 있습니다.

권장 공개 구조:

```text
relay-ai-talent-platform/
├── apps/
│   ├── candidate-web/
│   ├── recruiting-admin/
│   ├── practical-exam/
│   └── onboarding-web/
├── server/
├── docs/
├── README.md
└── .gitignore
```

소스까지 공개하기 전에는 회사 자산, 라이선스, 개인정보, 채용 문제 원문 공개 가능 여부를 별도로 검토해야 합니다.

