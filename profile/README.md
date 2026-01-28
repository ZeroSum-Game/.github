# 🎲 ZeroSum Game

**ZeroSum Game**은 실시간 멀티플레이 환경에서 자산의 증감이 항상 균형(Zero-Sum)을 이루도록 설계된 웹 기반 게임 서비스입니다.
프론트엔드(FE)와 백엔드(BE)를 분리한 구조로, 실시간 소켓 통신과 게임 로직을 중심으로 구현되었습니다.

---

## 📌 Project Overview

* **프로젝트 유형**: Full-Stack Web Game
* **핵심 개념**: 한 플레이어의 이득은 다른 플레이어의 손실로 귀결되는 Zero-Sum 구조
* **주요 목표**

  * 실시간 게임 상태 동기화
  * 명확한 게임 로직 분리 및 서버 중심 상태 관리
  * FE/BE 역할 분리를 통한 확장 가능한 구조 설계

---

## 🧩 Architecture Overview

```
[ Client (FE) ]
   │  REST API / WebSocket
   ▼
[ Server (BE) ]
   ├─ Game Logic
   ├─ Market / Rule Engine
   ├─ Auth & Session
   └─ Socket Event Handler
```

* **Frontend**: 사용자 입력 및 게임 상태 시각화
* **Backend**: 게임 규칙, 상태 판단, 실시간 이벤트 브로드캐스팅

---

## 🛠️ Tech Stack

### Frontend (zerosumgame-FE)

* TypeScript
* Vite
* React
* Tailwind CSS
* Socket.IO Client

### Backend (zerosumgame-BE)

* Node.js
* Express
* Socket.IO
* Prisma (DB ORM)
* Session / Auth Middleware

---

## 📂 Repository Structure

### Frontend

```
zerosumgame-FE/
├─ public/
├─ src/
│  ├─ components/
│  ├─ pages/
│  ├─ services/
│  ├─ store/
│  └─ utils/
├─ vite.config.ts
├─ tsconfig.json
└─ package.json
```

### Backend

```
zerosumgame-BE/
├─ prisma/
│  └─ schema.prisma
├─ public/
├─ server.js
├─ socketHandler.js
├─ gameLogic.js
├─ market.js
├─ auth.js
└─ package.json
```

---

## 🔄 FE ↔ BE Communication Flow

1. 클라이언트가 게임 액션을 API 또는 Socket Event로 전송
2. 서버에서 게임 로직 검증 및 상태 업데이트
3. 변경된 게임 상태를 모든 참여자에게 실시간 브로드캐스트
4. FE는 서버 상태를 기준으로 UI를 재렌더링

> **게임 상태의 Single Source of Truth는 서버**로 유지됩니다.

---

## 🔐 Authentication & Session

* 서버에서 세션 기반 사용자 식별 관리
* 소켓 연결 시 사용자 인증 정보 검증
* 비정상적인 상태 요청 차단 및 서버 기준 상태 유지

---

## 🚀 Local Development

### 1️⃣ Backend 실행

```bash
cd zerosumgame-BE
npm install
npm run start
```

### 2️⃣ Frontend 실행

```bash
cd zerosumgame-FE
npm install
npm run dev
```

> FE와 BE를 **동시에 실행**해야 정상 동작합니다.

---

## 💡 Key Design Decisions

* **게임 로직은 전부 서버에서 처리**
* 클라이언트는 결과를 “계산”하지 않고 “표현”만 담당
* 실시간성 요구 사항을 고려해 WebSocket 기반 구조 채택
* FE/BE 완전 분리를 통한 협업 및 유지보수 용이성 확보

---

## 👥 Team

| Name | Role                  |
| ---- | --------------------- |
| 신원영  | Frontend / Game Logic |
| 전하은   | Backend / Infra       |

---

## 📈 Future Improvements

* JWT 기반 인증 구조로 확장
* 게임 리플레이 기능
* 매칭 시스템 고도화
* 상태 이상 탐지 및 보안 강화

---

## 📄 License

This project is for educational and portfolio purposes.
