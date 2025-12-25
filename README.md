# Dummy – 예비 창업자를 위한 AI 기반 종합 금융 플랫폼

## 💡 프로젝트 소개

**Dummy**는 예비 창업자를 위한 AI 기반 종합 금융 플랫폼입니다.
맞춤형 대출 상품 추천, 상권 분석, 금융 상품 비교, 커뮤니티 등 다양한 금융 서비스를 제공합니다.

* **진행 기간** : 2025년 12월 29일 - 2025년 12월 26일
* **소개** : AI 기반 대출 추천, 상권 분석 지도, 예적금 상품 비교, 환율 정보, 커뮤니티, YouTube 금융 콘텐츠 등을 제공하는 웹 서비스

---

## ⚙ 팀 구성

|    이름   |           역할          |
| :-----: | :-------------------: |
| **김영진** | 백엔드, 프론트엔드, AI 대출 추천, 상권 분석 |
| **국민혁** | 백엔드, 프론트엔드, 금융 상품, 커뮤니티, UI/UX |

---

## 📊 업무 분담 (개발/기획)

|  이름 |                                    주요 담당 영역                                    |
| :----: | :-------------------------------------------------------------------------------: |
| 김영진 | **백엔드**: AI 대출 추천 시스템, RAG 구현, ChromaDB 연동 <br> **프론트엔드**: AI 챗봇 UI, 대출 설문 페이지 <br> **기타**: 상권 분석 로직, 지도 서비스 연동 | 
| 국민혁 | **백엔드**: 금융 상품 API, 커뮤니티 CRUD, 회원 관리 <br> **프론트엔드**: 메인 페이지, 상품 비교 UI, 커뮤니티 페이지 <br> **기타**: UI/UX 디자인, 환율 차트 구현 |

> **Note**: 각 팀원의 구체적인 담당 영역을 작성해주세요.

---

## ⚙ 개발 환경 및 기술 스택

| 구분     | 기술                                           |
| -------- | --------------------------------------------- |
| Frontend | Vue 3, JavaScript, Vite, Pinia, Chart.js      |
| Backend  | Django 5.2, Django REST Framework, Python     |
| AI       | OpenAI API (GPT-4.1), ChromaDB, RAG 기반 추천 |
| Database | SQLite3                                        |
| 기타     | JWT 인증, Kakao Mobility API, YouTube API, 금융감독원 API |

---

## 🧬 주요 서비스 기능

* **AI 기반 대출 상품 추천**
  * 사용자 설문조사 기반 맞춤형 대출 상품 추천
  * RAG(Retrieval-Augmented Generation) 기술을 활용한 정확한 추천
  * ChromaDB를 활용한 벡터 검색

* **상권 분석 및 지도 서비스**
  * 사용자 맞춤형 상권 추천
  * 지도 기반 상권 정보 시각화
  * Kakao Mobility API 연동

* **금융 상품 비교**
  * 예금/적금 상품 목록 및 상세 정보
  * 금리 비교 및 필터링 기능
  * 금융감독원 API 연동으로 실시간 데이터 제공

* **환율 정보**
  * 실시간 환율 정보 제공
  * 환율 차트 시각화 (Chart.js)

* **커뮤니티**
  * 금융 관련 게시글 작성/수정/삭제
  * 댓글 및 좋아요 기능
  * 사용자 간 정보 공유

* **YouTube 금융 콘텐츠**
  * 금융 관련 YouTube 영상 검색
  * 영상 상세 정보 및 재생

* **마이페이지**
  * 프로필 관리
  * 관심 상품 관리
  * 내가 작성한 게시글 관리

---

## 📐 ERD (Database 모델링)

![ERD](./erd.png)

### 주요 모델

- **User**: 사용자 정보 (Django 기본 User 확장)
- **LoanProduct**: 대출 상품 정보
- **DepositProduct / SavingProduct**: 예적금 상품 정보
- **District**: 상권 정보
- **Post**: 커뮤니티 게시글
- **Comment**: 댓글
- **UserProfile**: 사용자 프로필 확장 정보

---

## 🏗️ 시스템 아키텍처

![architecture](./architecture.png)

### 전체 서비스 구조

```
┌─────────────────────────────────────────────────────────────┐
│                         Frontend (Vue 3)                     │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐   │
│  │   Home   │  │ AI Chat  │  │ Products │  │Community │   │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘   │
└─────────────────────────────────────────────────────────────┘
                            │
                    ┌───────┴───────┐
                    │   REST API    │
                    │   (JWT Auth)  │
                    └───────┬───────┘
                            │
┌─────────────────────────────────────────────────────────────┐
│                    Backend (Django REST)                     │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐   │
│  │ Accounts │  │ AI Loans │  │ Products │  │Community │   │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘   │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐   │
│  │ District │  │   Maps   │  │ YouTube  │  │Commodity │   │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘   │
└─────────────────────────────────────────────────────────────┘
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
   ┌────▼────┐      ┌──────▼──────┐    ┌──────▼──────┐
   │ SQLite3 │      │  ChromaDB   │    │ External    │
   │   DB    │      │  (Vector)   │    │   APIs      │
   └─────────┘      └─────────────┘    └─────────────┘
                                        │ OpenAI      │
                                        │ 금융감독원   │
                                        │ Kakao Maps  │
                                        │ YouTube     │
                                        └─────────────┘
```

