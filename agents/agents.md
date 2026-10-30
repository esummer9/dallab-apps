---
layout: default
title: "DALLAB Apps Agent Guide"
permalink: /agents/
---

# DALLAB Apps Agent Guide (`agents.md`)

이 문서는 다른 프로젝트(안드로이드 앱, 크롬 확장 프로그램, 웹 서비스 등)를 개발하거나 릴리스할 때, **DALLAB 통합 안내 웹사이트(`apps.dallab.kr`)에 사용 가이드 및 개인정보 처리방침(Privacy Policy)을 연동·등록·갱신하기 위한 에이전트 참조 가이드**입니다.

- **온라인 웹 문서 주소**: [https://apps.dallab.kr/agents/](https://apps.dallab.kr/agents/)

---

## 1. 프로젝트 역할 및 연동 목적

- **저장소 위치**: `dallab-apps` (`https://github.com/dasanstudio/dallab-apps`)
- **운영 사이트**: [https://apps.dallab.kr](https://apps.dallab.kr) (GitHub Pages + Jekyll)
- **주요 목적**:
  1. Google Play Console 앱 등록 심사용 공식 개인정보 처리방침 URL 제공
  2. Chrome Web Store 확장 프로그램 등록 심사용 개인정보 처리방침 URL 제공
  3. DALLAB 브랜드 서비스의 사용자 가이드 및 랜딩 페이지 허브 역할
  4. 개정 이력(버전별 개인정보 처리방침) 관리

---

## 2. URL 및 디렉토리 명명 규칙

| 서비스 유형 | 디렉토리 경로 | 웹 사이트 접근 URL |
| :--- | :--- | :--- |
| **안드로이드 앱** | `/{app-name}/index.md` | `https://apps.dallab.kr/{app-name}/` |
| **크롬 확장 프로그램** | `/chrome/{extension-name}/index.md` | `https://apps.dallab.kr/chrome/{extension-name}/` |
| **버전별 아카이브** | `/{app-name}/versions/{version}/index.md` | `https://apps.dallab.kr/{app-name}/versions/{version}/` |
| **에이전트 연동 가이드** | `/agents/agents.md` | `https://apps.dallab.kr/agents/` |
| **커밋 메시지 규약** | `/agents/commits.md` | `https://apps.dallab.kr/agents/commits/` |

> [!TIP]
> - 경로 이름(`{app-name}`, `{extension-name}`)은 소문자, 하이픈(`-`) 조합을 권장합니다.
> - 크롬 확장 프로그램은 `/chrome/` 하위에 위치시키고 필요 시 `permalink: /chrome/{extension-name}/`을 Front Matter에 명시합니다.

---

## 3. 다른 프로젝트에서 작업 시 수행 절차 (Agent Action Steps)

다른 앱 프로젝트에서 신규 출시 또는 개인정보 처리방침 갱신이 필요할 때, 에이전트는 본 저장소(`dallab-apps`)에서 아래 단계를 순서대로 수행합니다.

### Step 1. 문서 파일 생성
- 해당 앱 디렉토리를 생성하고 `index.md` 파일을 작성합니다.
- 반드시 상단에 Jekyll Front Matter를 포함해야 합니다.
  ```yaml
  ---
  layout: default
  title: "앱 이름(영문명) 개인정보 처리방침 v1.0"
  ---
  ```

### Step 2. 필수 고지 항목 작성 (체크리스트)
각 스토어 정책을 준수하기 위해 아래 항목들이 반드시 포함되어야 합니다:

1. **개인정보 수집 및 처리 현황**:
   - 회원가입 유무, 개인정보 수집 여부 (일반적으로 "수집 항목 없음" 또는 "로컬 저장만 수행")
   - 기기 내부 저장소(SQLite, LocalStorage, Chrome Storage) 활용 범위
2. **앱 접근 권한 명시 (안드로이드/크롬)**:
   - 요청하는 모든 권한(Permission)과 사용 목적을 표(`Table`) 형식으로 정리
3. **제3자 서비스 및 SDK 사용 현황**:
   - Google AdMob, Firebase, 공공데이터 API 등 사용 중인 외부 서비스 명시 및 해당 서비스의 개인정보 처리방침 링크 포함
4. **데이터 파기 절차**:
   - 앱 삭제 또는 데이터 초기화 시 기기 내 로컬 데이터 즉시 파기 명시
5. **문의처 및 시행 일자**:
   - 담당자/개발자 이메일 (`smartup.kr@gmail.com` 등)
   - 시행 일자 (또는 최종 수정일자)
6. *(크롬 확장의 경우)*:
   - Google Chrome 웹 스토어 심사를 위해 국문 및 **영문(Privacy Policy)** 내용을 동일 파일 내 하단에 함께 제공

### Step 3. 앱 아이콘 에셋 등록
- 앱 아이콘 또는 대표 이미지를 `assets/images/` 폴더에 추가합니다.
  - 파일 형식: `.svg`, `.webp`, `.png`
  - 파일명 예시: `assets/images/{app-name}.webp`

### Step 4. 메인 허브(`index.md`) 카드 등록
- 루트의 [`index.md`](file:///d:/Users/workspace/apps/dallab-apps/index.md)에 신규 앱 카드를 추가합니다.

```html
<div class="app-card">
  <img src="/assets/images/{app-name}.webp" alt="{앱 이름} 아이콘" class="app-thumb">
  <div class="app-content">
    <h3 class="app-title blue">
      <a href="/{app-name}/">{앱 이름} 사용 가이드</a>
    </h3>
    <p class="app-desc">
      {앱에 대한 한 줄 설명 요약}
    </p>
  </div>
</div>
```
*(기존 카드의 지그재그 배치를 맞추려면 번갈아가며 `<div class="app-card reverse">` 적용)*

### Step 5. 변경 사항 커밋 및 자동 배포
- Git 변경 사항을 `main` 브랜치에 커밋 및 푸시합니다.
  - 커밋 메시지는 [Git 커밋 메시지 규약](/agents/commits/)을 준수하여 `<태그> (<기능, 메뉴, 카테고리>): <작업 내용>` 형식으로 작성합니다. (예: `docs (가이드): 신규 앱 사용 가이드 추가`)
  - **개발자 컨펌 필수**: Git 커밋 명령(`git commit`)을 실행하기 전에, 에이전트는 작성한 커밋 메시지를 개발자에게 사전에 보여주고 **항상 컨펌(승인)을 받은 후** 커밋을 진행해야 합니다.
- GitHub Actions 워크플로우가 자동으로 실행되어 수 분 내에 `https://apps.dallab.kr`에 반영됩니다.

---

## 4. 정책 변경 및 버전 관리 가이드

개인정보 처리방침이 개정(v1.0 -> v1.1 등)되는 경우:
1. 기존 문서를 `/{app-name}/versions/{old-version}/index.md`로 이동 또는 복사하여 보존합니다.
2. 현재 `/{app-name}/index.md`에 새로운 정책을 작성하고 시행 일자를 최신화합니다.
3. 문서 하단에 `## 버전별 개인정보 처리방침` 섹션을 두고 이전 버전 링크를 유지합니다.

---

## 5. 공통 문의처 및 기본 정보

- **사이트 기본 템플릿**: `_layouts/default.html`
- **스타일시트**: `assets/css/style.css`
- **기본 개발자 이메일**: `smartup.kr@gmail.com`
- **커스텀 도메인 설정 파일**: `CNAME` (`apps.dallab.kr`)
