# 사용자 알림 시스템 PRD

**상태**: 🟢 Approved
**작성자**: 김프로덕트
**작성일**: 2026-01-16
**최종 수정일**: 2026-01-16
**버전**: 1.0

---

## 📋 목차

1. [개요](#개요)
2. [배경 및 목표](#배경-및-목표)
3. [이해관계자](#이해관계자)
4. [사용자 스토리](#사용자-스토리)
5. [기능 요구사항](#기능-요구사항)
6. [비기능 요구사항](#비기능-요구사항)
7. [기술 스펙](#기술-스펙)
8. [UI/UX 설계](#uiux-설계)
9. [데이터 모델](#데이터-모델)
10. [API 명세](#api-명세)
11. [보안 및 권한](#보안-및-권한)
12. [성공 지표 (KPI)](#성공-지표-kpi)
13. [일정 및 마일스톤](#일정-및-마일스톤)
14. [리스크 및 완화 방안](#리스크-및-완화-방안)
15. [의존성](#의존성)
16. [참고 자료](#참고-자료)
17. [변경 이력](#변경-이력)

---

## 개요

### 프로젝트 요약
사용자에게 중요한 이벤트와 업데이트를 실시간으로 전달하는 통합 알림 시스템을 구축합니다. 인앱, 이메일, 푸시 알림을 지원하며, 사용자가 알림 설정을 세밀하게 제어할 수 있습니다.

### 문제 정의
현재 시스템에서는 사용자에게 중요한 정보를 전달할 수 있는 체계적인 방법이 없습니다. 이로 인해:
- 사용자가 중요한 업데이트를 놓치고 있음 (이탈률 35% 증가)
- 고객 지원 문의의 40%가 "알림을 못 받았다"는 내용
- 사용자 참여도가 업계 평균 대비 25% 낮음

### 해결 방안
다채널 알림 시스템을 구축하여 사용자가 선호하는 방식으로 중요한 정보를 받을 수 있도록 합니다. 사용자 맞춤 설정을 통해 알림 피로도를 최소화하고, 실시간 전달로 즉각적인 반응을 유도합니다.

---

## 배경 및 목표

### 배경
최근 사용자 설문조사에서 78%의 사용자가 "중요한 업데이트를 놓쳤다"고 응답했습니다. 경쟁사는 이미 정교한 알림 시스템을 갖추고 있으며, 우리 서비스의 사용자 유지율이 지속적으로 하락하고 있습니다.

비즈니스 영향:
- 월간 활성 사용자(MAU) 15% 감소
- 사용자 재방문율 20% 하락
- 고객 만족도(CSAT) 점수 3.2/5.0

### 목표

**주요 목표**:
- 사용자 참여도 40% 증가
- 7일 재방문율 60% 달성
- 알림 클릭률(CTR) 25% 이상
- 고객 만족도 4.0/5.0 이상

**부가 목표**:
- 고객 지원 문의 30% 감소
- 프리미엄 전환율 10% 증가
- 일일 활성 사용자(DAU) 증가

### 범위 (Scope)

#### In Scope
- [x] 인앱 알림 (실시간 알림 센터)
- [x] 이메일 알림
- [x] 웹 푸시 알림
- [x] 알림 설정 관리 UI
- [x] 알림 카테고리별 On/Off 제어
- [x] 알림 히스토리 조회
- [x] 읽음/읽지 않음 상태 관리
- [x] 알림 템플릿 시스템

#### Out of Scope
- [ ] 모바일 앱 푸시 알림 (Phase 2)
- [ ] SMS 알림 (Phase 2)
- [ ] 슬랙/디스코드 통합 (Phase 3)
- [ ] AI 기반 알림 최적화 (Phase 3)
- [ ] 알림 스케줄링 (Phase 2)

---

## 이해관계자

| 역할 | 이름 | 책임 | 연락처 |
|------|------|------|--------|
| 프로젝트 오너 | 박임원 | 최종 의사결정 | executive@company.com |
| 프로덕트 매니저 | 김프로덕트 | 제품 전략 및 우선순위 | pm@company.com |
| 개발 리드 | 이개발 | 기술 아키텍처 및 구현 | dev-lead@company.com |
| 백엔드 개발자 | 최백엔드 | API 및 알림 전송 로직 | backend@company.com |
| 프론트엔드 개발자 | 정프론트 | UI 컴포넌트 구현 | frontend@company.com |
| 디자이너 | 한디자인 | UI/UX 디자인 | design@company.com |
| QA 리드 | 강테스트 | 테스트 전략 및 실행 | qa@company.com |
| 마케팅 | 조마케팅 | 알림 콘텐츠 전략 | marketing@company.com |

---

## 사용자 스토리

### Persona 1: 액티브 사용자 (데일리 유저)
**배경**: 매일 서비스를 사용하며, 실시간 업데이트를 중요하게 생각하는 25-35세 직장인. 데스크톱과 모바일을 모두 활용.

**User Stories**:

1. **US-001**: 액티브 사용자로서, 중요한 업데이트를 즉시 받아보기 위해 실시간 알림을 원한다.
   - **Acceptance Criteria**:
     - [x] 알림이 발생한 후 5초 이내에 인앱 알림을 받을 수 있다
     - [x] 알림 센터에 읽지 않은 알림 개수가 표시된다
     - [x] 알림 클릭 시 관련 페이지로 이동한다
   - **우선순위**: P0

2. **US-002**: 액티브 사용자로서, 업무 시간에는 방해받지 않기 위해 알림 설정을 제어하고 싶다.
   - **Acceptance Criteria**:
     - [x] 알림 카테고리별로 On/Off를 설정할 수 있다
     - [x] 이메일/푸시 알림을 독립적으로 제어할 수 있다
     - [x] 설정 변경이 즉시 적용된다
   - **우선순위**: P0

### Persona 2: 캐주얼 사용자 (주간 유저)
**배경**: 일주일에 2-3회 서비스를 사용하며, 중요한 정보만 간결하게 받고 싶어 하는 35-50세 사용자.

**User Stories**:

3. **US-003**: 캐주얼 사용자로서, 놓친 중요한 알림을 한눈에 확인하기 위해 알림 히스토리를 원한다.
   - **Acceptance Criteria**:
     - [x] 최근 30일간의 알림을 조회할 수 있다
     - [x] 카테고리별로 필터링할 수 있다
     - [x] 읽지 않은 알림이 상단에 표시된다
   - **우선순위**: P1

4. **US-004**: 캐주얼 사용자로서, 알림이 너무 많아 피로하지 않도록 중요한 알림만 받고 싶다.
   - **Acceptance Criteria**:
     - [x] 알림 빈도를 설정할 수 있다 (실시간/일일 요약/주간 요약)
     - [x] 중요도가 높은 알림만 받는 옵션이 있다
     - [x] 알림 미리보기로 내용을 확인 후 설정할 수 있다
   - **우선순위**: P1

### Persona 3: 신규 사용자
**배경**: 서비스를 처음 사용하며, 알림 시스템을 잘 모르는 사용자.

**User Stories**:

5. **US-005**: 신규 사용자로서, 알림 시스템을 쉽게 이해하고 설정하기 위해 온보딩 가이드를 원한다.
   - **Acceptance Criteria**:
     - [x] 첫 로그인 시 알림 설정 가이드가 표시된다
     - [x] 추천 설정을 원클릭으로 적용할 수 있다
     - [x] 나중에 다시 설정할 수 있는 옵션이 있다
   - **우선순위**: P2

---

## 기능 요구사항

### 핵심 기능

#### REQ-001: 실시간 인앱 알림
- **설명**: 사용자가 로그인한 상태에서 실시간으로 알림을 받을 수 있는 기능
- **우선순위**: P0
- **사용자 스토리**: US-001
- **세부 요구사항**:
  - [x] WebSocket을 통한 실시간 알림 전송
  - [x] 알림 토스트(Toast) UI 표시 (5초 후 자동 사라짐)
  - [x] 알림 센터 아이콘에 뱃지 표시 (읽지 않은 개수)
  - [x] 알림 클릭 시 관련 페이지로 네비게이션
  - [x] 알림 음소거 기능
- **Acceptance Criteria**:
  - [x] 알림 발생 후 5초 이내 전달
  - [x] 동시에 여러 알림이 와도 모두 표시
  - [x] 오프라인 상태에서 발생한 알림은 로그인 시 표시

#### REQ-002: 알림 센터
- **설명**: 모든 알림을 확인하고 관리할 수 있는 중앙 허브
- **우선순위**: P0
- **사용자 스토리**: US-001, US-003
- **세부 요구사항**:
  - [x] 최근 알림 목록 표시 (페이지네이션)
  - [x] 읽음/읽지 않음 상태 토글
  - [x] 전체 읽음 처리 버튼
  - [x] 개별 알림 삭제
  - [x] 카테고리별 탭 필터
  - [x] 날짜별 그룹핑
- **Acceptance Criteria**:
  - [x] 알림 센터 로딩 시간 < 500ms
  - [x] 무한 스크롤 지원
  - [x] 모바일 반응형 UI

#### REQ-003: 이메일 알림
- **설명**: 중요한 알림을 이메일로 전송
- **우선순위**: P0
- **사용자 스토리**: US-001
- **세부 요구사항**:
  - [x] HTML 이메일 템플릿
  - [x] 이메일 내 CTA 버튼
  - [x] 이메일 수신 거부 링크
  - [x] 발송 실패 시 재시도 로직 (최대 3회)
- **Acceptance Criteria**:
  - [x] 알림 발생 후 1분 이내 이메일 발송
  - [x] 발송 성공률 > 99%
  - [x] 스팸 필터 회피 (SPF, DKIM 설정)

#### REQ-004: 웹 푸시 알림
- **설명**: 브라우저 푸시 알림 지원
- **우선순위**: P1
- **사용자 스토리**: US-001
- **세부 요구사항**:
  - [x] Push API 사용
  - [x] 푸시 알림 권한 요청 UI
  - [x] 푸시 알림 클릭 시 앱으로 이동
  - [x] 푸시 토큰 관리
- **Acceptance Criteria**:
  - [x] Chrome, Firefox, Safari 지원
  - [x] 푸시 알림 전송률 > 95%
  - [x] 사용자 거부 시 다시 묻지 않기

#### REQ-005: 알림 설정 관리
- **설명**: 사용자가 알림 수신 설정을 제어
- **우선순위**: P0
- **사용자 스토리**: US-002, US-004
- **세부 요구사항**:
  - [x] 알림 카테고리별 On/Off 토글
  - [x] 채널별 설정 (인앱/이메일/푸시)
  - [x] 알림 빈도 설정 (실시간/일일/주간)
  - [x] 중요도 필터 (모두/중요만)
  - [x] 전체 알림 비활성화 옵션
- **Acceptance Criteria**:
  - [x] 설정 변경 즉시 적용
  - [x] 설정 UI는 직관적이고 명확
  - [x] 기본 설정 제공

#### REQ-006: 알림 템플릿 시스템
- **설명**: 다양한 알림 타입을 지원하는 템플릿 엔진
- **우선순위**: P1
- **사용자 스토리**: 개발팀 요구사항
- **세부 요구사항**:
  - [x] 변수 치환 지원 (예: {user_name}, {product_name})
  - [x] 다국어 지원 (i18n)
  - [x] 이메일/인앱/푸시 별도 템플릿
  - [x] 템플릿 버전 관리
- **Acceptance Criteria**:
  - [x] 새 알림 타입 추가 시 코드 변경 최소화
  - [x] 템플릿 렌더링 < 50ms

---

## 비기능 요구사항

### 성능
- **응답 시간**:
  - 알림 센터 로딩 < 500ms (P95)
  - 알림 전송 < 5초 (P99)
  - 설정 변경 적용 < 1초
- **처리량**:
  - 동시 접속자 10,000명 지원
  - 초당 알림 전송 1,000건 처리
- **데이터 크기**:
  - 알림 히스토리 30일간 보관
  - 사용자당 최대 1,000개 알림 저장

### 확장성
- 수평적 확장 가능한 아키텍처 (마이크로서비스)
- 알림 전송 큐 시스템 (메시지 브로커 사용)
- 캐싱 전략으로 DB 부하 최소화

### 가용성
- **목표 가동률**: 99.9% (월 43분 다운타임 허용)
- **복구 시간**: MTTR < 15분
- **백업**: 일일 자동 백업, 7일 보관

### 보안
- 알림 내용 암호화 (전송 중, 저장 시)
- XSS 공격 방지 (알림 콘텐츠 sanitization)
- Rate limiting (사용자당 분당 100회)
- 개인정보 포함 알림은 이메일 본문에 미포함

### 접근성
- WCAG 2.1 AA 준수
- 스크린 리더 지원
- 키보드 네비게이션
- 고대비 모드 지원

### 호환성
- **브라우저**: Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- **모바일 웹**: iOS Safari 14+, Chrome Mobile
- **해상도**: 320px ~ 2560px 반응형

---

## 기술 스펙

### 기술 스택
- **프론트엔드**:
  - React 18+ (UI 컴포넌트)
  - TypeScript (타입 안전성)
  - TanStack Query (서버 상태 관리)
  - Socket.io Client (실시간 통신)
  - Tailwind CSS (스타일링)

- **백엔드**:
  - Node.js 20+ (런타임)
  - Express.js (API 서버)
  - Socket.io (WebSocket)
  - Bull (작업 큐)
  - Redis (캐시 & 큐)

- **데이터베이스**:
  - PostgreSQL 15+ (메인 DB)
  - Redis (세션, 캐시, 큐)

- **인프라**:
  - Docker (컨테이너화)
  - Kubernetes (오케스트레이션)
  - AWS SES (이메일 전송)
  - FCM/APNS (푸시 알림)

- **기타**:
  - SendGrid/AWS SES (이메일)
  - Sentry (에러 트래킹)
  - Datadog (모니터링)

### 아키텍처

```
┌─────────────┐
│   Client    │
│  (React)    │
└──────┬──────┘
       │
       │ HTTP/WS
       ▼
┌─────────────────────────────────┐
│      API Gateway / LB           │
└───────────┬─────────────────────┘
            │
    ┌───────┴────────┐
    │                │
    ▼                ▼
┌─────────┐    ┌──────────┐
│   API   │    │ WebSocket│
│ Server  │    │  Server  │
└────┬────┘    └─────┬────┘
     │               │
     │    ┌──────────┘
     │    │
     ▼    ▼
┌──────────────┐     ┌───────────┐
│  PostgreSQL  │     │   Redis   │
│  (알림 저장)  │     │ (캐시/큐)  │
└──────────────┘     └─────┬─────┘
                           │
                           ▼
                    ┌─────────────┐
                    │  Bull Queue │
                    │ (작업 큐)    │
                    └──────┬──────┘
                           │
            ┌──────────────┼──────────────┐
            │              │              │
            ▼              ▼              ▼
     ┌──────────┐   ┌──────────┐  ┌──────────┐
     │  Email   │   │   Push   │  │  Worker  │
     │  Worker  │   │  Worker  │  │  (기타)   │
     └────┬─────┘   └────┬─────┘  └──────────┘
          │              │
          ▼              ▼
     ┌─────────┐   ┌─────────┐
     │AWS SES  │   │   FCM   │
     │/SendGrid│   │  /APNS  │
     └─────────┘   └─────────┘
```

### 외부 서비스/API
- **AWS SES**: 이메일 전송
- **Firebase Cloud Messaging (FCM)**: Android 푸시
- **Apple Push Notification Service (APNS)**: iOS 푸시 (Phase 2)
- **Sentry**: 에러 모니터링
- **Datadog**: 성능 모니터링

---

## UI/UX 설계

### 화면 플로우

```
로그인
  │
  ├─→ [알림 발생] ─→ 토스트 알림 표시
  │                      │
  │                      ├─→ 클릭 → 관련 페이지
  │                      └─→ 무시 → 알림 센터에 저장
  │
  ├─→ 알림 센터 아이콘 클릭 → 알림 목록
  │                            │
  │                            ├─→ 알림 클릭 → 상세/관련 페이지
  │                            ├─→ 읽음 처리
  │                            └─→ 삭제
  │
  └─→ 설정 → 알림 설정
              │
              ├─→ 카테고리별 On/Off
              ├─→ 채널별 설정
              └─→ 빈도 설정
```

### 주요 화면

#### 화면 1: 알림 토스트
- **목적**: 실시간 알림을 사용자에게 즉시 전달
- **주요 요소**:
  - 아이콘 (알림 타입별)
  - 제목 및 메시지
  - 타임스탬프
  - 닫기 버튼
  - CTA 버튼 (선택사항)
- **위치**: 화면 우측 상단
- **동작**: 5초 후 자동 사라짐, 호버 시 유지

#### 화면 2: 알림 센터
- **목적**: 모든 알림을 한곳에서 관리
- **주요 요소**:
  - 헤더 (제목, 전체 읽음 처리, 설정 링크)
  - 탭 필터 (전체, 카테고리별)
  - 알림 목록 (무한 스크롤)
  - 각 알림 카드 (아이콘, 제목, 내용, 시간, 읽음 상태)
  - 빈 상태 화면
- **레이아웃**: 드롭다운 패널 (최대 높이 600px)

#### 화면 3: 알림 설정 페이지
- **목적**: 사용자 맞춤 알림 설정
- **주요 요소**:
  - 전체 알림 On/Off 토글
  - 카테고리별 설정 섹션
    - 카테고리 제목
    - 설명
    - 인앱/이메일/푸시 토글
  - 알림 빈도 라디오 버튼
  - 저장 버튼
- **레이아웃**: 설정 페이지 내 전용 섹션

---

## 데이터 모델

### Entity 1: notifications

| 필드명 | 타입 | 필수 | 설명 | 기본값 | 인덱스 |
|--------|------|------|------|--------|--------|
| id | UUID | Y | 고유 식별자 | auto | PK |
| user_id | UUID | Y | 수신자 ID | - | INDEX |
| type | ENUM | Y | 알림 타입 (예: comment, like, mention) | - | INDEX |
| category | ENUM | Y | 카테고리 (social, system, marketing) | - | INDEX |
| priority | ENUM | Y | 우선순위 (high, medium, low) | medium | - |
| title | VARCHAR(200) | Y | 알림 제목 | - | - |
| message | TEXT | Y | 알림 내용 | - | - |
| metadata | JSONB | N | 추가 데이터 (링크, 액션 등) | {} | - |
| is_read | BOOLEAN | Y | 읽음 여부 | false | INDEX |
| read_at | TIMESTAMP | N | 읽은 시각 | null | - |
| created_at | TIMESTAMP | Y | 생성 시각 | now() | INDEX |
| expires_at | TIMESTAMP | N | 만료 시각 | now() + 30 days | INDEX |

**인덱스**:
- `idx_notifications_user_created` ON (user_id, created_at DESC)
- `idx_notifications_user_unread` ON (user_id, is_read) WHERE is_read = false

### Entity 2: notification_settings

| 필드명 | 타입 | 필수 | 설명 | 기본값 |
|--------|------|------|------|--------|
| id | UUID | Y | 고유 식별자 | auto |
| user_id | UUID | Y | 사용자 ID | - |
| category | ENUM | Y | 알림 카테고리 | - |
| in_app_enabled | BOOLEAN | Y | 인앱 알림 On/Off | true |
| email_enabled | BOOLEAN | Y | 이메일 알림 On/Off | true |
| push_enabled | BOOLEAN | Y | 푸시 알림 On/Off | false |
| frequency | ENUM | Y | 빈도 (realtime, daily, weekly) | realtime |
| updated_at | TIMESTAMP | Y | 수정 시각 | now() |

**Unique 제약**: (user_id, category)

### Entity 3: push_subscriptions

| 필드명 | 타입 | 필수 | 설명 | 기본값 |
|--------|------|------|------|--------|
| id | UUID | Y | 고유 식별자 | auto |
| user_id | UUID | Y | 사용자 ID | - |
| endpoint | TEXT | Y | 푸시 엔드포인트 | - |
| auth_key | TEXT | Y | 인증 키 | - |
| p256dh_key | TEXT | Y | 공개 키 | - |
| user_agent | TEXT | N | 브라우저 정보 | - |
| created_at | TIMESTAMP | Y | 생성 시각 | now() |
| last_used_at | TIMESTAMP | Y | 마지막 사용 시각 | now() |

**인덱스**: user_id

### 관계도
```
users (1) ──< (N) notifications
users (1) ──< (N) notification_settings
users (1) ──< (N) push_subscriptions
```

---

## API 명세

### Endpoint 1: 알림 목록 조회

```
GET /api/v1/notifications
```

**Query Parameters**:
- `page` (int): 페이지 번호 (default: 1)
- `limit` (int): 페이지당 개수 (default: 20, max: 100)
- `category` (string): 필터링할 카테고리 (optional)
- `unread_only` (boolean): 읽지 않은 알림만 (optional)

**Request Headers**:
```
Authorization: Bearer {access_token}
```

**Response** (200 OK):
```json
{
  "data": [
    {
      "id": "550e8400-e29b-41d4-a716-446655440000",
      "type": "comment",
      "category": "social",
      "priority": "medium",
      "title": "새로운 댓글",
      "message": "홍길동님이 게시물에 댓글을 남겼습니다.",
      "metadata": {
        "post_id": "abc123",
        "comment_id": "def456",
        "action_url": "/posts/abc123"
      },
      "is_read": false,
      "created_at": "2026-01-16T10:30:00Z"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 150,
    "has_more": true
  },
  "unread_count": 12
}
```

**Error Responses**:
- `401 Unauthorized`: 인증 실패
- `500 Internal Server Error`: 서버 오류

---

### Endpoint 2: 알림 읽음 처리

```
PATCH /api/v1/notifications/:id/read
```

**Request Headers**:
```
Authorization: Bearer {access_token}
```

**Response** (200 OK):
```json
{
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "is_read": true,
  "read_at": "2026-01-16T11:00:00Z"
}
```

**Error Responses**:
- `401 Unauthorized`: 인증 실패
- `404 Not Found`: 알림을 찾을 수 없음
- `403 Forbidden`: 권한 없음

---

### Endpoint 3: 전체 읽음 처리

```
POST /api/v1/notifications/read-all
```

**Request Headers**:
```
Authorization: Bearer {access_token}
```

**Response** (200 OK):
```json
{
  "updated_count": 12,
  "message": "모든 알림을 읽음 처리했습니다."
}
```

---

### Endpoint 4: 알림 설정 조회

```
GET /api/v1/notifications/settings
```

**Request Headers**:
```
Authorization: Bearer {access_token}
```

**Response** (200 OK):
```json
{
  "settings": [
    {
      "category": "social",
      "in_app_enabled": true,
      "email_enabled": true,
      "push_enabled": false,
      "frequency": "realtime"
    },
    {
      "category": "system",
      "in_app_enabled": true,
      "email_enabled": true,
      "push_enabled": true,
      "frequency": "realtime"
    }
  ]
}
```

---

### Endpoint 5: 알림 설정 업데이트

```
PUT /api/v1/notifications/settings/:category
```

**Request Headers**:
```
Authorization: Bearer {access_token}
Content-Type: application/json
```

**Request Body**:
```json
{
  "in_app_enabled": true,
  "email_enabled": false,
  "push_enabled": true,
  "frequency": "daily"
}
```

**Response** (200 OK):
```json
{
  "category": "social",
  "in_app_enabled": true,
  "email_enabled": false,
  "push_enabled": true,
  "frequency": "daily",
  "updated_at": "2026-01-16T11:15:00Z"
}
```

---

### Endpoint 6: 푸시 구독 등록

```
POST /api/v1/notifications/push/subscribe
```

**Request Headers**:
```
Authorization: Bearer {access_token}
Content-Type: application/json
```

**Request Body**:
```json
{
  "endpoint": "https://fcm.googleapis.com/fcm/send/...",
  "keys": {
    "auth": "...",
    "p256dh": "..."
  }
}
```

**Response** (201 Created):
```json
{
  "id": "sub-12345",
  "message": "푸시 알림이 활성화되었습니다."
}
```

---

### WebSocket Events

#### 서버 → 클라이언트

**Event: `notification`**
```json
{
  "event": "notification",
  "data": {
    "id": "550e8400-e29b-41d4-a716-446655440000",
    "type": "comment",
    "category": "social",
    "title": "새로운 댓글",
    "message": "홍길동님이 게시물에 댓글을 남겼습니다.",
    "metadata": {
      "action_url": "/posts/abc123"
    },
    "created_at": "2026-01-16T10:30:00Z"
  }
}
```

**Event: `notification_read`**
```json
{
  "event": "notification_read",
  "data": {
    "notification_id": "550e8400-e29b-41d4-a716-446655440000"
  }
}
```

---

## 보안 및 권한

### 인증/인가
- **인증 방식**: JWT (JSON Web Token)
- **권한 관리**: 사용자는 자신의 알림만 조회/수정 가능
- **토큰 만료**: Access Token 1시간, Refresh Token 30일

### 역할 및 권한

| 역할 | 권한 |
|------|------|
| User | 자신의 알림 조회, 읽음 처리, 설정 변경, 삭제 |
| Admin | 모든 사용자 알림 조회 (관리 목적), 시스템 알림 발송 |
| System | 알림 생성 및 전송 (백엔드 서비스) |

### 데이터 보호
- **전송 중 암호화**: HTTPS (TLS 1.3)
- **저장 시 암호화**: 민감한 메타데이터는 AES-256 암호화
- **개인정보**: 이메일에는 최소한의 정보만 포함, 상세 내용은 링크로 제공
- **데이터 보관**: 30일 후 자동 삭제 (GDPR 준수)

### Rate Limiting
- 알림 조회: 사용자당 분당 100회
- 설정 변경: 사용자당 분당 10회
- WebSocket 연결: IP당 동시 5개

### XSS/Injection 방지
- 알림 내용 HTML 이스케이핑
- SQL Injection 방지 (Parameterized Query)
- CORS 정책 적용

---

## 성공 지표 (KPI)

### 비즈니스 메트릭
1. **사용자 참여도**: 7일 재방문율 60% 달성 (현재 40%)
2. **알림 CTR**: 알림 클릭률 25% 이상
3. **사용자 만족도**: CSAT 4.0/5.0 이상 (현재 3.2/5.0)
4. **고객 지원 감소**: 알림 관련 문의 30% 감소
5. **전환율**: 프리미엄 전환율 10% 증가

### 기술 메트릭
1. **알림 전송 속도**: 발생 후 5초 이내 전달 (P99)
2. **이메일 발송률**: 99% 이상 성공
3. **시스템 가용성**: 99.9% 이상
4. **API 응답 시간**: 알림 조회 < 500ms (P95)
5. **에러율**: < 0.1%

### 사용자 행동 메트릭
1. **알림 센터 방문율**: MAU의 70% 이상
2. **알림 설정 변경률**: 신규 사용자의 50% 이상
3. **푸시 허용률**: 35% 이상
4. **읽음 처리율**: 발송 알림의 80% 이상

### 측정 방법
- **Google Analytics**: 페이지 방문, 클릭 이벤트
- **Mixpanel**: 사용자 행동 추적, 퍼널 분석
- **Datadog**: 시스템 성능, API 응답 시간
- **Sentry**: 에러율, 장애 추적
- **자체 대시보드**: 알림 발송/읽음 통계

---

## 일정 및 마일스톤

| 마일스톤 | 주요 산출물 | 목표일 | 상태 |
|----------|-------------|--------|------|
| M1: 설계 완료 | 기술 설계 문서, DB 스키마, API 스펙 | 2026-01-20 | ✅ |
| M2: 백엔드 개발 완료 | API 구현, WebSocket 서버, 알림 전송 로직 | 2026-02-05 | 🟣 |
| M3: 프론트엔드 개발 완료 | UI 컴포넌트, 알림 센터, 설정 페이지 | 2026-02-15 | ⭕ |
| M4: 통합 테스트 완료 | E2E 테스트, 부하 테스트 | 2026-02-22 | ⭕ |
| M5: QA 완료 | 테스트 보고서, 버그 수정 | 2026-02-28 | ⭕ |
| M6: 베타 배포 | 베타 사용자 피드백 | 2026-03-05 | ⭕ |
| M7: 프로덕션 배포 | 전체 사용자 롤아웃 | 2026-03-12 | ⭕ |

### 상세 일정

**Week 1-2 (2026-01-16 ~ 01-27)**:
- 기술 설계 및 아키텍처 확정
- DB 스키마 설계
- API 스펙 문서화
- 프로토타입 UI 디자인

**Week 3-5 (2026-01-28 ~ 02-17)**:
- 백엔드 API 개발
- WebSocket 서버 구현
- 알림 전송 워커 개발
- 이메일/푸시 통합
- 프론트엔드 컴포넌트 개발

**Week 6-7 (2026-02-18 ~ 03-03)**:
- 통합 테스트
- 부하 테스트
- QA 및 버그 수정
- 문서화

**Week 8-9 (2026-03-04 ~ 03-12)**:
- 베타 배포 및 피드백 수집
- 최종 수정
- 프로덕션 배포

---

## 리스크 및 완화 방안

| 리스크 | 영향도 | 확률 | 완화 방안 | 담당자 |
|--------|--------|------|-----------|--------|
| WebSocket 서버 부하로 인한 지연 | High | Medium | 수평 확장 가능한 아키텍처 설계, Redis Pub/Sub 활용, 부하 테스트 사전 실시 | 이개발 |
| 이메일 스팸 필터링 | Medium | High | SPF/DKIM/DMARC 설정, 평판 좋은 이메일 서비스 사용, 발송량 점진적 증가 | 최백엔드 |
| 푸시 알림 허용률 저조 | Medium | Medium | UX를 고려한 권한 요청 타이밍, 가치 제안 명확화, A/B 테스트 | 김프로덕트 |
| 알림 피로도 증가 | High | Medium | 기본 설정 보수적 설정, 알림 빈도 제한, 사용자 설정 강조 | 김프로덕트 |
| 개발 일정 지연 | Medium | Medium | 2주 버퍼 포함, 주간 진행 상황 체크, 우선순위 조정 가능성 | 이개발 |
| 데이터베이스 성능 저하 | High | Low | 적절한 인덱스 설계, 쿼리 최적화, Read Replica 활용, 파티셔닝 고려 | 최백엔드 |
| 개인정보 규제 위반 | High | Low | GDPR 준수, 데이터 30일 자동 삭제, 법무팀 검토 | 박임원 |

---

## 의존성

### 내부 의존성
- **인증 시스템**: JWT 토큰 발급 및 검증
- **사용자 관리 시스템**: 사용자 정보 조회
- **콘텐츠 시스템**: 게시물, 댓글 등 연관 데이터

**영향**: 알림 생성 시 해당 시스템의 데이터 필요

### 외부 의존성
- **AWS SES**: 이메일 전송 서비스
  - SLA: 99.9%
  - 대체 옵션: SendGrid
- **Firebase (FCM)**: 푸시 알림
  - 무료 티어 제한 확인 필요
  - 대체 옵션: OneSignal
- **Datadog**: 모니터링
  - 비용 예산 승인 필요

**블로커**: AWS SES 계정 승인 (최대 2일 소요)

---

## 참고 자료

- [Slack 알림 시스템 분석](https://example.com/slack-notifications)
- [GitHub 알림 UX 연구](https://example.com/github-ux)
- [Push API 공식 문서](https://developer.mozilla.org/en-US/docs/Web/API/Push_API)
- [Socket.io Best Practices](https://socket.io/docs/v4/)
- [이메일 전송 Best Practices (AWS)](https://docs.aws.amazon.com/ses/)
- [GDPR Compliance Checklist](https://gdpr.eu/checklist/)

---

## 변경 이력

| 버전 | 날짜 | 작성자 | 변경 내용 |
|------|------|--------|-----------|
| 1.0 | 2026-01-16 | 김프로덕트 | 초안 작성 및 검토 완료 |

---

## 승인

| 역할 | 이름 | 승인 날짜 | 서명 |
|------|------|-----------|------|
| 프로덕트 매니저 | 김프로덕트 | 2026-01-16 | ✅ |
| 개발 리드 | 이개발 | 2026-01-16 | ✅ |
| 프로젝트 오너 | 박임원 | 2026-01-16 | ✅ |
