# Pitch 관리 가이드

이 디렉토리는 프로젝트 Pitch 문서를 체계적으로 관리하기 위한 공간입니다.

## 📁 폴더 구조

```
pitch/
├── feature/           # 새로운 기능 개발 관련 Pitch
├── bugfix/            # 버그 수정 관련 Pitch
├── improvement/       # 기존 기능 개선 관련 Pitch
├── templates/         # Pitch 템플릿 파일
└── assets/           # 이미지, 다이어그램 등 첨부 파일
    ├── images/
    └── diagrams/
```

## 📝 Pitch 작성 방법

### 1. 템플릿 사용
`templates/pitch-template.md` 파일을 복사하여 사용하세요.

```bash
# 예시: 새로운 기능 Pitch 작성
cp pitch/templates/pitch-template.md pitch/feature/YYYY-MM-DD_프로젝트명_Pitch.md
```

### 2. 네이밍 컨벤션
Pitch 파일명은 다음 형식을 따릅니다:
- **형식**: `YYYY-MM-DD_프로젝트명_Pitch.md`
- **예시**:
  - `2026-01-16_enterprise-wallet_Pitch.md`
  - `2026-01-20_ai-chatbot_Pitch.md`
  - `2026-02-01_search-optimization_Pitch.md`

### 3. 카테고리 분류
- **feature/**: 새로운 기능 추가
  - 예: 소셜 로그인, 결제 시스템, 추천 알고리즘
- **bugfix/**: 버그 수정 및 핫픽스
  - 예: 로그인 오류 수정, 데이터 누락 문제 해결
- **improvement/**: 기존 기능 개선 및 최적화
  - 예: 검색 속도 개선, UI/UX 개선, 코드 리팩토링

## 📄 Pitch 문서 구조

Pitch는 다음 3개 섹션으로 구성됩니다:

### 1. Background
- 프로젝트의 배경과 필요성
- 왜 이 프로젝트를 진행하는지

### 2. Solution
- **제품 개요**: 핵심 가치를 표 형태로 정리
- **차별화 기능**: 각 기능별로 문제 인식 → 해결 방식 → 효과

### 3. User Story
- 기능 단위로 구성된 사용자 스토리
- 각 스토리는 `[카테고리]` + 설명 형태
- **Test Case**: UI를 상상할 수 있는 구체적인 테스트 케이스

## ✅ Pitch 작성 전 체크리스트

Pitch 작성 시 `pitch-checklist.md`를 참고하여 필수 항목을 확인하세요.

## 📊 Pitch 상태 관리

각 Pitch 문서 상단에 상태를 표시하세요:

| 상태 | 설명 |
|------|------|
| 🟡 Draft | 초안 작성 중 |
| 🔵 Review | 검토 중 |
| 🟢 Approved | 승인됨 |
| 🟣 In Progress | 개발 진행 중 |
| ✅ Completed | 완료 |
| ⭕ On Hold | 보류 |
| ❌ Cancelled | 취소 |

## 🔗 이미지 및 다이어그램 관리

- 이미지는 `assets/images/` 폴더에 저장
- 다이어그램은 `assets/diagrams/` 폴더에 저장
- Pitch에서 상대 경로로 참조: `![설명](../assets/images/파일명.png)`

## 📌 베스트 프랙티스

### Background 작성 시
- 간결하고 명확하게 배경 설명
- 비즈니스 임팩트나 기술적 필요성 강조

### Solution 작성 시
- 핵심 가치는 표 형태로 간단명료하게
- 차별화 기능은 문제→해결→효과 구조로 논리적으로 작성
- 기술 용어는 설명과 함께 사용

### User Story 작성 시
- 사용자 관점에서 기능 단위로 작성
- Test Case는 실제 UI 상호작용을 상상할 수 있게 구체적으로 작성
- "사용자는 ~을 할 수 있다" 형태로 작성

## 🔄 Pitch 업데이트 프로세스

1. Pitch 수정 필요 시 버전 업데이트
2. 중요한 변경사항은 이해관계자에게 공유
3. 승인 후 개발 착수

## 📚 참고 문서

- [샘플 Pitch](feature/2026-01-16_enterprise-wallet_Pitch.md) - 참고용 예제
- [Pitch 체크리스트](pitch-checklist.md) - 작성 시 확인 사항
- [Pitch 템플릿](templates/pitch-template.md) - 기본 템플릿

## 💡 팁

- Background는 간결하게, Solution은 구체적으로
- User Story는 개발자가 바로 개발할 수 있을 정도로 명확하게
- Test Case는 QA가 바로 테스트할 수 있을 정도로 상세하게
- 복잡한 기능은 여러 개의 Story로 분할

---

**문의사항이나 제안사항은 이슈를 통해 공유해주세요.**
