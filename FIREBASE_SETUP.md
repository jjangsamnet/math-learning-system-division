# Firebase Database 설정 가이드

## 문제 상황
`permission_denied` 오류가 발생하는 이유는 Firebase Realtime Database의 보안 규칙이 나눗셈 시스템의 데이터 경로를 허용하지 않기 때문입니다.

## 해결 방법

### 1. Firebase Console 접속
1. https://console.firebase.google.com/ 접속
2. `multiplication-practice-2024` 프로젝트 선택

### 2. Realtime Database 규칙 수정
1. 왼쪽 메뉴에서 **"Realtime Database"** 클릭
2. 상단 탭에서 **"규칙"** 또는 **"Rules"** 클릭
3. 현재 규칙을 다음과 같이 수정:

```json
{
  "rules": {
    "students": {
      ".read": true,
      ".write": true
    },
    "students_division": {
      ".read": true,
      ".write": true
    },
    "allStudents": {
      ".read": true,
      ".write": true
    },
    "allStudents_division": {
      ".read": true,
      ".write": true
    },
    "activities": {
      ".read": true,
      ".write": true
    },
    "activities_division": {
      ".read": true,
      ".write": true
    },
    "accessCodes": {
      ".read": true,
      ".write": true
    },
    "accessCodes_division": {
      ".read": true,
      ".write": true
    }
  }
}
```

### 3. 규칙 게시
1. **"게시"** 또는 **"Publish"** 버튼 클릭
2. 확인 대화상자에서 **"예"** 클릭

## 보안 참고사항

⚠️ **주의**: 위 규칙은 개발/테스트 환경용입니다. 프로덕션 환경에서는 다음과 같이 더 엄격한 규칙을 사용하세요:

```json
{
  "rules": {
    "students_division": {
      ".read": true,
      ".write": "auth != null"
    },
    "allStudents_division": {
      ".read": true,
      ".write": "auth != null"
    },
    "activities_division": {
      ".read": true,
      ".write": "auth != null"
    },
    "accessCodes_division": {
      ".read": true,
      ".write": "auth != null"
    }
  }
}
```

## 확인 방법

규칙 적용 후:
1. division-system.html 페이지 새로고침 (Ctrl+F5)
2. 브라우저 콘솔(F12) 확인
3. `permission_denied` 오류가 사라지고 다음 메시지 확인:
   - ✅ 기본 접근 코드 설정 완료
   - ✅ 접근 코드 저장 완료

## 문제가 계속되는 경우

1. 브라우저 캐시 완전 삭제
2. 시크릿 모드에서 테스트
3. Firebase Console에서 데이터베이스 탭 확인하여 데이터가 생성되는지 확인
