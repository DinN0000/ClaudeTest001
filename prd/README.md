# PRD 관리 가이드

이 디렉토리는 Product Requirements Document(PRD)를 체계적으로 관리하기 위한 공간입니다.

## 📁 폴더 구조

```
prd/
├── feature/           # 새로운 기능 개발 관련 PRD
├── bugfix/            # 버그 수정 관련 PRD
├── improvement/       # 기존 기능 개선 관련 PRD
├── templates/         # PRD 템플릿 파일
└── assets/           # 이미지, 다이어그램 등 첨부 파일
    ├── images/
    └── diagrams/
```

## 📝 PRD 작성 방법

### 1. 템플릿 사용
`templates/prd-template.md` 파일을 복사하여 사용하세요.

```bash
# 예시: 새로운 기능 PRD 작성
cp templates/prd-template.md feature/YYYY-MM-DD_프로젝트명_PRD.md
```

### 2. 네이밍 컨벤션
PRD 파일명은 다음 형식을 따릅니다:
- **형식**: `YYYY-MM-DD_프로젝트명_PRD.md`
- **예시**:
  - `2026-01-16_user-authentication_PRD.md`
  - `2026-01-20_payment-integration_PRD.md`
  - `2026-02-01_search-performance-improvement_PRD.md`

### 3. 카테고리 분류
- **feature/**: 새로운 기능 추가
  - 예: 소셜 로그인, 결제 시스템, 추천 알고리즘
- **bugfix/**: 버그 수정 및 핫픽스
  - 예: 로그인 오류 수정, 데이터 누락 문제 해결
- **improvement/**: 기존 기능 개선 및 최적화
  - 예: 검색 속도 개선, UI/UX 개선, 코드 리팩토링

## ✅ PRD 작성 전 체크리스트

PRD 작성 시 `prd-checklist.md`를 참고하여 필수 항목을 확인하세요.

## 📊 PRD 상태 관리

각 PRD 문서 상단에 상태를 표시하세요:

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
- PRD에서 상대 경로로 참조: `![설명](../assets/images/파일명.png)`

## 📌 베스트 프랙티스

1. **명확성**: 기술적인 용어는 설명과 함께 사용
2. **구체성**: 모호한 표현 대신 구체적인 수치와 기준 사용
3. **추적 가능성**: 각 요구사항에 고유 ID 부여 (예: REQ-001)
4. **최신성 유지**: PRD 변경 시 변경 이력 섹션 업데이트
5. **리뷰 프로세스**: 최소 1명 이상의 리뷰어 확보

## 🔄 PRD 업데이트 프로세스

1. PRD 수정 필요 시 새로운 버전으로 관리
2. 문서 하단 "변경 이력" 섹션에 수정 내용 기록
3. 중요한 변경사항은 이해관계자에게 공유

## 📚 참고 문서

- [샘플 PRD](feature/2026-01-16_sample-feature_PRD.md) - 참고용 예제
- [PRD 체크리스트](prd-checklist.md) - 작성 시 확인 사항
- [PRD 템플릿](templates/prd-template.md) - 기본 템플릿

## 💡 팁

- 복잡한 기능은 여러 개의 작은 PRD로 분할하는 것을 고려하세요
- 다이어그램과 플로우차트를 적극 활용하여 이해도를 높이세요
- 기술 스펙은 별도 문서로 분리할 수도 있습니다

---

**문의사항이나 제안사항은 이슈를 통해 공유해주세요.**
