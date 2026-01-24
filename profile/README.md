![header](https://capsule-render.vercel.app/api?type=waving&color=auto&height=300&text=OOTD's%20Github&desc=Development%20Log&fontAlign=63&Desc&descAlign=83)

# 후쿠부쿠로 (Fukubukuro) 🎁

> **AI 기반 가상 피팅룸 온라인 쇼핑 플랫폼**

사용자의 전신 사진을 제공하면 AI 기반 가상 피팅을 통해 의류가 어떻게 보일지 미리 확인할 수 있는 데스크톱 쇼핑 서비스입니다.

---

## 📋 프로젝트 소개

후쿠부쿠로(Fukubukuro)는 일본어로 '服袋(옷주머니)'를 의미하며, 온라인 쇼핑의 불확실성을 해소하고 사용자에게 예상치 못한 즐거움을 선사하는 것을 목표로 합니다.

### 🎯 핵심 가치

- **가상 피팅**: FastFit AI 모델을 활용한 실시간 가상 착용 체험
- **개인화**: 사용자의 체형 정보에 기반한 맞춤형 쇼핑 경험
- **편리성**: 직관적인 UI/UX로 누구나 쉽게 사용 가능

### 🔄 사용자 흐름

```
체형 입력 → 상품 검색 → 상품 상세 → AI 피팅 요청 → 결과 확인 → 추천/랭킹
(신장/치수)  (키워드/필터)  (이미지/정보)  (AI 서버)    (전후 비교)  (조회수/좋아요)
```

---

## 🛠️ 기술 스택

### Backend

| 기술 | 버전 | 용도 |
|------|------|------|
| **Spring Boot** | 3.5.9 | 백엔드 프레임워크 |
| **Java** | 21 | 프로그래밍 언어 |
| **Thymeleaf** | - | 서버 사이드 템플릿 엔진 |
| **Spring Data JPA** | - | ORM |
| **MySQL** | 8.0+ | 데이터베이스 |
| **Spring Security** | - | 인증/인가 |
| **OAuth 2.0** | - | 카카오 소셜 로그인 |
| **Lombok** | - | 보일러플레이트 코드 감소 |

### AI Server

| 기술 | 버전 | 용도 |
|------|------|------|
| **FastAPI** | - | AI 추론 API 서버 |
| **Python** | 3.10+ | 프로그래밍 언어 |
| **FastFit** | - | Virtual Try-On AI 모델 |
| **PyTorch** | - | 딥러닝 프레임워크 |
| **CUDA** | 13.0+ | GPU 가속 |

### Crawler

| 기술 | 용도 |
|------|------|
| **Selenium** | 웹 스크래핑 |
| **Python** | 데이터 수집 및 전처리 |

### Frontend

| 기술 | 용도 |
|------|------|
| **HTML/CSS** | 마크업 및 스타일링 |
| **Vanilla JavaScript** | 클라이언트 사이드 로직 |
| **Thymeleaf** | 동적 뷰 렌더링 |

---

## 📁 프로젝트 구조

```
fukubukuro/
├── .github/                      # GitHub 설정 및 README
│   └── README.md                 # 📌 이 파일
│
├── backend/                      # Spring Boot 백엔드
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/ootd/
│   │   │   │   ├── controller/   # REST API 및 뷰 컨트롤러
│   │   │   │   ├── service/      # 비즈니스 로직
│   │   │   │   ├── repository/   # JPA 리포지토리
│   │   │   │   ├── entity/       # 엔티티 (JPA)
│   │   │   │   ├── dto/          # 데이터 전송 객체
│   │   │   │   └── config/       # 설정 (Security, OAuth)
│   │   │   └── resources/
│   │   │       ├── application.properties  # 애플리케이션 설정
│   │   │       ├── static/       # 정적 리소스 (CSS, JS, 이미지)
│   │   │       └── templates/    # Thymeleaf 템플릿
│   │   └── test/                 # 테스트 코드
│   ├── build.gradle              # Gradle 빌드 설정
│   ├── ootd.sql                  # 데이터베이스 스키마
│   ├── clothing_sample.sql       # 샘플 데이터
│   ├── uploads/                  # 사용자 업로드 이미지
│   └── CONTRIBUTING.md           # 팀 협업 규칙
│
├── AI/                           # FastFit AI 추론 서버
│   ├── server/
│   │   ├── app/
│   │   │   ├── main.py           # FastAPI 진입점
│   │   │   ├── config.py         # 환경 설정
│   │   │   ├── routers/          # API 라우터
│   │   │   │   ├── health.py     # 헬스체크 API
│   │   │   │   └── fitting.py    # 피팅 API
│   │   │   ├── services/
│   │   │   │   └── fastfit_service.py  # FastFit 추론 서비스
│   │   │   ├── schemas/          # Pydantic 스키마
│   │   │   └── utils/            # 유틸리티
│   │   ├── tests/                # 테스트 코드 (Mock/GPU)
│   │   ├── requirements.txt      # Python 의존성
│   │   ├── .env.example          # 환경 변수 템플릿
│   │   └── Dockerfile            # Docker 이미지 빌드
│   ├── models/                   # AI 모델 파일 (자동 다운로드)
│   ├── sample/                   # 샘플 이미지
│   └── README.md                 # AI 서버 가이드
│
├── crawler/                      # 웹 크롤러
│   ├── src/                      # 크롤링 소스 코드
│   ├── python/                   # Python 크롤러 스크립트
│   └── *.json                    # 크롤링 결과 데이터
│
└── github-practice/              # Git/GitHub 협업 연습
    ├── src/calculator/           # Java 계산기 예제
    ├── PROJECT_INTRO.md          # 프로젝트 소개
    ├── README.md                 # 협업 워크플로우 가이드
    └── CONTRIBUTING.md           # 커밋 및 PR 규칙
```

---

## ✨ 주요 기능

### 1️⃣ 회원 인증 시스템

- **카카오 OAuth 2.0** 소셜 로그인
- **Spring Security** 기반 인증/인가
- 세션 관리 및 보안 설정

### 2️⃣ 쇼핑몰 코어 기능

- 상품 목록 조회 및 검색
- 상품 상세 정보
- 장바구니 및 주문 처리
- 카테고리별 필터링

### 3️⃣ AI 가상 피팅 🎯

> **핵심 기능**: FastFit 모델을 활용한 Virtual Try-On

#### 피팅 API

| Method | Endpoint | 설명 |
|--------|----------|------|
| `POST` | `/api/v1/fitting/single` | 단일 아이템 피팅 |
| `POST` | `/api/v1/fitting/multi` | 다중 아이템 피팅 (최대 5개) |
| `POST` | `/api/v1/fitting/upload/multi` | 이미지 업로드 및 피팅 |

### 4️⃣ 검색 및 추천

- 키워드 기반 상품 검색
- 최근 검색어 관리
- 조회수 및 좋아요 기반 랭킹
- 개인화 추천 시스템 (구현 예정)

### 5️⃣ 데이터 수집

- Selenium 기반 웹 크롤러
- 의류 데이터 자동 수집
- JSON 형태로 데이터 저장

---

## 🚀 시작하기

### 사전 요구사항

#### Backend
- **JDK 21** 이상
- **MySQL** 8.0 이상
- **Gradle** 8.x

#### AI Server
- **Python** 3.10 이상
- **CUDA 지원 GPU** (VRAM 8GB 이상 권장)
- **Anaconda** (권장)

### Backend 실행

```bash
# 1. 저장소 클론
git clone <repository-url>
cd fukubukuro/backend

# 2. MySQL 데이터베이스 설정
mysql -u root -p < ootd.sql
mysql -u root -p < clothing_sample.sql

# 3. application.properties 설정
# - DB 연결 정보 수정
# - 카카오 OAuth 클라이언트 ID/Secret 설정

# 4. 애플리케이션 실행
./gradlew bootRun
```

접속: http://localhost:9999

### AI Server 실행

```bash
# 1. 가상환경 생성
cd fukubukuro/AI/server
conda create -n fastfit python=3.10
conda activate fastfit

# 2. PyTorch with CUDA 설치
pip install torch torchvision --index-url https://download.pytorch.org/whl/cu130

# 3. 의존성 설치
pip install -r requirements.txt
pip install easy-dwpose --no-dependencies

# 4. 환경 변수 설정
cp .env.example .env

# 5. 서버 실행
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

API 문서: http://localhost:8000/docs

---

## 🤝 팀 협업 규칙

본 프로젝트는 **GitHub Flow** 기반 협업 전략을 따릅니다.

### 커밋 컨벤션

**Angular JS Commit Convention** 준수

```
Type: Subject

예시:
- Feat: 로그인 API 구현
- Fix: 0으로 나누기 예외 처리 추가
- Docs: README 업데이트
- Refactor: 코드 리팩토링
- Design: CSS 스타일링 변경
```

### 브랜치 전략

- **main**: 배포 가능한 상태 유지
- **feat/기능명**: 기능 개발 브랜치
- **fix/버그명**: 버그 수정 브랜치

예시: `feat/12-login`, `fix/15-typo-correction`

### 네이밍 컨벤션

| 항목 | 규칙 | 예시 |
|------|------|------|
| Class/Component | PascalCase | `UserService`, `LoginButton` |
| Variable/Method | camelCase | `getUserList`, `isActive` |
| Constant | UPPER_SNAKE_CASE | `MAX_COUNT`, `API_URL` |
| Entity Class | PascalCase | `MemberEntity`, `Order` |
| DB Table | snake_case | `member_info`, `orders` |
| DB Column | snake_case | `created_at`, `user_id` |
| URL Endpoint | kebab-case | `/api/user-profiles` |

자세한 내용은 [CONTRIBUTING.md](../backend/CONTRIBUTING.md) 참조

---

## 📈 향후 계획

> [!NOTE]
> 아래 항목들은 현재 설계 중이거나 구현 예정인 기능들입니다.

### 1. ERD 설계

데이터베이스 스키마 및 ERD 다이어그램을 작성할 예정입니다. 주요 테이블:

- **users**: 사용자 정보
- **products**: 상품 정보
- **clothing_sample**: AI 피팅용 의류 샘플
- **fitting_results**: 피팅 결과 저장
- **orders**: 주문 정보
- **cart**: 장바구니

### 2. 프로젝트 전체 흐름도

사용자 시나리오별 상세 플로우차트를 작성할 예정입니다:

- 회원가입/로그인 플로우
- 상품 검색 및 필터링 플로우
- AI 피팅 요청 및 결과 처리 플로우
- 주문 및 결제 플로우

### 3. API 명세서

RESTful API 엔드포인트 상세 명세를 문서화할 예정입니다:

- Request/Response 스키마
- 에러 코드 정의
- 인증/인가 방식
- 페이지네이션 규칙

### 4. UI/UX 개선

- 반응형 디자인 적용
- 접근성(Accessibility) 향상
- 로딩/에러 상태 UI 개선
- 다국어 지원 (한국어/일본어)

### 5. 성능 최적화

- AI 추론 속도 개선
- 데이터베이스 인덱싱 최적화
- 이미지 캐싱 및 CDN 적용
- API 응답 시간 단축

### 6. 테스트 자동화

- 단위 테스트 (JUnit, pytest)
- 통합 테스트
- E2E 테스트
- CI/CD 파이프라인 구축

---

## 📚 참고 문서

- [FastFit AI 서버 가이드](../AI/README.md)
- [Git 협업 가이드](../github-practice/README.md)

---

## 🔗 관련 링크

- **OOTD - 프로젝트 링크**: [Google Drive](https://drive.google.com/drive/folders/1EzpK6uiY6iz1cTISduM1DPqirM5CmqGb)
- **OOTD - Notion 링크**: [Notion](https://www.notion.so/SCIT-48-2e35bcf44d6e8022a45cf7a4bebfd4e3)
- **FastFit**: [GitHub](https://github.com/Zheng-Chong/FastFit)
- **Spring Boot**: [공식 문서](https://spring.io/projects/spring-boot)
- **FastAPI**: [공식 문서](https://fastapi.tiangolo.com/)

---

## 👥 팀 구성

* 🍀[이민재](https://github.com/kamillee0918) - 팀장 | 총괄/AI/개발
* 🍀[김민기](https://github.com/mismyl) - 팀원 | 개발 (프론트)
* 🍀[김원형](https://github.com/davidking981218-rgb) - 팀원 | 개발 (프론트)
* 🍀[배시원](https://github.com/SiwonBai) - 팀원 | 개발 (백엔드)
* 🍀[장지웅](https://github.com/Uhnewly) - 팀원 | AI/개발 (크롤링)

---

**Made with ❤️ by SCIT OOTD Team**
