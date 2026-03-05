![header](https://capsule-render.vercel.app/api?type=waving&color=auto&height=300&text=OOTD's%20Github&desc=Development%20Log&fontAlign=63&Desc&descAlign=83)

# 후쿠부쿠로 (Fukubukuro) 🎁

> **AI 기반 가상 피팅 및 패션 이커머스 플랫폼**

사용자의 이미지를 활용한 AI 가상 피팅(Virtual Try-On), 패션 분석 라벨링과 BGM 추천, 사주 분석, 비디오 생성 서비스까지 경험할 수 있는 혁신적인 이커머스 데스크톱 서비스입니다.

---

## 📋 프로젝트 소개

후쿠부쿠로(Fukubukuro)는 일본어로 '服袋(옷주머니)'를 의미하며, 온라인 쇼핑의 불확실성을 해소하고 사용자에게 흥미와 색다른 온라인 쇼핑 경험을 선사하는 것을 목표로 합니다.

### 🎯 핵심 가치

- **가상 피팅**: FastFit AI 모델을 활용한 전신 실시간 가상 착용 체험
- **AI 융합 콘텐츠**: 패션 사주, OOTD BGM 리스트, 착장 기반 비디오 생성 등 독창적인 기능
- **통합 파이프라인**: Crawler + Backend + AI Server의 유기적인 연동 파이프라인 완성

---

## ✨ 주요 기능 (Key Features)

### 1️⃣ 쇼핑몰 코어 시스템

- **인증/인가**: Naver OAuth 2.0 및 Spring Security 기반의 소셜 로그인
- **마켓 기능**: 상품 검색, 상품 상세 조회, 위시리스트, 장바구니
- **주문 및 결제**: Toss Payments API(테스트 연동)를 활용한 주문 결제
- **마이페이지**: 프로필/치수/배송지 관리, 구매 및 토큰 충전 내역 등

### 2️⃣ AI Labs 🎯

> **총 3개의 파이프라인으로 구성된 핵심 체험 기능입니다.**

- **AI 가상 피팅 (FastFit)**
  - 단일 및 다중 아이템 피팅 (상·하의 개별 피팅 등)
  - 원활한 합성을 위한 이미지 배경 제거(RMBG) 자체 지원
- **AI 비디오 생성 (Veo 3.1)**
  - 피팅 결과를 바탕으로 한 패션 착장 전환 영상(Image-to-Video) 제작
- **AI 패션 분석 & BGM 추천 (Gemini)**
  - 의상 스타일에 리드미컬하게 어울리는 Spotify 음악 추천
- **AI 사주 분석 (Gemini)**
  - 생년월일과 패션 취향 매칭 기반 행운의 컬러/아이템 제공

### 3️⃣ 토큰 크레딧 시스템 (수익화 시나리오)

- **Toss Payments**를 통한 자체 토큰 충전
- 피팅(50), 룩 분석(30), 사주(20) 등 기능 호출당 AI 추론 비용으로 토큰 차감 설계

### 4️⃣ 데이터 하이브리드 자동 수집

- **Playwright 기반 Crawler**: 무신사 및 29CM 크롤링 API 구축
- 실시간으로 최신 상품 및 랭킹 데이터를 가져와 내부 DB에 동기화 완료

---

## 🛠️ 기술 스택 (Tech Stack)

### Backend

| 기술                            | 설명                             |
| ------------------------------- | -------------------------------- |
| **Spring Boot 3.5.9**           | 백엔드 메인 프레임워크           |
| **Java 21**                     | 런타임 환경                      |
| **MySQL 8.x + JPA**             | 관계형 DB 메타데이터 관리 및 ORM |
| **Spring Security 6**           | 인증 인가 처리                   |
| **Thymeleaf**                   | 동적 뷰(View) 렌더링             |
| **Toss Payments / Naver OAuth** | 결제 시스템 및 소셜 승인 연동    |

### AI Server

| 기술                      | 설명                                     |
| ------------------------- | ---------------------------------------- |
| **FastAPI**               | 백엔드와 통신하는 추론 서빙 API 서버     |
| **Python 3.10+**          | 베이스 런타임                            |
| **FastFit**               | Virtual Try-On 딥러닝 코어 모델          |
| **Gemini 2.5 Flash 우선** | 멀티모달 라벨링 / 사주 분석              |
| **Veo 3.1**               | 이미지 기반 비디오 생성 (Image-to-Video) |

### Crawler

| 기술             | 설명                                                  |
| ---------------- | ----------------------------------------------------- |
| **FastAPI**      | 크롤링 로직 분리 서빙                                 |
| **Python 3.10+** | 스크립트 작성 언어                                    |
| **Playwright**   | 동적 렌더링 요소를 수집하기 위한 브라우저 자동화 도구 |

---

## 📁 프로젝트 구조 요약

전체 시스템은 유연성을 위해 서비스별 리포지토리(디렉터리)를 분리하여 운영 중입니다.

```
fukubukuro/
├── backend/                      # Spring Boot 백엔드 (Port 9999)
├── AI/
│   ├── models/                   # AI 모델 Weights
│   └── server/
│       ├── fastfit/              # 피팅 API (Port 8000)
│       ├── gemini/               # 분석/BGM API (Port 8002)
│       └── veo3.1/               # 비디오 생성 API (Port 8001)
├── crawler/                      # 무신사/29CM 스크래핑 엔진 (Port 8888)
└── INSTALL.md                    # 통합 설치/실행 가이드
```

---

## 🚀 시작하기 (Getting Started)

프로젝트를 실행하려면 DB 테이블 덤프부터 여러 환경 변수 세팅 및 AI 모델 세팅 단계가 요구됩니다.
서버 각각의 설치 순서부터 도커 컴포즈(Docker Compose)를 활용한 쉬운 구동까지, **자세한 사항은 반드시 아래의 설치 가이드를 참조하세요.**

> 👉 **[통합 설치 가이드 (INSTALL.md) 이동](https://github.com/SCIT-OOTD/fukubukuro/blob/main/INSTALL.md)**

---

## 🤝 팀 협업 규칙 및 개발 가이드

본 프로젝트는 **GitHub Flow** 컨벤션을 기반으로 개발되었습니다.
자세한 코드 컨벤션과 Branch 전략, PR 규약은 [CONTRIBUTING.md](../backend/CONTRIBUTING.md) 페이지에 명시되어 있습니다.

---

## 👥 SCIT OOTD Team

- 🍀[이민재](https://github.com/kamillee0918) - **Team Leader** | 총괄기획 / AI (FastFit, Veo 3.1 기반) 구현 / 프로젝트 관리
- 🍀[김민기](https://github.com/mismyl) - **Member** | 프론트엔드 (UI/UX) / 애니메이션
- 🍀[김원형](https://github.com/davidking981218-rgb) - **Member** | 프론트엔드 (UI/UX) / AI (Gemini 기반)
- 🍀[배시원](https://github.com/SiwonBai) - **Member** | 백엔드 시스템 설계 / DB 및 인증 개발
- 🍀[장지웅](https://github.com/Uhnewly) - **Member** | 크롤링 스크립트 개발 / Data Pipeline 구성

---

**Made with ❤️ by SCIT OOTD Team**
