# PFMEA / CP AI — AIAG-VDA PWA

AIAG-VDA 5th Edition 기반 AI 자동 PFMEA & Control Plan 작성 PWA 도구

## 기능

- PDF / 이미지 도면 업로드 → AI 자동 분석
- 잠재 고장모드(FM), 영향(Effect), S/O/D/RPN 자동 생성
- Control Plan 항목 전체 자동 생성 (SC/CC 구분)
- 모든 셀 직접 편집 가능
- Excel / PDF(A3) 출력
- PWA 설치 지원 (오프라인 캐싱)

## GitHub Pages 배포 방법

### 1. 리포지토리 생성

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/<유저명>/pfmea-cp-pwa.git
git push -u origin main
```

### 2. GitHub Pages 활성화

1. Repository → **Settings** → **Pages**
2. Source: **GitHub Actions** 선택
3. 자동으로 `.github/workflows/deploy.yml` 실행됨
4. 배포 완료 후 URL: `https://<유저명>.github.io/pfmea-cp-pwa/`

### 3. 앱 사용

1. 배포된 URL 접속
2. **API 키 입력**: Anthropic Console → API Keys → `sk-ant-api03-...` 입력
   - API 키는 브라우저 localStorage에만 저장 (서버 전송 없음)
3. 품번/품명/고객사/공장 입력
4. **공정 추가** → 도면 업로드 (PDF/JPG/PNG) → 공정명/기능 입력
5. **AI 분석 시작** → PFMEA + Control Plan 자동 생성
6. 셀 클릭하여 직접 편집
7. Excel / PDF 출력

## 파일 구조

```
pfmea-cp-pwa/
├── index.html          # 메인 앱 (단일 파일 SPA)
├── manifest.json       # PWA 매니페스트
├── sw.js               # Service Worker (오프라인 지원)
├── icons/
│   ├── icon-192.png    # PWA 아이콘
│   └── icon-512.png    # PWA 아이콘 (대형)
└── .github/
    └── workflows/
        └── deploy.yml  # 자동 배포
```

## 보안 참고

- Anthropic API 키는 브라우저 localStorage에 저장되며 서버로 전송되지 않습니다
- API 호출은 클라이언트에서 직접 Anthropic API로 이루어집니다
- 도면 이미지는 AI 분석 후 메모리에서 제거됩니다

## 기준 규격

- AIAG-VDA PFMEA 5th Edition (2019)
- IATF 16949:2016
- AIAG Control Plan Reference Manual
