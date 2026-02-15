# Mern-job-tracker-back-end-project
Here is your **final backend README** with **drag & drop mentioned but without order persistence**.
It is **copy-paste ready**.

---

# 📦 CareerBoards API — Backend

CareerBoards is a full-stack MERN job tracking application that helps users manage job applications using a kanban-style workflow.

This repository contains the **Node.js + Express + MongoDB REST API** that powers:

* User authentication
* Job card CRUD operations
* Notes per job
* Job status updates for drag-and-drop columns

---

## 🚀 Features

* 🔐 JWT Authentication

  * Sign up
  * Sign in
  * Protected routes
* 💼 Full CRUD for job cards
* 📝 Notes tied to a specific job (`/jobs/:jobId`)

  * Create note
  * Delete note
* 🧲 Drag & drop support

  * Job cards store a **status field** (kanban column)
  * Status updates are saved to MongoDB
* 👤 User-scoped data (users only access their own jobs)
* ❗ Proper HTTP status codes (401, 404, 500)

---

## 🧰 Tech Stack

* Node.js
* Express
* MongoDB
* Mongoose
* JSON Web Token (JWT)
* bcrypt
* cors
* morgan
* dotenv

---

## 📁 Project Structure

```
controllers/
middleware/
models/
server.js
```

---

## ⚙️ Environment Variables

Create a `.env` file in the root:

```env
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
```

---

## ▶️ Installation & Setup

```bash
git clone https://github.com/jaydendavis746-debug/Mern-job-tracker-back-end-project.git
cd Mern-job-tracker-back-end-project
npm install
npm run dev
```

Server runs on:

```
http://localhost:3000
```

---

## 🔐 Authentication

### Sign Up

```
POST /auth/sign-up
```

**Body**

```json
{
  "username": "testuser",
  "password": "password123"
  "confirm-password": "password123"
}
```

---

### Sign In

```
POST /auth/sign-in
```

**Response**

```json
{
  "token": "JWT_TOKEN_HERE"
}
```

Use the token for protected routes:

```
Authorization: Bearer <token>
```

---

## 💼 Job Card Endpoints (Protected)

### Get all jobs for the logged-in user

```
GET /jobs
```

---

### Get a single job

```
GET /jobs/:jobId
```

Returns `404` if the job does not exist or does not belong to the user.

---

### Create a job

```
POST /jobs
```

**Body example**

```json
{
  "position": "Frontend Developer",
  "companyName": "Tech Co",
  "location": "London",
  "salary": 45000,
  "jobType": "Full-time",
  "workArrangement": "Hybrid",
  "description": "React role",
  "status": "Applied"
}
```

---

### Update a job

```
PUT /jobs/:jobId
```

Used for:

* Editing job details
* Updating **status** when a card is moved between columns (drag & drop)

---

### Delete a job

```
DELETE /jobs/:jobId
```

---

## 📝 Notes Endpoints (Per Job)

Notes are **nested under a specific job** and are only accessible to the job owner.

---

### Create a note

```
POST /jobs/:jobId/notes
```

**Body**

```json
{
  "text": "Follow up next week"
}
```

---

### Delete a note

```
DELETE /jobs/:jobId/notes/:noteId
```

---

## 🔒 Authorization Rules

* All job and note routes require a valid JWT
* Users can only access **their own jobs**
* Notes can only be created or deleted on jobs owned by the user

---

## 🧱 Data Model Overview

```
User
 └── Jobs (one-to-many)
       ├── status (Applied | Interview | Offer | Rejected)
       └── Notes (one-to-many)
```

* `status` determines the kanban column
* Drag & drop updates the job’s `status`

---

## ❗ Error Handling

The API returns appropriate HTTP status codes:

| Status | Meaning                              |
| ------ | ------------------------------------ |
| 401    | Unauthorized (missing/invalid token) |
| 404    | Job or note not found                |
| 400    | Validation error                     |
| 500    | Server error                         |



---

## 🧪 Testing

Test endpoints using:

* Postman
* Include the JWT token for all protected routes.

---
# 🔗 Frontend Repository

The frontend repository can be found here:
👉 [https://github.com/jaydendavis746-debug/Mern-job-tracker-front-end-project](https://github.com/jaydendavis746-debug/Mern-job-tracker-front-end-project)

---

## 📌 Future Improvements

* Edit a singular note instead of having an array of notes and deleting the outdated notes
* Persist card ordering within columns
* File uploads (CV / cover letter)
* Job analytics dashboard


---

## 👤 Author
* Built by **jaydendavis746-debug** as a MERN portfolio project.
* With the collaboration of ranjith-jacob

**CareerBoards — MERN Job Tracker**
Full-stack portfolio project demonstrating authentication, protected routes, kanban drag-and-drop status updates, and nested resources.

---

