BharatPath AI – Design Document
1. System Overview
BharatPath AI is an AI-driven government opportunity intelligence and learning platform designed for Indian students and job aspirants.
The system:
Aggregates verified government exam and scheme notifications
Structures and analyzes eligibility criteria
Uses AI to personalize recommendations
Provides AI-powered learning assistance
Delivers intelligent push notifications
Supports multi-language explanations
The architecture is cloud-native, modular, and built entirely using open-source technologies with Firebase as the backend platform.
2. High-Level Architecture
User
↓
Frontend Application (Web / Mobile)
↓
Backend API Layer (FastAPI / Node.js)
↓
AI Intelligence Engine
↓
Firebase (Database + Auth + Notifications)
3. Core Architecture Components
3.1 Frontend Layer
Purpose:
User interaction
Dashboard and recommendation feed
Chat interface
Study assistant
Notification center
Technology:
React / Next.js (Web)
Flutter (Optional mobile expansion)
TailwindCSS for UI
Firebase SDK for authentication & push notifications
Key Modules:
User Profile Dashboard
Personalized Opportunity Feed
AI Chat Interface
Study & Mock Test Section
Notification Panel
3.2 Backend API Layer
Purpose:
Handle business logic
Process notification ingestion
Connect AI models
Manage user personalization logic
Technology:
FastAPI (Python) or Node.js (Express)
REST API architecture
Firebase Admin SDK integration
Responsibilities:
API routing
Eligibility scoring engine
AI orchestration
Data validation
Security enforcement
3.3 Data Ingestion & Structuring System
Purpose:
Fetch official government exam & scheme notifications
Extract structured data from PDFs/webpages
Convert unstructured text into structured JSON
Process Flow:
Scheduled scraper or API fetch
Extract raw content
Clean and normalize text
Extract key fields:
Exam name
Eligibility criteria
Age limits
Qualification requirements
Application deadline
Official source URL
Store structured data in Firebase Firestore
Technologies:
Python scraper (BeautifulSoup / Requests)
pdfplumber or PyMuPDF
Tesseract OCR (if needed)
Storage:
Firebase Firestore (structured data)
Firebase Storage (raw PDF files)
3.4 Database Architecture (Firebase)
Primary Database:
Firebase Firestore (NoSQL)
Collections:
Users
userId
age
qualification
category
location
interests
examPreferences
learningProgress
Notifications
notificationId
title
description
eligibilityCriteria
deadline
sourceURL
tags
relevanceMetadata
QuizResults
userId
topic
score
timestamp
Security:
Firebase Authentication
Role-based access rules
Firestore security policies
3.5 AI Intelligence Layer
The AI layer consists of multiple sub-modules.
3.5.1 Personalization Engine
Purpose: Match user profile with exam/scheme eligibility.
Logic:
Relevance Score =
Age match score
Qualification compatibility score
Location relevance weight
Category alignment
User interest weight
Deadline urgency factor
Each notification receives a composite relevance score per user.
Output:
Personalized ranked feed
Priority alerts
Technology:
Rule-based filtering
Open-source LLM for contextual reasoning (via Ollama or HuggingFace)
3.5.2 Summarization Engine
Purpose: Convert complex government language into simple explanations.
Function:
Input: Official notification text
Output: Simplified explanation
Highlight:
Who can apply
Important dates
Required documents
Technology:
Open-source LLM (Mistral / LLaMA-based model)
T5 or BART for summarization
3.5.3 Regional Language Engine
Purpose: Break language barriers.
Function:
Translate simplified explanation into Tamil, Hindi, Telugu, etc.
Technology:
NLLB (No Language Left Behind)
MarianMT
LibreTranslate (self-hosted)
3.5.4 Study Assistant Engine
Purpose: Improve exam preparation productivity.
Features:
Topic-based note generation
Step-by-step math problem solving
Quiz generator
Mock test simulation
Adaptive difficulty adjustment
Adaptive Learning Logic:
Track quiz performance
Identify weak areas
Increase question difficulty gradually
Suggest revision topics dynamically
Technology:
Open-source LLM
Python logic for scoring & adaptation
3.6 Notification Engine
Purpose: Send intelligent alerts instead of mass notifications.
Workflow:
New notification added
Personalization engine calculates relevance
High-score users flagged
Push notification sent
Technology:
Firebase Cloud Messaging (FCM)
Scheduled backend triggers
Notification Types:
Deadline reminder
Newly eligible opportunity
Daily important update summary
Mock test reminder
4. Data Flow
Government notification published
Scraper fetches and stores raw data
Processing system extracts structured fields
AI summarizes and tags notification
Data stored in Firestore
Personalization engine calculates user relevance
Ranked feed generated
Push notifications triggered for high-priority users
User interacts with AI assistant for clarification and study support
5. Security Architecture
Firebase Authentication (Email/OTP)
Firestore role-based access control
HTTPS API communication
Source whitelist validation
Input sanitization
Encrypted storage
6. Scalability Strategy
Firebase auto-scaling database
Stateless backend APIs
Modular AI services
Horizontal scaling capability
Cloud deployment ready
Designed to support millions of users with minimal architectural change.
7. Reliability & Availability
Managed Firebase infrastructure
Stateless backend design
Scheduled ingestion retries
Logging & monitoring system
Target uptime: 99%+
8. Performance Optimization
Cached summarized responses
Indexed Firestore queries
Precomputed relevance scores
Lazy loading for frontend
Background AI processing
9. Future Enhancements
Voice-based AI assistant
Offline caching mode
AI career path predictor
Resume analyzer
Physical fitness tracker (Defence mode)
Public scheme eligibility auto-application guidance
10. Architectural Strengths
Fully open-source AI stack
Zero-cost MVP capability
Scalable cloud-native design
AI-driven personalization logic
Regional language inclusion
High public impact alignment
