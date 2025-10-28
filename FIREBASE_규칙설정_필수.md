# ⚠️ Firebase Database 규칙 설정 (필수)

## 현재 문제
`permission_denied` 오류가 계속 발생하고 있습니다. 이는 Firebase Realtime Database의 보안 규칙이 설정되지 않아서입니다.

## 즉시 해결 방법 (5분 소요)

### 1단계: Firebase Console 접속
1. 브라우저에서 https://console.firebase.google.com/ 열기
2. Google 계정으로 로그인
3. **"multiplication-practice-2024"** 프로젝트 클릭

### 2단계: Realtime Database 메뉴 이동
1. 왼쪽 사이드바에서 **"빌드"** 또는 **"Build"** 클릭
2. 하위 메뉴에서 **"Realtime Database"** 클릭
3. 상단 탭에서 **"규칙"** 또는 **"Rules"** 클릭

### 3단계: 규칙 편집
현재 규칙이 아마 다음과 같을 것입니다:
```json
{
  "rules": {
    "students": {
      ".read": true,
      ".write": true
    },
    "allStudents": {
      ".read": true,
      ".write": true
    },
    "activities": {
      ".read": true,
      ".write": true
    },
    "accessCodes": {
      ".read": true,
      ".write": true
    }
  }
}
```

**이것을 다음과 같이 변경하세요** (복사해서 붙여넣기):
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

### 4단계: 규칙 게시
1. 우측 상단의 **"게시"** 또는 **"Publish"** 버튼 클릭
2. 확인 창이 나오면 **"예"** 클릭

### 5단계: 확인
1. division-system.html 페이지로 돌아가기
2. **Ctrl + Shift + R** (또는 Cmd + Shift + R) 눌러 강력 새로고침
3. 브라우저 콘솔(F12)에서 다음 메시지 확인:
   - ✅ 접근 코드 저장 완료
   - ✅ 기본 접근 코드 설정 완료

## 대안: 모든 권한 열기 (빠른 테스트용)

테스트를 위해 임시로 모든 접근을 허용하려면:

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

⚠️ **주의**: 이 설정은 보안이 없으므로 테스트용으로만 사용하세요!

## 여전히 작동하지 않는 경우

### 확인 사항
1. Firebase Console에서 프로젝트가 맞는지 확인
   - 프로젝트 ID: `multiplication-practice-2024`

2. Realtime Database가 활성화되어 있는지 확인
   - Database URL: `https://multiplication-practice-2024-default-rtdb.asia-southeast1.firebasedatabase.app`

3. 브라우저 캐시 완전 삭제
   - Chrome: 설정 > 개인정보 및 보안 > 인터넷 사용 기록 삭제
   - 전체 기간 선택
   - "캐시된 이미지 및 파일" 체크
   - 삭제 후 브라우저 재시작

4. 시크릿/비공개 모드에서 테스트

## Firebase Console 접근 권한이 없는 경우

Firebase 프로젝트의 소유자나 관리자에게 연락하여:
1. Firebase Console 접근 권한 요청
2. 위의 Database 규칙 수정 요청

## 스크린샷 가이드

### 규칙 설정 화면 찾기:
```
Firebase Console
├── 프로젝트 선택: multiplication-practice-2024
├── 왼쪽 메뉴
│   └── 빌드 (Build)
│       └── Realtime Database
│           └── 규칙 (Rules) 탭
└── 편집기에서 규칙 수정 → 게시 버튼 클릭
```

## 추가 도움

여전히 문제가 해결되지 않으면:
1. Firebase Console 스크린샷 캡처
2. 브라우저 콘솔 전체 로그 복사
3. 문의

---

**이 작업은 반드시 Firebase Console 웹사이트에서 직접 수행해야 합니다.**
**코드 수정으로는 해결할 수 없습니다.**
