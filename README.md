# 🩺 Medical Voice AI Agent

**Real-Time AI-Powered Virtual Doctor with Voice Conversations, AI Triage, and Automated Medical Reports**

A full-stack AI healthcare application that allows users to speak with specialized AI doctors through real-time voice calls. The platform analyzes symptoms, recommends the most relevant medical specialist, conducts an AI-powered consultation, and automatically generates structured medical reports.

---

## 🚀 Live Demo

https://medical-voice-ai-agent-vqa8.vercel.app/

---

## ✨ Key Features

### 🎙️ Real-Time AI Doctor Calls

* Natural voice conversations with AI medical specialists
* Real-time speech-to-text transcription
* AI-generated spoken responses
* Live conversation streaming

### 🩺 Intelligent Doctor Recommendation

* Analyze patient symptoms using OpenAI
* Suggest the most relevant medical specialists
* Support for multiple doctor personas and specialties

### 📋 Automated Medical Reports

* Generate structured consultation summaries
* Extract symptoms, medications, severity, and duration
* AI-generated recommendations
* Store reports for future reference

### 🔐 Secure Authentication

* User registration and login with Clerk
* Protected dashboard and medical sessions
* User-specific consultation history

### 📊 Session Management

* Create and manage consultations
* Store conversation transcripts
* View historical reports
* Track consultation records

### 📱 Modern User Experience

* Responsive design
* Mobile-friendly interface
* Smooth animations with Framer Motion
* Accessible UI components using Radix UI

---

# 🏗️ System Architecture

## 1. Authentication Layer

Users authenticate through Clerk.

* Sign Up / Sign In
* Session Management
* Protected Routes
* User Creation in Database

When a user logs in for the first time, a record is automatically created in PostgreSQL with default credits.

---

## 2. AI Symptom Analysis & Doctor Recommendation

Users enter symptoms and medical concerns.

Example:

> "I have a skin rash, itching, and redness for the past week."

The application sends the symptoms to:

```http
POST /api/suggest-doctors
```

OpenAI analyzes the symptoms and recommends the most suitable specialists such as:

* General Physician
* Dermatologist
* Cardiologist
* Pediatrician
* Neurologist

---

## 3. Medical Session Creation

After selecting a doctor:

* Unique Session ID is generated
* Patient notes are stored
* Selected doctor profile is saved
* AI prompt configuration is attached

All data is persisted using Drizzle ORM and PostgreSQL.

---

## 4. Real-Time Voice Consultation

The application uses Vapi as the voice orchestration engine.

### Voice Pipeline

User Speech
↓
AssemblyAI (Speech-to-Text)
↓
OpenAI GPT-4.1 Nano
↓
PlayHT (Text-to-Speech)
↓
AI Doctor Voice Response

Vapi manages the complete real-time conversation flow.

### During the Call

* Live transcription
* Streaming AI responses
* Conversation history tracking
* Voice interaction with specialized AI doctors

---

## 5. AI Medical Report Generation

When the call ends:

```http
POST /api/medical-report
```

The complete transcript is sent to OpenAI.

The AI generates a structured medical report containing:

### Report Sections

* Chief Complaint
* Consultation Summary
* Symptoms Identified
* Duration & Severity
* Medications Mentioned
* Risk Factors
* AI Recommendations
* Follow-up Suggestions

The report is stored in PostgreSQL and can be viewed from the dashboard.

---

# 🛠️ Tech Stack

## Frontend

* Next.js 15 (App Router)
* React 19
* TypeScript
* Tailwind CSS
* Framer Motion
* Radix UI
* Lucide React

## Authentication

* Clerk

## Backend

* Next.js API Routes
* Server Actions

## Database

* PostgreSQL
* Neon Database
* Drizzle ORM

## AI & Voice Technologies

### OpenAI

Used for:

* Symptom Analysis
* Doctor Recommendation
* Medical Report Generation
* AI Consultation Logic

Model:

```text
gpt-4.1-nano
```

### Vapi

Used for:

* Real-time voice calls
* Conversation orchestration
* Streaming communication

### AssemblyAI

Used through Vapi for:

* Speech-to-Text Transcription

### PlayHT

Used through Vapi for:

* Text-to-Speech Voice Generation

---

# 📂 Project Flow

User Login
↓
Enter Symptoms
↓
AI Suggests Doctors
↓
Select Doctor
↓
Create Session
↓
Start Voice Call
↓
Live AI Consultation
↓
Call Ends
↓
Generate Medical Report
↓
Store in Database
↓
View Report

---

# ⚙️ Environment Variables

Create a `.env.local` file:

```env
# Clerk
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
CLERK_SECRET_KEY=

# Database
DATABASE_URL=

# OpenAI
OPENAI_API_KEY=

# Vapi
NEXT_PUBLIC_VAPI_PUBLIC_KEY=
VAPI_PRIVATE_KEY=
```

---

# 🚀 Local Development

Clone the repository:

```bash
git clone https://github.com/Darshan3690/medical-voice-ai-agent.git
```

Install dependencies:

```bash
npm install
```

Run database migrations:

```bash
npm run db:push
```

Start development server:

```bash
npm run dev
```

Open:

```text
http://localhost:3000
```

---

# 🔮 Future Enhancements

* Multi-language medical consultations
* Video consultation support
* Appointment booking system
* AI-powered prescription assistance
* Medical document uploads
* Health analytics dashboard
* Mobile application (React Native)

---

# ⚠️ Disclaimer

This application is for educational and informational purposes only.

It does not provide professional medical advice, diagnosis, or treatment. Users should always consult qualified healthcare professionals for medical concerns.

---

# 👨‍💻 Author

Darshan Rajput

Computer Science Student – Marwadi University

GitHub:
https://github.com/Darshan3690
