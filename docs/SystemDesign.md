# System Design

## High-Level Architecture

```text
User
  │
  ▼
Frontend (React)
  │
  ▼
Backend (Express)
  │
  ├── MongoDB
  ├── OpenAI
  └── Pinecone (Future)
```

### Responsibilities

#### Frontend (React)

* User Interface
* Authentication Pages
* Resume Upload
* Dashboard
* Results Display

#### Backend (Express)

* Authentication
* Business Logic
* Resume Processing
* AI Integration
* Database Communication

#### MongoDB

Stores:

* Users
* Resumes
* Analysis Results

#### OpenAI

Generates:

* ATS Feedback
* Skill Gap Suggestions
* Interview Questions

#### Pinecone (Future)

Stores vector embeddings for RAG.

---

## Client-Server Architecture

```text
Client (React)
      │
      ▼
HTTP Request
      │
      ▼
Server (Express)
      │
      ▼
MongoDB
```

Example Login Flow:

User
→ React Login Page
→ POST /api/auth/login
→ Express Server
→ MongoDB
→ JWT Generated
→ Response Returned

---

## REST API Overview

### Authentication APIs

POST /api/auth/signup

POST /api/auth/login

GET /api/auth/me

### Resume APIs

POST /api/resume/upload

GET /api/resume/:id

### Analysis APIs

POST /api/analysis/run

GET /api/analysis/:id

### Interview APIs

GET /api/interview/:analysisId

---

## JWT Authentication Flow

### Step 1

User enters email and password.

### Step 2

Backend validates credentials.

### Step 3

JWT token is generated.

### Step 4

Token is returned to frontend.

```json
{
  "token": "jwt_here"
}
```

### Step 5

Frontend stores token.

### Step 6

Protected requests send:

```text
Authorization: Bearer <token>
```

---

## Resume Analysis Flow

```text
User Uploads Resume
        │
        ▼
Express Server
        │
        ▼
PDF/DOCX Parser
        │
        ▼
Extract Resume Text
        │
        ▼
Skill Extraction
        │
        ▼
ATS Analysis
        │
        ▼
Save Results
        │
        ▼
Return Response
```

---

## Future AI Flow

```text
Resume
   │
   ▼
Extract Text
   │
   ▼
OpenAI
   │
   ▼
ATS Feedback
Skill Gap Analysis
Interview Questions
```

---

## Future RAG Flow

```text
Resume
   │
   ▼
Chunking
   │
   ▼
Embeddings
   │
   ▼
Pinecone
   │
   ▼
Retriever
   │
   ▼
LLM
   │
   ▼
Response Generation
```

---

## Backend Folder Structure

```text
backend/
└── src/
    ├── routes/
    ├── controllers/
    ├── services/
    ├── middleware/
    ├── models/
    ├── utils/
    └── config/
```

### Why Controllers and Services?

#### Controller

* Handles HTTP requests
* Sends HTTP responses

#### Service

* Contains business logic
* Interacts with database
* Generates JWT
* Processes resume analysis

Benefits:

* Maintainability
* Scalability
* Testability

```
```
