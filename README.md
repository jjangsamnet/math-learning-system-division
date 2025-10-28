# 나눗셈 마스터 v3.0 - 3학년 온라인 학습 시스템

나눗셈 학습을 위한 인터랙티브 웹 기반 학습 시스템입니다.

## 🎯 주요 기능

- **10단계 난이도 시스템**: 10으로 나누기부터 고난이도 나눗셈까지
- **가로셈 형식**: 직관적이고 간단한 문제 표시 (예: 72 ÷ 8 = __)
- **실시간 랭킹**: Firebase 기반 실시간 순위 및 점수 동기화
- **반별 관리**: 8개 반까지 독립적인 관리 가능
- **교사 모니터링**: 학생들의 진행 상황 실시간 확인
- **공개 랭킹 화면**: TV나 프로젝터로 전체 순위 표시

## 📁 파일 구조

```
project_division/
├── index.html              # 자동 리다이렉트 페이지
├── division-system.html    # 메인 나눗셈 학습 시스템
├── README.md              # 프로젝트 설명
└── FIREBASE_SETUP.md      # Firebase 설정 가이드
```

## 🚀 시작하기

### 1. 기본 사용 (로컬)
1. `division-system.html` 파일을 브라우저로 열기
2. 반 선택 후 이름 입력
3. 반별 접근 코드 입력 (기본값: 1111, 2222, ...)
4. 학습 시작!

### 2. Firebase 연동 필수 설정

⚠️ **중요**: Firebase Database 권한 설정이 필요합니다.

자세한 설정 방법은 [FIREBASE_SETUP.md](./FIREBASE_SETUP.md) 파일을 참조하세요.

**간단 요약:**
1. Firebase Console (https://console.firebase.google.com/) 접속
2. `multiplication-practice-2024` 프로젝트 선택
3. Realtime Database > 규칙 탭 선택
4. 다음 경로에 대한 읽기/쓰기 권한 추가:
   - `students_division`
   - `allStudents_division`
   - `activities_division`
   - `accessCodes_division`

### 3. GitHub Pages 배포

1. GitHub 저장소 설정 > Pages
2. Source를 "Deploy from a branch" 선택
3. Branch를 "master" 선택
4. 저장 후 배포 완료!

접속 URL: `https://jjangsamnet.github.io/math-learning-system-division/`

## 🎮 사용 방법

### 학생 모드
1. 반 선택 (1~8반)
2. 이름 입력
3. 반별 접근 코드 입력
4. 문제 풀이 시작
5. 정답 입력 후 "확인" 버튼 클릭

### 교사 모드
1. 로그인 화면에서 "교사 로그인" 버튼 클릭
2. 비밀번호 입력: `2025`
3. 모니터링 화면에서:
   - 실시간 학생 순위 확인
   - 반별 상세 랭킹 확인
   - 활동 로그 확인
   - 반별 접근 코드 관리
   - 반별 데이터 초기화

### 공개 모니터링 화면
1. 로그인 화면에서 "공개 모니터링" 버튼 클릭
2. TV나 프로젝터에 연결하여 전체 학생에게 순위 표시
3. 반별 필터링 가능

## 🎓 레벨 시스템

| 레벨 | 설명 | 예시 |
|------|------|------|
| Level 1 | 10으로 나누기 | 20÷10, 50÷10 |
| Level 2 | 간단한 나눗셈 | 15÷3, 20÷4 |
| Level 3 | 두 자리÷한 자리 | 45÷3, 72÷4 |
| Level 4-7 | 점진적 난이도 증가 | 범위별 나눗셈 |
| Level 8-9 | 큰 수 나눗셈 | 100 이상의 수 |
| Level 10 | 최고 난이도 | 고급 나눗셈 |

## 🏆 점수 시스템

- 정답: +10점
- 3연속 정답: +40점 (10점 + 30점 보너스)
- 오답: -50점 + 레벨 하락
- 레벨 상승: 10문제 연속 정답 필요

## 🔧 기술 스택

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Backend**: Firebase Realtime Database
- **호스팅**: GitHub Pages

## 📊 데이터 구조

Firebase Realtime Database 구조:
```
multiplication-practice-2024/
├── students_division/
│   └── class{1-8}/
│       └── {studentName}/
│           ├── name
│           ├── class
│           ├── level
│           ├── score
│           └── lastUpdated
├── allStudents_division/
│   └── {classNum}_{studentName}/
├── activities_division/
│   └── {activityId}/
└── accessCodes_division/
    └── class{1-8}
```

## 🔐 보안 설정

기본 접근 코드:
- 1반: 1111
- 2반: 2222
- 3반: 3333
- ... (8반까지)

교사 비밀번호: `2025`

⚠️ **프로덕션 환경에서는 반드시 변경하세요!**

## 🐛 문제 해결

### "permission_denied" 오류
→ [FIREBASE_SETUP.md](./FIREBASE_SETUP.md) 참조하여 Firebase 규칙 설정

### 로그인이 안 됨
1. 브라우저 콘솔(F12) 확인
2. Firebase 연결 상태 확인 (우측 상단)
3. 접근 코드가 올바른지 확인

### 랭킹이 업데이트되지 않음
1. Firebase 연결 상태 확인
2. 페이지 새로고침 (Ctrl+F5)
3. Firebase Console에서 데이터 확인

## 📝 변경 이력

### v3.0 (2025-10-28)
- 곱셈에서 나눗셈으로 변환
- 가로셈 형식 적용
- Firebase 데이터 경로 분리
- 상세 디버깅 로그 추가
- 접근 코드 저장/로드 로직 개선

## 🤝 관련 프로젝트

- [곱셈 학습 시스템](https://github.com/jjangsamnet/math-learning-system)

## 📄 라이선스

이 프로젝트는 교육 목적으로 자유롭게 사용 가능합니다.

## 💡 지원

문제가 발생하면:
1. [FIREBASE_SETUP.md](./FIREBASE_SETUP.md) 확인
2. 브라우저 콘솔 로그 확인
3. GitHub Issues에 문의

---

🤖 Generated with [Claude Code](https://claude.com/claude-code)
