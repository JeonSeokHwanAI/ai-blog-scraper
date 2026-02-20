# AI Blog Scraper

> AI는 펜이고, 당신이 작가입니다.

네이버 블로그 스크래핑 및 분석 도구입니다.
블로그 포스트를 수집하고, AI로 분석하여 인사이트를 얻을 수 있습니다.

## 주요 기능

- **블로그 스크래핑** - 네이버 블로그 포스트 자동 수집
- **블로그 분석** - 포스트 구조, 강점/약점, SEO 분석
- **이달의 블로그** - 네이버 추천 블로그 자동 수집
- **클리핑** - 참고할 글을 마크다운으로 저장

## 설치 방법

### 1. 요구 사항

- Python 3.9 이상
- Claude Code (Claude Desktop)

### 2. 의존성 설치

```bash
pip install -r requirements.txt
```

### 3. Playwright 설치 (이달의 블로그 기능 사용 시)

```bash
playwright install chromium
```

## 사용 방법

Claude Code에서 슬래시 명령어로 실행합니다.

### 블로그 스크래핑

```
/search <블로그ID> <수량>
```

예시:
- `/search zeroenter 5` - zeroenter 블로그의 최신 5개 포스트 수집

### 블로그 분석

```
/review <블로그ID> <포스트번호>
```

예시:
- `/review zeroenter 00` - 00번 포스트 분석
- `/review zeroenter 댓글` - 최신 글 추천 댓글 생성

### 블로거 관리

```
/bloggers <명령>
```

예시:
- `/bloggers all` - 전체 목록
- `/bloggers add <ID>` - 새 블로그 추가
- `/bloggers #IT` - IT 주제 필터

### 이달의 블로그

```
/monthly
```

## 프로젝트 구조

```
├── main.py                 # 메인 스크래퍼
├── CLAUDE.md               # Claude Code 설정
├── requirements.txt        # Python 의존성
├── config/
│   ├── blogs.json          # 블로그 목록
│   └── naver_topics.json   # 주제 카테고리
├── scraper/
│   ├── blog_scraper.py     # 블로그 스크래퍼
│   ├── parser.py           # HTML 파서
│   └── monthly_blog.py     # 이달의 블로그
├── utils/
│   ├── helpers.py          # 유틸리티
│   └── bloggers_cli.py     # 블로거 CLI
├── output/                 # 스크래핑 결과
└── docs/
    ├── reviews/            # 분석 리뷰
    └── clips/              # 클리핑
```

## 분석 결과

`/review` 명령으로 다음 8가지 섹션을 분석합니다:

1. **콘텐츠 구조 분석** - 글의 구성 요소 평가
2. **강점 4가지** - 글의 장점
3. **약점 및 개선점** - 보완할 부분
4. **SEO 분석** - 검색 최적화 제안
5. **독자 반응 예측** - 예상 반응
6. **종합 평가** - 점수화된 평가
7. **총평** - 요약
8. **추천 댓글** - 작성자에게 남길 댓글

## 더 많은 기능

전체분석, 페르소나 글쓰기, 키워드 분석 등 고급 기능은
AI Blog Writer 교육 과정에서 제공됩니다.

---

Made with [Claude Code](https://claude.ai/code)

## License

MIT License
