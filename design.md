# BharatPath AI - System Design Document

## 1. Architecture Overview

BharatPath AI follows a cloud-native, serverless, AI-driven architecture built on AWS.

Main Components:

1. Data Ingestion Layer
2. Processing & Structuring Layer
3. AI Intelligence Layer
4. Application Layer
5. Notification Layer

---

## 2. High-Level Architecture

User → Frontend App → API Gateway → Backend Services → AI Engine → Database → Notification Service

---

## 3. Core Components

### 3.1 Data Ingestion System

- Scheduled crawler or API fetcher
- Pulls verified government notifications
- Runs daily via event scheduler
- Stores raw data in cloud storage

Technology:
- AWS Lambda
- Amazon EventBridge
- Amazon S3

---

### 3.2 Data Processing Layer

- Cleans and structures notification data
- Extracts eligibility criteria
- Converts PDF/text into structured JSON

Technology:
- AWS Lambda
- Amazon Textract (if PDFs)
- DynamoDB for structured storage

---

### 3.3 AI Intelligence Layer

#### a) Personalization Engine
- Matches user profile with eligibility criteria
- Uses rule-based + LLM reasoning
- Assigns relevance score

#### b) Summarization Engine
- Converts complex government language into simple explanations

#### c) Regional Language Translation
- Converts English explanations into Tamil/Hindi/etc.

Technology:
- Amazon Bedrock (LLM)
- Amazon Translate

---

### 3.4 Study Assistant Engine

- Generates topic-based notes
- Solves maths step-by-step
- Adaptive quiz generation
- Weakness detection logic

AI Model handles:
- Context understanding
- Learning personalization
- Dynamic content generation

---

### 3.5 Application Layer

- Web or Mobile frontend
- User dashboard
- Personalized recommendation feed
- Chat interface

---

### 3.6 Notification Engine

- Filters high-priority updates
- Sends push notifications
- Deadline reminders

Technology:
- Amazon SNS
- Event-driven triggers

---

## 4. Data Flow

1. Government notification published
2. Ingestion system fetches data
3. Processing layer structures it
4. AI layer simplifies and tags it
5. Stored in database
6. Personalization engine matches users
7. Relevant users receive notifications

---

## 5. Security

- Secure authentication
- Role-based access
- Encrypted data storage
- Verified source validation

---

## 6. Scalability

- Serverless architecture
- Auto-scaling Lambda functions
- Managed databases
- CDN for frontend delivery

---

## 7. Future Enhancements

- Voice-based AI assistant
- Offline mode
- Career path predictor
- Resume analyzer
- Physical fitness tracker (Defence mode)
