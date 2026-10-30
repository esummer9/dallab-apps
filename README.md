# DALLAB Apps Guide & Privacy Policy (apps.dallab.kr)

[![Deploy Jekyll with GitHub Pages](https://github.com/dasanstudio/dallab-apps/actions/workflows/jekyll-gh-pages.yml/badge.svg)](https://github.com/dasanstudio/dallab-apps/actions/workflows/jekyll-gh-pages.yml)
[![Live Site](https://img.shields.io/badge/Site-apps.dallab.kr-5967c8)](https://apps.dallab.kr)

**DALLAB**에서 개발·배포하는 안드로이드 애플리케이션 및 구글 크롬 확장 프로그램의 공식 **사용 가이드**와 스토어(Google Play, Chrome Web Store) 심사 필수 규정인 **개인정보 처리방침(Privacy Policy)**을 제공하는 GitHub Pages 정적 웹사이트 프로젝트입니다.

---

## 🌐 서비스 개요

- **도메인**: [https://apps.dallab.kr](https://apps.dallab.kr) (GitHub Pages + CNAME 연동)
- **목적**: 
  - 각 앱 및 확장 프로그램 사용 안내 및 가이드 허브
  - Google Play Console 및 Chrome 웹 스토어 심사 등록용 공식 개인정보 처리방침 호스팅
  - 버전별 정책 이력 아카이빙

---

## 📱 호스팅 중인 서비스 목록

### 1. 안드로이드 앱 (Android Apps)

| 앱 명칭 | 설명 | 경로 |
| :--- | :--- | :--- |
| **오믹스 (Ohmics)** | 저항 색상 코드 계산 및 표준 저항값/오차 범위를 확인하는 전자 엔지니어용 도구 | [`/omics/`](/omics/) |
| **내손안의 법구경 (Dhammapada)** | 법구경 구절 읽기, TTS 음성 듣기 및 일일 알림 서비스 | [`/dhammapada/`](/dhammapada/) |
| **투캘린더 (TwoCalendar)** | 양력/음력 달력, 일정 및 기념일 관리, Firebase 백업/복원 지원 달력 | [`/twocalendar/`](/twocalendar/) |

### 2. 크롬 확장 프로그램 (Chrome Extensions)

| 확장 프로그램 명칭 | 설명 | 경로 |
| :--- | :--- | :--- |
| **K-Calendar** | 공공데이터 공휴일·기상청 날씨 조회 및 날짜 포맷 클립보드 복사 사이드패널 도구 | [`/chrome/k-calendar/`](/chrome/k-calendar/) |
| **K-Work Memo** | 로컬 우선(Local-first) 보안 메모, 현재 탭 URL 캡처 및 PIN 잠금 지원 사이드패널 메모장 | [`/chrome/k-work-memo/`](/chrome/k-work-memo/) |

---

## 🛠 기술 스택 및 구조

- **정적 사이트 빌더**: Jekyll (GitHub Pages 기본 지원 런타임)
- **CI/CD**: GitHub Actions ([`.github/workflows/jekyll-gh-pages.yml`](.github/workflows/jekyll-gh-pages.yml))
  - `main` 브랜치에 변경 사항이 푸시되면 Jekyll 빌드가 실행되어 `_site`로 산출된 후 GitHub Pages로 자동 배포됩니다.
- **스타일/템플릿**:
  - `_layouts/default.html`: 전체 페이지 공통 템플릿 (반응형 레이아웃, 모바일 친화 뷰포트 지원)
  - `assets/css/style.css`: 사용자 친화적 카드 UI 및 디자인 스타일시트
  - `assets/images/`: 각 앱 아이콘 및 썸네일 리소스

---

## 📂 디렉토리 구조

```text
dallab-apps/
├── .github/
│   └── workflows/
│       └── jekyll-gh-pages.yml   # GitHub Actions Jekyll 빌드 & 배포 워크플로우
├── _layouts/
│   └── default.html              # 공통 HTML 레이아웃
├── agents/
│   ├── agents.md                 # 타 프로젝트 연동 및 AI 에이전트 참조 가이드 (/agents/)
│   └── commits.md                # Git 커밋 메시지 규약 (/agents/commits/)
├── assets/
│   ├── css/
│   │   └── style.css             # 스타일시트 (카드 UI 등)
│   └── images/                   # 앱 아이콘 및 이미지 리소스
├── chrome/
│   ├── k-calendar/               # K-Calendar 개인정보 처리방침
│   └── k-work-memo/              # K-Work Memo 개인정보 처리방침
├── dhammapada/                   # 내손안의 법구경 안내 및 처리방침
├── omics/                        # 오믹스 안내 및 처리방침 (버전별 히스토리 포함)
│   └── versions/
├── twocalendar/                  # 투캘린더 안내 및 처리방침
├── CNAME                         # 커스텀 도메인 설정 (apps.dallab.kr)
├── index.md                      # 메인 페이지 (앱 목록 허브)
└── README.md                     # 프로젝트 안내 문서
```

---

## ✍️ 신규 앱 또는 정책 문서 추가 방법

새로운 앱이나 개인정보 처리방침을 추가할 때는 아래 단계를 따릅니다.

1. **디렉토리 생성 및 마크다운 파일 작성**:
   - 신규 앱의 경우 루트에 디렉토리(예: `myapp/`)를 생성하고 `index.md` 파일을 작성합니다.
   - 상단에 YAML Front Matter를 필수로 추가합니다:
     ```yaml
     ---
     layout: default
     title: "앱 이름 개인정보 처리방침"
     ---
     ```

2. **아이콘 리소스 추가 (선택)**:
   - `assets/images/` 디렉토리에 앱 아이콘 또는 썸네일 이미지(SVG, WebP, PNG 등)를 저장합니다.

3. **메인 페이지([`index.md`](index.md))에 링크/카드 등록**:
   - `index.md` 파일에 카드 컴포넌트 또는 목록 항목을 추가합니다:
     ```html
     <div class="app-card">
       <img src="/assets/images/myapp.webp" alt="앱 아이콘" class="app-thumb">
       <div class="app-content">
         <h3 class="app-title blue">
           <a href="/myapp/">앱 이름 사용 가이드</a>
         </h3>
         <p class="app-desc">앱에 대한 간단한 설명을 입력합니다.</p>
       </div>
     </div>
     ```

4. **배포**:
   - `main` 브랜치에 커밋 및 푸시하면 GitHub Actions가 자동으로 빌드 및 배포를 완료합니다.

---

## 📬 문의

- **운영/개발**: DALLAB
- **문의 이메일**: `smartup.kr@gmail.com`
