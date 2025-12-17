# 오픈소스SW의이해 프로젝트

파이어베이스 Auth를 이용한 회원가입/로그인 예제입니다. 앱 실행 시 인증 상태에 따라 화면을 전환하고, 회원가입 시 이메일 인증을 거쳐 로그인하도록 구성했습니다.

## 주요 플로우
- 앱 실행 → Firebase 초기화 후 로그인 여부 확인
- 미로그인 시 로그인 화면으로 이동 (아이디/비밀번호 입력)
- 로그인 화면 하단의 **회원가입** 버튼을 눌러 회원가입 화면으로 전환
- 회원가입 화면에서 아이디, 이메일, 비밀번호, 이름, 닉네임 입력
- Firebase Auth로 계정 생성 후 이메일 인증 메일 발송, Firestore `users` 컬렉션에 프로필 저장
- 회원가입 완료 시 로그아웃 후 로그인 화면으로 복귀 (이메일 인증 후 로그인)
- 로그인 성공 시 메인 화면으로 이동, 설정 탭에서 로그아웃 가능

## 사전 준비
1. Flutter 및 Firebase CLI 설치
2. Firebase 프로젝트 생성 후 `firebase_core`, `firebase_auth`, `cloud_firestore` 활성화
3. `flutterfire configure`를 실행해 `lib/firebase_options.dart`를 생성하거나 이 저장소의 템플릿 값을 실제 프로젝트 키로 교체

## 실행 방법
```bash
flutter pub get
flutter run
```

## 파일 구조
- `lib/main.dart`: 화면 전환, 로그인/회원가입/이메일 인증/메인/설정 화면 구현
- `lib/firebase_options.dart`: Firebase 설정 (플랫폼별 키를 실제 값으로 교체 필요)
- `pubspec.yaml`: Flutter 및 Firebase 의존성 정의
