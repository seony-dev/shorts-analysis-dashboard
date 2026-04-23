# YouTube Shorts Success Analysis Dashboard

## 📋 프로젝트 개요

유튜브 쇼츠 영상을 분석하여 성공 패턴을 추출하고, 향후 콘텐츠 발굴을 위한 탐색 기준을 제시하는 인터랙티브 대시보드입니다.

🔗 **라이브**: https://seony-dev.github.io/shorts-analysis-dashboard/

## 📁 파일 구조

```
├── index.html              # 엔트리 — CSS/JS 로드 + 서브패스 라우팅 처리
├── 404.html                # spa-github-pages 리다이렉트 스텁 (서브라우트 새로고침 대응)
├── css/
│   └── styles.css          # Tailwind 번들
├── js/
│   └── app.js              # React 앱 번들 (wouter 라우터 패치 포함)
├── data/
│   ├── videos_data.json    # 영상 메타데이터 ★ 팀원 업데이트 대상
│   ├── videos_data.csv     # CSV 미러
│   └── insights.json       # 집계 인사이트 ★ 팀원 업데이트 대상
├── .gitignore
└── README.md
```

> 개발 원본(`source-code/`, `dist/`)은 `.gitignore` 처리돼 레포에는 포함되지 않습니다.

## 🚀 업데이트 방법

### 영상/인사이트 추가·수정

`data/videos_data.json` 과 `data/insights.json` 만 수정하면 됩니다. push 하면 1-2분 내 자동 배포됩니다.

```bash
# 수정 후
git add data/
git commit -m "영상 N개 추가"
git push
```

### 팀원 제출 포맷

팀원이 새 영상 분석 결과를 넘겨줄 때 아래 포맷으로 받으면 그대로 JSON 에 넣기 편합니다.

```
번호:
링크:
영상_제목:
채널명:
조회수:
업로드_날짜:
영상_길이:
소재_유형:
첫_3초_훅:
감정_자극_포인트: (복수 가능)
시의성: 낮음 / 중간 / 높음
반복_가능성: 낮음 / 중간 / 높음
주요_분석_내용:
```

위 포맷으로 받은 내용을 Claude/Manus 에게 "이거 3번 영상으로 넣어줘" 라고 주면 JSON 구조 맞춰 삽입 + `insights.json` 의 집계(소재 분포, 감정 포인트 카운트 등)도 자동 업데이트됩니다.

## 📊 대시보드 구성

- **홈**: 프로젝트 소개
- **분석 대시보드**: 개요 / 영상목록 / 패턴분석 / 인사이트 4개 탭
- **영상 상세**: 개별 영상 분석 내용 + 차트
- **차트 시각화**: 소재·감정·훅 패턴 분포

## 🔧 기술 스택

- **프론트**: React 19, TypeScript, Tailwind CSS 4, Recharts, shadcn/ui
- **라우팅**: wouter
- **빌드**: Vite (원본 개발 코드는 별도 보관)
- **호스팅**: GitHub Pages

## 🛠️ GitHub Pages 서브패스 대응 (기술 메모)

프로젝트 레포라 `/shorts-analysis-dashboard/` 서브패스에서 서빙됩니다. 다음 두 가지 처리가 들어가 있어요:

1. **`index.html` 의 `__getPath__`**: `location.pathname` 에서 베이스 경로를 벗겨서 wouter 에 전달
2. **`404.html` 리다이렉트**: 서브라우트 직접 접속 시 `/?/path` 형태로 인코딩해 `index.html` 로 보내고, `index.html` 이 다시 디코드해서 원래 경로로 `replaceState`

앱 로직(라우트 등)을 수정해서 `js/app.js` 를 다시 빌드·교체할 경우, 번들에서 `RP=()=>location.pathname` 을 `RP=()=>window.__getPath__()` 로 재패치해야 합니다.

---

**마지막 업데이트**: 2026-04-23
