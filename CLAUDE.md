# AI Blog Scraper

> AI는 펜이고, 당신이 작가입니다.

네이버 블로그 스크래핑 및 분석 도구입니다.
블로그 포스트를 수집하고, 글을 분석하여 인사이트를 얻을 수 있습니다.

## 프로젝트 구조

```
├── main.py                      # 메인 스크래퍼 실행
├── config/                      # 설정 파일
│   ├── blogs.json               # 블로그 목록
│   └── naver_topics.json        # 네이버 주제 카테고리
├── scraper/                     # 스크래핑 모듈
│   ├── blog_scraper.py          # 블로그 포스트 수집
│   └── monthly_blog.py          # 이달의 블로그 수집
├── utils/                       # 유틸리티 함수
├── output/                      # 스크래핑 결과
│   └── {blog_id}/               # 각 블로그 ID별 폴더
├── docs/                        # 문서
│   ├── clips/                   # 클리핑된 블로그 글
│   └── reviews/                 # 블로그 리뷰 저장
└── .claude/commands/            # 슬래시 명령어
```

## Commands (슬래시 명령어)

### 수집 및 분석

| 명령어 | 설명 | 예시 |
|--------|------|------|
| `/search` | 블로그 스크래핑 | `/search zeroenter 5` |
| `/review` | 블로그 분석 리뷰 (특정글) | `/review 비움 00` |
| `/monthly` | 이달의 블로그 수집 | `/monthly add` |

### 블로거 관리

| 명령어 | 설명 | 예시 |
|--------|------|------|
| `/bloggers` | 블로거 목록 관리 | `/bloggers *` (즐겨찾기) |
| `/bloggers add` | 새 블로그 추가 | `/bloggers add zeroenter` |

### 저장

| 명령어 | 설명 | 예시 |
|--------|------|------|
| `/save` | 블로그 리뷰 저장 | `/save` |
| `/clip` | 블로그 글 클리핑 | `/clip list` |

---

## 사전 준비 (처음 사용 시)

### 방법 1: 자동 설치 (권장)

| OS | 파일 | 실행 방법 |
|----|------|-----------|
| Windows | `setup.bat` | 더블클릭 |
| Mac/Linux | `setup.sh` | 터미널에서 `bash setup.sh` |

- Python 없으면 → 자동 설치 (Windows: winget, Mac: Homebrew)
- pip 업그레이드
- 필수 패키지 설치
- Playwright 설치 (선택)

> Windows 자동 설치 실패 시: `setup.bat` 우클릭 → "관리자 권한으로 실행"

### 방법 2: 수동 설치

1. **Python 설치**: https://www.python.org/downloads/
   - 설치 시 "Add Python to PATH" 반드시 체크!

2. **패키지 설치**:
```bash
pip install -r requirements.txt
```

3. **Playwright 설치** (이달의 블로그 기능 사용 시):
```bash
playwright install chromium
```

### 방법 3: Claude Code에서 `/setup`

```
/setup          # 환경 점검 + 자동 설치
/setup check    # 점검만 (설치 안 함)
```

---

## 상세 사용법

### /search {blog_id} {count}
네이버 블로그 스크래퍼 실행. 별명/블로그명 자동 매칭 지원.

```
/search 980207        # 최신 1개 포스트
/search zeroenter 5   # 5개 포스트
/search 리리 3        # 별명 매칭 → ari_school
```

### /review {별명/ID} {포스트번호}
수집된 데이터로 블로그 분석. 직전 `/search` 결과를 자동 연결.

```
/review                # 직전 search 결과 자동 분석
/review 비움 00        # hhey0510의 00번 포스트 분석
/review 비움 5         # hhey0510 포스트 5개 목록 표시
/review 리리 댓글      # 최신 글 댓글만 바로 출력
```

**특정글분석**: 8개 섹션 (구조분석, 강점, 약점, SEO, 독자반응, 종합평가, 총평, 추천댓글)

### /monthly
네이버 "이달의 블로그" 자동 수집.
- `/monthly` - 수집 실행
- `/monthly add` - 수집 후 blogs.json에 추가
- `/monthly list` - 최근 수집 결과 보기

### /bloggers
블로그 목록 관리.
- `*` - 즐겨찾기만 보기
- `#주제` - 주제 필터링
- `@ID` - ID로 검색
- `+ID` / `-ID` - 즐겨찾기 추가/제거

### /save
분석한 블로그 글을 `docs/reviews/`에 저장.

### /clip
읽은 블로그 글을 `docs/clips/`에 클리핑.

---

## 파일 저장 위치

| 파일 유형 | 저장 위치 |
|-----------|-----------|
| 스크래핑 결과 | `output/{blog_id}/` |
| 블로그 리뷰 | `docs/reviews/` |
| 클리핑 글 | `docs/clips/` |

## 분석 참조 파일

| 파일 | 용도 |
|------|------|
| `output/{blog_id}/{blog_id}_summary_*.json` | 포스트 목록 요약 |
| `output/{blog_id}/{blog_id}_posts_*.json` | 포스트 본문 내용 |

---

> 💡 **더 많은 기능이 필요하신가요?**
>
> - **전체분석** (12개 항목 종합 분석)
> - **페르소나** (나만의 글쓰기 스타일)
> - **AI 글쓰기** (페르소나 기반 글 작성)
> - **키워드 분석** (검색 최적화)
>
> AI Blog Writer 교육 과정에서 만나보세요!