### API 흐름도 (AI 대출 추천 예시)

```
User → Frontend → Backend API → AI Loans Service
                                      │
                                      ├─→ ChromaDB (벡터 검색)
                                      │
                                      └─→ OpenAI GPT-4.1 (추천 생성)
                                            │
                                            └─→ Response
                                                  │
User ← Frontend ← Backend API ←──────────────────┘
```

---

## 🤖 생성형 AI 활용 내용

### 1. AI 대출 상품 추천 시스템

#### 데이터 생성
- **ChromaDB 벡터 데이터베이스 구축**
  - 공공데이터포털의 대출 상품 정보를 임베딩하여 벡터 DB에 저장
  - OpenAI의 `text-embedding-3-small` 모델 사용
  - 상품명, 설명, 조건 등을 벡터화하여 의미 기반 검색 가능

#### 추천 로직
- **RAG (Retrieval-Augmented Generation) 기술**
  1. 사용자 설문 응답을 분석하여 쿼리 생성
  2. ChromaDB에서 유사도 기반 상품 검색 (Top-K)
  3. 검색된 상품 정보를 GPT-4.1에 컨텍스트로 제공
  4. GPT-4.1이 사용자 상황에 맞는 추천 이유와 함께 상품 추천

#### 코드 개선
- **프롬프트 엔지니어링**
  - 사용자 맞춤형 추천을 위한 프롬프트 최적화
  - 추천 이유를 명확하게 설명하도록 구조화된 프롬프트 작성
  
```python
# AI 대출 추천 프롬프트 예시
prompt = f"""
당신은 금융 전문가입니다. 다음 사용자 정보를 바탕으로 최적의 대출 상품을 추천해주세요.

사용자 정보:
- 직업: {user_job}
- 소득: {user_income}
- 대출 목적: {loan_purpose}
- 희망 금액: {desired_amount}

검색된 상품:
{retrieved_products}

위 정보를 바탕으로 가장 적합한 상품 3개를 추천하고, 각각의 추천 이유를 설명해주세요.
"""
```

### 2. 상권 분석 AI

- **GPT-4.1을 활용한 상권 분석 리포트 생성**
  - 상권 데이터(유동인구, 업종 분포 등)를 분석하여 자연어 리포트 생성
  - 창업 적합도를 수요, 경쟁력, 안정성 측면에서 평가

### 3. AI 챗봇

- **금융 Q&A 챗봇**
  - OpenAI GPT-4.1 기반 대화형 인터페이스
  - 금융 상품, 대출, 상권 분석 등에 대한 질문 응답
  - 컨텍스트 유지를 통한 연속적인 대화 지원

---

## 🎨 페이지 설계

> **Note**: 주요 페이지의 와이어프레임 또는 스크린샷을 추가해주세요.

### 주요 화면

1. **메인 페이지** (`HomeView.vue`)
   - 서비스 소개 및 주요 기능 안내
   - 금융 상품 추천 바로가기
   - 최신 커뮤니티 게시글

2. **AI 대출 추천** (`LoanSurveyView.vue` → `AiView.vue`)
   - 설문조사 폼
   - AI 추천 결과 표시
   - 추천 이유 상세 설명

3. **상권 분석 지도** (`MapRecommendView.vue`)
   - Kakao Map 기반 지도
   - 추천 상권 마커 표시
   - 상권 상세 정보 팝업

4. **금융 상품 비교** (`ProductsView.vue`)
   - 예적금 상품 목록
   - 필터 및 정렬 기능
   - 금리 비교 차트

5. **커뮤니티** (`CommunityListView.vue`)
   - 게시글 목록
   - 검색 및 필터
   - 좋아요/댓글 기능

---

## 🚀 실행 방법

### 1. 백엔드

