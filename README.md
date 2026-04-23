# YouTube Shorts Success Analysis Dashboard

## 📋 프로젝트 개요

10개의 유튜브 쇼츠 영상을 분석하여 성공 패턴을 추출하고, 향후 콘텐츠 발굴을 위한 탐색 기준을 제시하는 인터랙티브 대시보드입니다.

## 📁 파일 구조

```
├── index.html                 # 🌟 독립형 HTML (이 파일만 브라우저에서 열면 됨)
├── source-code/              # 전체 소스 코드
│   ├── client/              # React 프론트엔드
│   ├── server/              # Express 백엔드
│   └── package.json         # 의존성
├── data/                     # 분석 데이터
│   ├── videos_data.json     # 10개 영상 메타데이터
│   ├── videos_data.csv      # CSV 형식 데이터
│   └── insights.json        # 공통 패턴 및 인사이트
└── dist/                     # 빌드된 배포 파일
```

## 🚀 빠른 시작

### 옵션 1: 독립형 HTML (권장 - 가장 간단함)
**index.html을 웹 브라우저에서 열기만 하면 됨** (인터넷 연결 필요 없음)

### 옵션 2: 로컬 개발 서버
```bash
cd source-code
npm install
npm run dev
```

### 옵션 3: 프로덕션 빌드
```bash
cd source-code
npm install
npm run build
npm run start
```

## 📊 주요 기능

- **홈 페이지**: 프로젝트 소개
- **분석 대시보드**: 개요/영상목록/패턴분석/인사이트 4개 탭
- **비디오 상세페이지**: 각 영상 분석 내용
- **차트 시각화**: 소재/감정/훅 패턴 분포

## 📈 분석 결과 요약

- **훅 패턴**: 5가지 (비교형, 의외성형, 극한상황형, 설명형, 유머형)
- **감정 포인트**: 놀라움(4회), 충격·이해·웃음·공감(각 3회)
- **소재 분포**: K-pop 산업 분석 40%, 기타 60%
- **시의성**: 90% 낮음 (시간 무관 콘텐츠)
- **반복 가능성**: 100% 높음

## 🔧 기술 스택

- React 19, TypeScript, Tailwind CSS 4, Recharts
- shadcn/ui, Vite, Express

---

**마지막 업데이트**: 2026-04-23
