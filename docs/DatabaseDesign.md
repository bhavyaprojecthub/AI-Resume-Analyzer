# Database Design

## Overview

The AI Resume Analyzer uses MongoDB as its primary database.

Main collections:

1. Users
2. Resumes
3. JobDescriptions
4. Analyses

---

# Users Collection

Purpose:
Store user account information.

Schema:

```javascript
{
  _id: ObjectId,
  name: String,
  email: String,
  password: String,
  createdAt: Date,
  updatedAt: Date
}
```

Indexes:

```javascript
email: 1
```

Reason:
Login and signup frequently search by email.

---

# Resumes Collection

Purpose:
Store uploaded resumes and extracted content.

Schema:

```javascript
{
  _id: ObjectId,
  userId: ObjectId,
  fileName: String,
  originalText: String,

  extractedSkills: [String],

  education: [String],
  experience: [String],
  projects: [String],

  createdAt: Date,
  updatedAt: Date
}
```

Indexes:

```javascript
userId: 1
```

Reason:
Quickly fetch all resumes belonging to a user.

---

# JobDescriptions Collection

Purpose:
Store job descriptions uploaded by users.

Schema:

```javascript
{
  _id: ObjectId,
  userId: ObjectId,

  title: String,
  company: String,

  description: String,

  extractedSkills: [String],

  createdAt: Date,
  updatedAt: Date
}
```

Indexes:

```javascript
userId: 1
```

---

# Analyses Collection

Purpose:
Store ATS analysis results.

Schema:

```javascript
{
  _id: ObjectId,

  userId: ObjectId,
  resumeId: ObjectId,
  jobDescriptionId: ObjectId,

  atsScore: Number,
  matchPercentage: Number,

  matchedSkills: [String],
  missingSkills: [String],

  recommendations: [String],

  status: String,

  createdAt: Date,
  updatedAt: Date
}
```

Indexes:

```javascript
userId: 1
resumeId: 1
jobDescriptionId: 1
```

---

# Relationships

User (1)
│
├── Resumes (Many)
│
├── JobDescriptions (Many)
│
└── Analyses (Many)

Analysis
│
├── Resume (1)
└── JobDescription (1)

---

# Database Diagram

```text
User
│
├── Resume
│       userId
│
├── JobDescription
│       userId
│
└── Analysis
        │
        ├── resumeId
        └── jobDescriptionId
```

---

# Design Decisions

### Why store parsed resume text?

Resume parsing is expensive.

Instead of parsing the PDF every time:

Upload PDF
→ Parse Once
→ Store Text
→ Reuse Stored Text

Benefits:

* Faster analysis
* Lower processing cost
* Better user experience

### Why use references instead of embedding?

A user can upload many resumes and analyses.

Using references:

* Improves scalability
* Prevents large user documents
* Makes querying easier
* Follows MongoDB best practices

```
```
