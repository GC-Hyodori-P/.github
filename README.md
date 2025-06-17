# 효도리 (Hyodori) Wiki

---

## 📘 Overview

**효도리**는 부모님과 자녀 간의 원활한 소통과 정서적 유대를 강화하기 위해 개발된 **가족 커뮤니케이션 앱**입니다.  
사용자는 가족 구성원과의 일상적인 대화를 나누고, 사진과 음성 메시지를 공유하며, 일정과 건강 정보를 함께 관리할 수 있습니다.

**주요 목적**:
- 가족 간의 정서적 유대 강화
- 부모님의 일상과 건강 상태 공유
- 간편한 커뮤니케이션 도구 제공

---

## 🛠 Tech Stack

### 📡 Backend (Spring Boot)
- **Language**: Java
- **Framework**: Spring Boot
- **Database**: MySQL
- **Security**: Spring Security (JWT 기반 인증)
- **Build Tool**: Gradle
- **Documentation**: Swagger

### 📱 iOS App
- **Language**: Swift
- **Framework**: SwiftUI, Combine
- **Network Layer**: URLSession, Codable
- **State Management**: MVVM
- **Dependency Management**: Swift Package Manager (SPM)

---

## ✨ Features

| 기능                   | 설명                                                                 |
|------------------------|----------------------------------------------------------------------|
| **건강 정보 공유**         | 부모님의 건강 상태를 기록하고 자녀와 공유할 수 있습니다.                    |
| **긴급 알림**             | 위급 상황 시 가족에게 긴급 알림을 보낼 수 있습니다.                        |
| **다크모드 지원 (iOS)**    | 사용자 환경에 따라 테마 자동 전환                                         |
| **푸시 알림**             | 일정, 메시지, 건강 등 주요 이벤트에 대해 실시간 알림 제공                   |
| **접근성 강화**           | 큰 글씨, 음성 안내 등 고령자 친화적 UI/UX 제공                             |
| **보안/개인정보**         | 모든 데이터 암호화 저장, 개인정보 최소 수집 및 보호 정책 준수                |
| **가족 그룹 생성 및 관리** | 가족 구성원을 초대하고 그룹을 관리할 수 있습니다.  (추후 개발 예정)                      |
| **일상 공유**             | 사진과 음성 메시지를 통해 일상을 공유할 수 있습니다. (추후 개발 예정)                |
| **일정 관리**             | 가족 간의 중요한 일정을 함께 관리하고 알림을 받을 수 있습니다. (추후 개발 예정)        |

---

## 🧩 Architecture

```
+-------------+     REST API     +----------------+
|   iOS App   | <--------------> | Spring Server  |
+-------------+                  +----------------+
      |                                 |
      |    Network 통신 (JSON, HTTPS)    |
      v                                 v
+------------+                  +-------------------+
| SwiftUI UI |                  | MySQL Database    |
+------------+                  +-------------------+
```

- iOS 앱과 백엔드는 RESTful API로 통신합니다.
- 인증은 JWT 방식이며, 서버에서 토큰 발급/검증을 수행합니다.
- 클라이언트는 MVVM 아키텍처로 구성되어 있어 데이터 흐름이 명확합니다.

---

## 🔑 인증 및 보안

- **JWT 기반 인증**: 로그인/회원가입 시 JWT 토큰 발급, 모든 API 요청에 토큰 필요
- **OAuth2 소셜 로그인(확장 가능)**: 추후 Apple, Google 등 연동 고려
- **데이터 암호화**: 민감 정보는 서버-클라이언트 간 HTTPS로 암호화 전송
- **권한 분리**: 가족 관리자는 그룹 관리, 일반 사용자는 제한된 기능

---

## 🚀 Getting Started

### Backend

```bash
# 프로젝트 클론
git clone https://github.com/hyodori/hyodori-backend.git

# 환경변수 설정 (.env 또는 application.yml)

# 빌드 및 실행
./gradlew bootRun
```

### iOS App

```bash
# 프로젝트 클론
git clone https://github.com/hyodori/hyodori-ios.git

# Xcode에서 열기
open Hyodori.xcodeproj
```

---

## 📂 API Documentation

API 문서는 Swagger를 통해 제공됩니다.

- 접속 주소: `http://localhost:8080/swagger-ui/index.html`
- 주요 엔드포인트:
  - `POST /auth/login`
  - `POST /auth/signup`
  - `GET /family`
  - `POST /messages`
  - `PUT /health/{userId}`

---

## 📱 iOS App Structure

```
Hyodori/
├── Views/
├── ViewModels/
├── Models/
├── Network/
│   └── APIService.swift
├── Resources/
│   └── Assets.xcassets
├── Utils/
├── App.swift
```

- `ViewModels`: 각 화면의 상태 관리
- `Network`: API 통신 모듈
- `Utils`: 공통 유틸리티 함수 및 확장

---

## 📊 데이터 흐름 예시

1. **긴급 알림**
   - 부모님이 긴급 버튼 클릭 → 서버에서 가족 전체에 푸시 + 위치 정보 전송
2. **건강 정보 기록**
   - 부모님이 혈압 입력 → iOS 앱에서 서버로 POST → 자녀 앱에 실시간 반영 및 알림
3. **가족 초대** (추후 개발 예정)
   - 관리자가 초대 코드 생성 → 자녀가 앱에서 코드 입력 → 서버에서 가족 그룹에 추가

---

## 🧑‍💻 협업 및 유지보수

- **코드 컨벤션**: Java/Kotlin, Swift 스타일 가이드 준수
- **이슈 관리**: Github Issues, PR 템플릿 활용
- **문서화**: Swagger(백엔드), README 및 Wiki(iOS/공통)
- **테스트**: JUnit(Spring), XCTest(iOS) 활용

---

## 🔗 참고 및 확장 방향

- **Wearable 연동**: Apple Watch, 건강 기기 등 확장 가능
- **웹 대시보드**: 가족 건강/일정 통합 관리용 웹 서비스 개발 가능
- **AI 추천**: 건강 관리, 일정 추천 등 스마트 기능 추가 가능

---

## 📄 License

본 프로젝트는 MIT License 하에 배포됩니다. 자세한 내용은 [LICENSE](../blob/main/LICENSE) 파일을 참고하세요.

---

## ❓ FAQ

- **Q. 부모님이 스마트폰 사용이 익숙하지 않은데, 어떻게 도와드릴 수 있나요?**  
  A. 앱 내 튜토리얼, 큰 글씨, 음성 안내 등 접근성 기능을 제공합니다.

- **Q. 건강 정보는 안전하게 저장되나요?**  
  A. 모든 건강 데이터는 암호화되어 저장 및 전송됩니다.

- **Q. 가족 초대/가입이 어려워요.**  
  A. 초대 코드를 활용한 간편 가입 절차를 제공합니다.
