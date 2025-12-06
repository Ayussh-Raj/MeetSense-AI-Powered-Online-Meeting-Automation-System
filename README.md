# MeetSense – AI-Powered Online Meeting Automation System

## 1. Problem Statement

Modern online meetings generate a huge amount of information: discussions, decisions, action items, and participant reactions. Most of this is lost or manually captured in notes, which is:

- Time-consuming and error-prone
- Difficult to analyze across multiple meetings
- Poor at capturing engagement/emotion in real time

**MeetSense** aims to automate meeting workflows using AI:

- Capture key moments and decisions automatically
- Track facial expressions and engagement during meetings
- Generate post-meeting analytics and insights
- Provide searchable history of meetings, transcripts, and notes

## 2. Model / Module Architecture

At a high level, the system is split into three main parts:

- **Frontend (React/Vite)**  
  - Meeting UI (video tiles, controls, chat)  
  - Authentication and dashboard  
  - Emotion capture client running in the browser  
  - Displays real-time emotion analytics and meeting insights

- **Backend (Node.js/Express + MongoDB)**  
  - REST APIs for auth, meetings, analytics, users, AI notes, etc.  
  - Socket.IO server for real-time events (chat, presence, emotion events)  
  - Persists meetings, transcripts, participants, analytics metadata

- **AI & Emotion Pipeline**  
  - Browser captures frames and sends them to backend `/api/detect/frame`  
  - Backend runs emotion detection and stores per-frame predictions  
  - Aggregated analytics exposed through `/api/emotion-analytics/...` endpoints

## 3. UML Diagrams (Placeholders)

### 3.1 Use Case Diagram (Placeholder)

> TODO: Insert UML use case diagram showing primary actors (Host, Participant) and core use cases (Create Meeting, Join Meeting, View Analytics, etc.).

### 3.2 Sequence Diagram (Placeholder)

> TODO: Insert UML sequence diagram for a typical meeting flow (User joins meeting → media setup → emotion capture → analytics generation → post-meeting review).

## 4. How to Install & Run

### 4.1 Prerequisites

- Node.js (LTS recommended) and npm  
- MongoDB instance (local or remote)  
- Git (to clone the repository)

### 4.2 Clone the Repository

```bash
git clone <your-fork-or-origin-url>
cd MeetSense
```

### 4.3 Backend Setup

From the `backend` directory:

```bash
cd backend
npm install
```

Create or update `.env` in `backend/` with at least:

```env
PORT=5000
MONGO_URI=<your_mongodb_connection_string>
JWT_SECRET=<your_jwt_secret>
CLIENT_URL=http://localhost:5173
FRONTEND_URL=http://localhost:5173
```

Run the backend:

```bash
npm run dev   # or: npm start
```

### 4.4 Frontend Setup

From the `frontend` directory:

```bash
cd ../frontend
npm install
```

Create or update `.env` in `frontend/` with the API base URL (adjust host/port as needed, e.g. LAN IP):

```env
VITE_API_URL=http://localhost:5000/api
```

Run the frontend:

```bash
npm run dev
```

The app will be available at `http://localhost:5173` by default.

## 5. Directory Structure

High-level structure of this repository:

```bash
.
├── backend/                    # Node.js/Express backend (APIs, sockets, models)
├── frontend/                   # React/Vite frontend (UI, emotion client)
├── EMOTION_DETECTION_README.md # Additional notes on emotion detection pipeline
├── docker-compose.emotion.yml  # Docker compose for emotion detection services
├── Dockerfile.emotion          # Dockerfile for emotion-related services
├── package.json                # Root scripts and shared tooling
├── package-lock.json
├── debug-output/               # Debug artifacts
└── README.md                   # This file
```

Refer to `backend/README.md` and `frontend/README.md` for more detailed, layer-specific structures.

## 6. Maker
- Ayush Raj  
