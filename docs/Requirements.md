# Requirements Document

## Functional Requirements (FR)

### FR-1 Authentication

Users should be able to:

* Sign Up
* Login
* Logout

### FR-2 Resume Upload

Users should be able to upload:

* PDF files
* DOCX files

System should:

* Store uploaded files
* Extract resume text

### FR-3 Resume Analysis

System should analyze resumes and identify:

* Skills
* Projects
* Experience
* Education

### FR-4 Job Description Analysis

Users should be able to paste a Job Description.

System should extract:

* Skills
* Keywords
* Requirements

### FR-5 ATS Analysis

System should generate:

* ATS Score
* Keyword Match Percentage
* Missing Keywords

### FR-6 Skill Gap Analysis

System should display:

* Existing Skills
* Missing Skills
* Learning Suggestions

### FR-7 Interview Question Generation

System should generate:

* Technical Questions
* HR Questions
* Resume-Based Questions

---

## Non-Functional Requirements (NFR)

### NFR-1 Security

* Passwords must be hashed using bcrypt.
* Sensitive information must not be stored in plain text.

### NFR-2 Scalability

* Architecture should support future growth without major redesign.

### NFR-3 Availability

* Target high availability and reliability.

### NFR-4 Performance

* Resume analysis should complete within 10 seconds under normal conditions.

### NFR-5 Maintainability

Backend should follow:

* Routes
* Controllers
* Services
* Middleware

Architecture pattern.

---

## MVP Scope

### Included in MVP

* User Authentication

  * Signup
  * Login

* Resume Upload

  * PDF
  * DOCX

* Job Description Input

  * Paste JD

* ATS Analysis

  * ATS Score

* Skill Gap Analysis

  * Missing Skills

* Interview Question Generation

* Dashboard

* Results Page

---

## Out of Scope (Future Versions)

The following features are intentionally postponed:

* Multi-Agent System
* Pinecone Integration
* RAG Pipeline
* Resume Rewriter
* Mock Interviews
* Voice AI
* Job Recommendations
* Cover Letter Generator

These features may be added in future versions after the MVP is completed.