```bash
cd Back
python -m venv venv
source venv/Scripts/activate
# .env 파일 생성 (아래 환경변수 참고)
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

#### 필요한 환경변수 (.env)
```
SECRET_KEY=your-secret-key
DEBUG=True
ALLOWED_HOSTS=127.0.0.1,localhost
OPENAI_API_KEY=your-openai-api-key
YOUTUBE_API_KEY=your-youtube-api-key
KAKAO_MOBILITY_KEY=your-kakao-key
FSS_API_KEY=your-fss-api-key
DATA_GO_KR_SERVICE_KEY=your-data-go-kr-key
```

### 2. 프론트엔드

```bash
cd Front
npm install
npm run dev
```

---

## 📋 폴더 구조 및 주요 파일

### 백엔드 (`/Back`)
* `accounts/` : 사용자 인증 및 회원 관리
* `ai_loans/` : AI 기반 대출 추천 로직
* `chroma_ai_loans/` : ChromaDB 벡터 데이터베이스
* `commodities/` : 환율 정보 관리
* `community/` : 커뮤니티 게시판
* `district/` : 상권 분석 및 추천
* `loans/` : 대출 상품 데이터 관리
* `maps/` : 지도 서비스
* `products/` : 예적금 상품 관리
* `youtube/` : YouTube API 연동
* `prototype/` : Django 프로젝트 설정

### 프론트엔드 (`/Front`)
* `/src/views/` : 페이지 컴포넌트
  * `HomeView.vue` : 메인 페이지
  * `AiView.vue` : AI 챗봇
  * `AiLandingView.vue` : AI 서비스 소개
  * `RecommendView.vue` : 상권 추천 결과
  * `MapRecommendView.vue` : 지도 기반 상권 추천
  * `LoanSurveyView.vue` : 대출 설문조사
  * `ProductsView.vue` : 금융 상품 목록
  * `CommunityListView.vue` : 커뮤니티 게시판
  * `ProfileView.vue` : 마이페이지
* `/src/components/` : 재사용 가능한 컴포넌트
* `/src/stores/` : Pinia 상태 관리
* `/src/router/` : Vue Router 설정

---

## 📞 사용 API

1. [OpenAI API](https://platform.openai.com/docs/api-reference/introduction) - AI 대출 추천 및 챗봇
2. [금융감독원 API](https://finlife.fss.or.kr/) - 예적금 상품 정보
3. [공공데이터포털 API](https://www.data.go.kr/) - 대출 상품 정보
4. [YouTube Data API](https://developers.google.com/youtube/v3) - 금융 콘텐츠 검색
5. [Kakao Mobility API](https://developers.kakaomobility.com/) - 지도 서비스

---

## 🎯 기획/차별화 포인트

* **"AI로 예비 창업자에게 스마트하게 금융 추천을 제공한다"**
  * RAG 기술을 활용한 정확한 대출 상품 추천
  * 사용자 맞춤형 상권 분석으로 창업 지원
  * 실시간 금융 상품 비교로 최적의 선택 지원
  * 커뮤니티를 통한 금융 정보 공유
  * YouTube 콘텐츠 연동으로 금융 교육 제공

---

## 🔑 주요 기능 상세

### AI 대출 추천 시스템
* **설문조사 기반 추천**: 사용자의 직업, 소득, 대출 목적 등을 분석
* **RAG 기술 활용**: ChromaDB에 저장된 대출 상품 정보를 벡터 검색
* **GPT-4.1 활용**: 자연어 처리를 통한 맞춤형 추천 이유 제공

### 상권 분석 서비스
* **맞춤형 상권 추천**: 사용자 설문을 기반으로 최적의 상권 추천
* **지도 시각화**: 추천된 상권을 지도에 표시
* **상세 분석 정보**: 수요, 경쟁력, 안정성 측면에서 상권 정보 제공

### 금융 상품 비교
* **실시간 데이터**: 금융감독원 API를 통한 최신 정보 제공
* **다양한 필터**: 금리, 은행, 상품 유형별 필터링
* **상세 비교**: 여러 상품의 조건을 한눈에 비교

---

## 🔒 보안 및 인증

* **JWT 기반 인증**: Access Token (60분), Refresh Token (7일)
* **비밀번호 검증**: Django 기본 비밀번호 검증기 활성화

---

## 📅 자동화 기능

* **대출 상품 자동 동기화**: 매일 새벽 3시에 대출 상품 정보 자동 업데이트
* **환경변수 설정**: `LOANS_SYNC_ENABLED`, `LOANS_SYNC_HOUR`, `LOANS_SYNC_MINUTE`

---

## 💭 프로젝트 후기 및 느낀 점

### 팀원1

> **Note**: 프로젝트를 진행하면서 느낀 점, 배운 점, 어려웠던 점 등을 작성해주세요.

```
예시:
RAG 기술을 처음 도입하면서 벡터 데이터베이스의 중요성을 깨달았습니다. 
ChromaDB를 활용하여 대출 상품을 의미 기반으로 검색할 수 있게 되면서 
추천의 정확도가 크게 향상되었습니다. 특히 OpenAI API와의 연동 과정에서 
프롬프트 엔지니어링의 중요성을 배웠고, 적절한 컨텍스트 제공이 
AI 성능에 얼마나 큰 영향을 미치는지 실감했습니다.
```

### 팀원2

> **Note**: 프로젝트를 진행하면서 느낀 점, 배운 점, 어려웠던 점 등을 작성해주세요.

```
예시:
Vue 3와 Pinia를 활용한 상태 관리를 처음 경험하면서 프론트엔드 
아키텍처의 중요성을 배웠습니다. 특히 Chart.js를 활용한 데이터 
시각화 작업이 인상 깊었고, 사용자 경험을 개선하기 위한 
UI/UX 디자인의 중요성을 깨달았습니다. 팀원과의 협업을 통해 
Git을 활용한 버전 관리와 코드 리뷰의 가치를 배울 수 있었습니다.
```

---

## 👫 저작권 및 오픈소스 안내

본 프로젝트는 교육/비영리 목적으로 제작되었습니다.
AI 추천 및 일부 API 기능은 OpenAI, 금융감독원, 공공데이터포털, YouTube, Kakao 등의 API를 활용하였습니다.

---
