# Capstone Sprint 2 (Backend) Verification Report

**Emganwini Nedbank Hub | Master Project Portfolio**  
*Capstone Sprint 2 (Backend Deliverable)*

---

## 🛠️ Backend System Verification

All backend modules are fully implemented, verified, and operational within the [`../../phase-02-backend-development/backend`](../../phase-02-backend-development/backend) workspace.

### 1. All Relational Models (Prisma ORM)
- `User`: Handles identity, email uniqueness, hashed passwords, and role-based permissions (`CLIENT`, `ADVISOR`, `ADMIN`).
- `Profile`: Financial profiles (credit rating, monthly income, names).
- `Post` & `Category`: Financial advisory articles with many-to-many topic mapping (`PostCategory`).
- `Conversation` & `Message`: Session memory tracking token metrics and role messages (`USER`, `ASSISTANT`, `SYSTEM`).

### 2. All CRUD Routes
- **Users**: `GET /api/users`, `GET /api/users/:id`, `POST /api/users`, `PUT /api/users/:id`, `DELETE /api/users/:id`
- **Posts**: `GET /api/posts`, `GET /api/posts/:id`, `POST /api/posts`, `PUT /api/posts/:id`, `DELETE /api/posts/:id`
- Error codes verified: `200`, `201`, `204`, `400`, `401`, `404`, `409`, `500`.

### 3. JWT Authentication
- `POST /api/auth/register`: Hashes passwords with bcrypt (10 rounds) and generates JWT.
- `POST /api/auth/login`: Verifies hash and issues signed token.
- `GET /api/auth/me`: Decodes token and returns identity payload.
- `authenticateToken`: Reusable Express middleware guarding sensitive routes.

### 4. AI Endpoints
- `POST /api/ai/chat`: Interactive copilot with conversation history.
- `POST /api/ai/summarize`: 3-sentence financial disclosure summarizer.
- Integrated sliding window rate limiter (`aiRateLimiter`).

### 5. RAG Implementation
- `POST /api/ai/rag`: Vector similarity search against 2,500-word Nedbank knowledge base.
- Returns grounded answer with chunk citations and snippet references.
