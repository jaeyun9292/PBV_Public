<img width=900px src="https://github.com/user-attachments/assets/60a14b95-acd8-4b22-9157-26f17ffbb9f6">

> **스마트폰을 차량 내 무빙 스크린과 연결해 멀티스크린 환경을 제공하는 애플리케이션  -  PBV**

## 🔹 서비스 소개

PBV 앱을 사용하면, 무빙 스크린에는 넷플릭스, 유튜브 등 원하는 컨텐츠를 띄워 大화면에서 감상할 수 있고, 
 
동시에 스마트폰에서는 웹서핑이나 메시지 확인 등 개인 작업을 병행할 수 있습니다. 
 
에어 마우스, 음성 비서, AI 번역 등 다양한 인터랙션 기능을 지원하여, 
 
탑승자가 차량에서 손쉽고 직관적인 조작이 가능하도록 설계하였습니다.

<br>

## 🔹 주요 기능

- **에어 마우스**  
스마트폰 카메라로 손 제스처를 인식하여 서브 디스플레이의 커서를 이동하고 액션을 제어합니다.
    
- **음성 비서 호출**  
호출 키워드 "하이 애니"를 인식하면 음성 명령 대기 상태로 진입하며, <br>
“유튜브 틀어줘”, “번역기 실행” 등 자연어 명령어를 통해 기능을 실행할 수 있습니다.
    
- **AI 번역기**  
AI가 사용자의 음성을 사전에 지정한 언어로 번역하고, 번역 결과를 음성과 텍스트로 동시에 출력합니다.
    
- **캐스트 / 미러링**  
앱 화면을 서브 디스플레이에 캐스트하고, 필요 시 미러링 모드로 전환해 컨텐츠를 동기화할 수 있습니다.

<br>

## 🔹 실행 화면

- ### 스마트폰 UI

| <img src="https://github.com/user-attachments/assets/6ee82e16-86ae-40ac-a7be-63d94ca7a797" width="150" height="330"/> | <img src="https://github.com/user-attachments/assets/1b3f4b79-2209-43e4-8621-3c5d4b91f651" width="150" height="330"/> | <img src="https://github.com/user-attachments/assets/b5ea2777-e58c-4e5f-b5df-0d435e12e273" width="150" height="330"/>| <img src="https://github.com/user-attachments/assets/5b745dbc-39eb-43bf-ba61-13bc228dbf7f" width="150" height="330"/> 
|:---:|:---:|:---:|:---:|
| **스플래시 화면** | **권한 허용** | **디스플레이 연결 안내** | **홈 화면** |

| <img src="https://github.com/user-attachments/assets/36e0a598-2362-44e4-8ea4-4193bb75c53a" width="150" height="330"/> | <img src="https://github.com/user-attachments/assets/a467f6ad-559c-4c89-aa3e-4378a75fc158" width="150" height="330"/> | <img src="https://github.com/user-attachments/assets/96c317d1-c95b-40df-bc83-ea13985035b0" width="150" height="330"/> |<img src="https://github.com/user-attachments/assets/a8f0b0a6-55e6-4ae0-bf5a-fc9a2a22d4d8" width="150" height="330"/>
|:---:|:---:|:---:|:---:|
| **번역 화면** | **번역 언어 선택** | **ROI 설정** | **터치 패드** | 

<br>

- ### 서브디스플레이 UI

| <img src="https://github.com/user-attachments/assets/bc4dc6ea-9b5c-44f5-bb50-bda515dd966a" width="650"/> |
|:---:|
| **홈 화면** |

| <img src="https://github.com/user-attachments/assets/0e67e46a-a67c-47bf-bb22-57ead491af69" width="650"/> |
|:---:|
| **뮤직 화면** |

| <img src="https://github.com/user-attachments/assets/2961a999-a41d-4235-a7e6-2ed9df8fed4e" width="650"/> |
|:---:|
| **에어마우스 동작 화면** |

<br>

## 🔹 아키텍처 개요
- **Coroutines**
- **Hilt (DI)**
- **Jetpack Navigation**
- **MVVM + Clean Architecture**

<img src="https://github.com/user-attachments/assets/45a69dc7-b5b1-499b-a0c4-b114509ea5db" width="800">

> ### Clean Architecture

- **Data Layer**  
  외부 모듈과 통신하거나 로컬 DB에 접근하는 역할을 담당합니다.  
  Repository 구현체, DTO, DataSource 등을 포함합니다.

- **Domain Layer**  
  앱의 핵심 비즈니스 로직을 담당하며, View나 Data Layer에 직접 의존하지 않습니다.  
  UseCase, Entity, Repository Interface로 구성됩니다.

- **Presentation Layer**  
  UI 렌더링과 상태 관리를 담당합니다.  
  View와 ViewModel은 MVVM 패턴을 기반으로 연결되며, 사용자 입력은 ViewModel을 통해 처리됩니다.

> ### MVVM + Coroutines

- `StateFlow`와 `SharedFlow`를 활용하여 UI 상태 및 이벤트를 비동기적으로 처리했습니다.
- `View → ViewModel → UseCase → Repository`의 단방향 데이터 흐름을 유지하여 아키텍처를 설계했습니다.  
- 화면 전환은 Fragment 기반 UI와 Navigation Component를 통해 구조적으로 관리했습니다.


> ### Dependency Injection

- **Hilt**를 사용하여 객체 생명주기와 의존성을 효율적으로 관리했습니다.  
- ViewModel, UseCase, Repository 등 주요 컴포넌트 간의 결합도를 낮추고 테스트 용이성을 확보했습니다.

<br>

## 🔹 폴더 구조

```jsx
PBVApp-AOS/
├── 📁 app
│   ├── presentation/
│   └── di/
│
├── 📁 build/
│   └── build:convention
│
├── 📁 common/
│   ├── util/
│   ├── constants/
│   ├── extensions/
│   ├── base/
│   └── view/
│
├── 📁 data/
│   ├── di/
│   ├── model/
│   ├── retrofit/
│   ├── bluetooth/
│   ├── service/
│   ├── repository/
│   └── database/
│
├── 📁 domain/
│   ├── model/
│   ├── usecase/
│   └── repository/
│
├── 📁 feature:airmouse/             
│   ├── presentation/               
│   ├── model/
│   └── di/
│
├── 📁 feature:kws/
│   ├── presentation/
│   ├── model/
│   └── di/
│
├── ...
```

<br>

## 🔹 사용 기술 및 라이브러리

| **라이브러리 (Library)** | **사용 목적 (Purpose)** |
| ------------------------ | ------------------------ |
| Jetpack Navigation       | 화면 전환 관리 |
| Hilt                     | 의존성 주입 |
| Coroutine                | 비동기 처리 |
| MediaRouter              | 오디오 출력 제어 |
| ExoPlayer                | 서브 디스플레이 동영상 재생 |
| androidx-webkit          | JS ↔ Native 연동 |
| Retrofit                 | API 통신 |
| Gson                     | JSON 변환 |
| Bluetooth API            | BLE 통신 |
| AzureKws                 | 키워드 음성 인식 |
| Google STT/TTS           | 음성 변환 처리 |
| OpenAI                   | 번역 API |
| MediaPipe                | 손 관절 추론 |
| JD-GUI                   | 라이브러리 디컴파일 |
