# PrepPilot - AI Interview Preparation Platform

An AI-powered interview preparation platform that helps users analyze their resumes and practice domain-based mock interviews with AI-generated questions and feedback.

The application combines a **Next.js frontend** with a **Node.js/Express backend**, MongoDB for data storage, and the Groq API for AI-powered resume analysis and interview evaluation.

---

## Features

### 🔐 User Authentication

* User registration and login
* Password hashing using bcrypt
* JWT-based authentication
* Protected application routes

### 📄 Resume Analysis

* Upload a resume in PDF format
* Extract resume content
* Analyze the resume using AI
* Identify:

  * Candidate summary
  * Experience level
  * Technical skills
  * Strengths
  * Recommended interview domains
  * Confidence/recommendation information

### 🎯 AI Mock Interviews

* Select an interview domain
* Start an AI-generated mock interview
* Receive interview questions dynamically
* Submit answers
* Receive AI-generated evaluation and feedback
* Continue with the next question
* Receive a final interview score

### 📊 Interview History

* Store completed interviews in MongoDB
* View previous interview sessions
* Review interview questions, answers, feedback, and scores

---

## Tech Stack

### Frontend

* **Next.js**
* **React**
* **TypeScript**
* **Tailwind CSS**
* **Radix UI**
* **Axios**
* **Lucide React**

### Backend

* **Node.js**
* **Express.js**
* **MongoDB**
* **Mongoose**
* **JWT**
* **bcryptjs**
* **Multer**
* **PDF.js**

### AI

* **Groq API**
* Configurable Groq model through environment variables
---

## Application Workflow

```text
                    ┌─────────────────┐
                    │      User       │
                    └────────┬────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │   Next.js Frontend  │
                  └──────────┬──────────┘
                             │
                    HTTP Requests
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Express.js Backend  │
                  └──────────┬──────────┘
                             │
             ┌───────────────┼────────────────┐
             │               │                │
             ▼               ▼                ▼
        Authentication   Resume Analysis   Interviews
             │               │                │
             │               ▼                ▼
             │          Groq API          Groq API
             │
             ▼
          MongoDB
```

---

## API Routes

### Authentication

```text
POST /api/auth/register
```

Register a new user.

```text
POST /api/auth/login
```

Authenticate an existing user.

```text
GET /api/auth/me
```

Retrieve the authenticated user's information.

---

### Resume

```text
POST /api/resume/analyze
```

Upload and analyze a resume.

---

### Interviews

```text
POST /api/interviews/start
```

Start a new mock interview.

```text
POST /api/interviews/submit-answer
```

Submit an answer and receive AI-generated feedback.

```text
GET /api/interviews
```

Retrieve interview history.

```text
GET /api/interviews/:id
```

Retrieve a specific interview.

---

## Prerequisites

Before running the project, make sure you have:

* Node.js installed
* npm installed
* MongoDB database
* Groq API key

---

## Authentication Flow

```text
User
 │
 ▼
Register / Login
 │
 ▼
Express Authentication API
 │
 ├── bcrypt → Password verification
 │
 └── JWT → Authentication token
 │
 ▼
Authenticated User
 │
 ▼
Protected Routes
```

---

## Resume Analysis Flow

```text
Resume Upload
      │
      ▼
Backend receives file
      │
      ▼
PDF text extraction
      │
      ▼
Resume content
      │
      ▼
Groq AI analysis
      │
      ▼
Structured resume analysis
      │
      ▼
Frontend displays results
```

---

## Mock Interview Flow

```text
Select Interview Domain
          │
          ▼
    Start Interview
          │
          ▼
 AI generates question
          │
          ▼
    User answers
          │
          ▼
 AI evaluates answer
          │
          ▼
 Feedback + next question
          │
          ▼
      Next question
          │
          ▼
    Interview completed
          │
          ▼
   Final score + history
```

---

## Database

The application uses **MongoDB** with **Mongoose**.

Main models:

### User

Stores user information including:

* Name
* Email
* Password
* Account creation date

### Interview

Stores interview-related information including:

* Interview details
* Questions
* User answers
* AI feedback
* Interview score
* Interview history information

---

## Security

The application includes:

* Password hashing using `bcryptjs`
* JWT authentication
* Protected backend routes
* Environment variables for sensitive credentials
* Helmet for HTTP security headers
* MongoDB query sanitization

Sensitive configuration should always remain inside `.env` files and should never be committed to the repository.

---

## Future Improvements

Possible improvements that can be added in future versions include:

* Additional interview domains
* More detailed performance analytics
* Interview difficulty selection
* Additional resume formats
* Improved interview history visualization
* More personalized interview questions
