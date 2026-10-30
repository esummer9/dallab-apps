# agents.md

이 프로젝트(`dallab-apps`)는 **DALLAB**에서 개발·배포하는 안드로이드 애플리케이션 및 크롬 확장 프로그램의 공식 사용 가이드와 개인정보 처리방침(Privacy Policy)을 호스팅하는 GitHub Pages(Jekyll) 정적 웹사이트입니다.

---

## 1. 프로젝트 구조 (Project Structure)
- `_layouts/default.html`: 전체 페이지 공통 Jekyll HTML 레이아웃 (반응형 뷰포트 및 스타일 포함)
- `assets/css/style.css`: 사이트 스타일시트 (카드 컴포넌트, 컬러 테마 등)
- `assets/images/`: 앱 아이콘 및 이미지 리소스
- `index.md`: 메인 허브 페이지 (등록된 앱 및 확장 프로그램 목록 카드)
- `agents/`:
  - `agents.md`: 타 프로젝트 연동 및 AI 에이전트 참조 가이드 ([웹 주소: https://apps.dallab.kr/agents/](https://apps.dallab.kr/agents/))
  - `commits.md`: Git 커밋 메시지 규약 가이드 ([웹 주소: https://apps.dallab.kr/agents/commits/](https://apps.dallab.kr/agents/commits/))
- `CNAME`: 커스텀 도메인 매핑 (`apps.dallab.kr`)
- `.github/workflows/jekyll-gh-pages.yml`: GitHub Actions 자동 빌드 및 배포 파이프라인

---

## 2. AI 에이전트를 위한 작업 지침 (Guidelines for AI Agents)
1. **GitHub Pages & Jekyll 환경**: 마크다운 파일 작성 시 상단에 반드시 Jekyll Front Matter (`layout: default`, `title`, 필요시 `permalink`)를 포함해야 합니다.
2. **신규 앱/가이드 등록 시**:
   - 해당 앱 디렉토리 생성 후 `index.md` 작성
   - `assets/images/`에 아이콘 리소스 배치
   - 메인 허브([`index.md`](index.md))에 앱 카드 컴포넌트 등록
3. **가이드 참조**:
   - 타 프로젝트 연동 상세 절차는 [에이전트 연동 가이드(https://apps.dallab.kr/agents/)](https://apps.dallab.kr/agents/)를 참조합니다.
4. **Git 커밋 규약 준수**:
   - 커밋 작성 시 공식 규약인 **[Git 커밋 메시지 규약(https://apps.dallab.kr/agents/commits/)](https://apps.dallab.kr/agents/commits/)**을 반드시 준수합니다.
5. **개발자 컨펌 필수 원칙**:
   - AI 에이전트는 커밋(`git commit`)을 수행하기 전, 작성된 커밋 메시지를 개발자에게 사전에 반드시 제시하고 **최종 승인(컨펌)을 받은 후** 커밋을 진행해야 합니다.
6. **단축 명령어 ("커푸") 지원**:
   - 사용자가 **"커푸"**라고 요청하면 이는 **'커밋 & 푸시 (Git Commit & Push)'**를 의미합니다. 변경된 파일들을 스테이징(`git add`)하고, 규약에 맞는 커밋 메시지를 개발자에게 확인받은 뒤 커밋 및 푸시(`git push`)를 진행합니다.

---

## 3. Git 커밋 메시지 규약 (Conventional Commits)

> **공식 규약 웹 문서**: [https://apps.dallab.kr/agents/commits/](https://apps.dallab.kr/agents/commits/)

### 커밋 메시지 형식
```text
<태그> (<기능, 메뉴, 카테고리>): <작업 내용>
```

*예시:*
- `feat (저항 계산기): 5밴드 색상 코드 계산 기능 추가`
- `fix (음력 달력): 윤달 계산 시 날짜 밀림 현상 수정`
- `docs (가이드): 신규 앱 사용 가이드 추가`
- `docs (개인정보처리방침): 오믹스 v1.1 개인정보 처리방침 문서 추가`
- `chore (CI/CD): Jekyll GitHub Actions 배포 워크플로우 설정 갱신`
- `test (기능, 메뉴, 카테고리): 공휴일 API 응답 파싱 단위 테스트 추가`

### 태그 목록
| 태그 | 의미 |
| :--- | :--- |
| **init** | 초기화 |
| **feat** | 새로운 기능 추가 |
| **fix** | 버그 수정 |
| **style** | 코드 포맷 변경, 세미콜론 누락 등 (코드 로직 변경 없음) |
| **refactor** | 코드 리팩토링 (기능 변화 없이 코드 구조 개선) |
| **test** | 테스트 코드 추가 및 리팩토링 |
| **chore** | 빌드 업무, 패키지 매니저 설정 등 기타 작업 |
| **perf** | 성능 개선 |
| **docs** | README.md 수정, 새로운 도움말 .md 파일 추가, API 문서 업데이트, 코드 내 주석 추가 등 |

### 태그 선택 판단 기준
- **시스템에 기능을 더하는 메시지** ➔ `feat`
- **설명이나 주석 목적의 메시지** ➔ `docs`
- **운영 관리를 위한 설정/기타 작업** ➔ `chore`
- **코드의 로직에 영향을 주지 않고, 개발자나 운영자가 참고하기 위한 주석(Comment)이나 설명 문구만 추가한 것** ➔ `docs`

