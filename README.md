# 🤖 AI Resume Screening & Candidate Evaluation System

An AI-powered resume screening and candidate evaluation system built with **n8n**, **Google Gemini**, **Google Sheets**, and **Gmail**.

The system automatically extracts information from a resume, compares the candidate against a provided job description, calculates a match score, and categorizes the candidate as **SHORTLIST**, **REVIEW**, or **REJECT**.

---

## 🚀 Overview

Recruiters often spend significant time manually reviewing resumes and comparing candidate qualifications against job requirements.

This workflow automates the initial screening process.

A recruiter provides:

- A resume PDF
- Job title
- Job description

The system then:

1. Extracts text from the resume.
2. Sends the resume and job description to Google Gemini.
3. Evaluates the candidate against the job requirements.
4. Calculates a score from 0–100.
5. Identifies matching and missing skills.
6. Categorizes the candidate.
7. Stores the screening result in Google Sheets.
8. Sends an email notification for shortlisted and review candidates.

---

## ✨ Features

### 📄 Resume Processing

- Accepts resume PDFs through a webhook.
- Extracts text from the uploaded resume.
- Processes candidate information automatically.

### 🤖 AI-Powered Screening

Google Gemini evaluates:

- Technical skills
- Required skill matches
- Missing required skills
- Preferred skills
- Professional experience
- Education
- Relevant projects

### 📊 Candidate Scoring

Candidates receive a score from **0–100**.

The scoring system evaluates:

| Category | Points |
|---|---:|
| Required Skills Match | 40 |
| Professional Experience | 25 |
| Relevant Projects | 15 |
| Education | 10 |
| Preferred Skills | 10 |
| **Total** | **100** |

### 🎯 Automated Decision Making

Candidates are categorized into:

- **90–100 → SHORTLIST**
- **70–89 → REVIEW**
- **0–69 → REJECT**

### 📋 Candidate Database

Screening results are automatically stored in Google Sheets.

Stored information includes:

- Candidate name
- Email
- Phone
- Education
- Experience
- Technical skills
- Matching skills
- Missing skills
- Strengths
- Weaknesses
- Score
- Recommendation
- AI reasoning

### 📧 HR Notifications

- SHORTLIST candidates → HR notification
- REVIEW candidates → Human review notification
- REJECT candidates → Stored in the database

### 🔄 Dynamic Job Descriptions

The system does not rely on a single hard-coded position.

Recruiters can provide a different:

- Job title
- Job description

for each screening request.

This allows the same workflow to screen candidates for different positions.

---

## 🏗️ Workflow Architecture

```text
Resume PDF + Job Description
            ↓
         Webhook
            ↓
    Extract Resume Text
            ↓
       Edit Fields
            ↓
      Google Gemini AI
            ↓
   Structured Output Parser
            ↓
      Candidate Score
            ↓
        Switch Node
       /     |      \
      /      |       \
SHORTLIST  REVIEW   REJECT
    ↓        ↓        ↓
Google     Google   Google
Sheets     Sheets   Sheets
    ↓        ↓
  Gmail     Gmail
```

---

## 🛠️ Technologies Used

- **n8n** — Workflow automation
- **Google Gemini** — AI resume analysis
- **Google Sheets** — Candidate database
- **Gmail** — HR notifications
- **Postman** — API/webhook testing
- **PDF extraction** — Resume text extraction

---

## 📸 Screenshots

### Complete Workflow
![image alt](https://github.com/akseghazi/ai-resume-screening-n8n/blob/c3bf0c0e0e35851c25c4ff5583287dcd8e36dcca/screenshots/complete-workflow.jpg)

### AI Screening Result

![image alt](https://github.com/akseghazi/ai-resume-screening-n8n/blob/7e5440a844329827367d4de88e811b76410ea596/screenshots/shortlist-result.jpg)

### Shortlisted Candidate



### Review Candidate


### Candidate Database



### Dynamic Job Description


---

## 📥 Installation / Setup

### 1. Import the n8n Workflow

Download the workflow JSON file from the `workflow` folder.

Import it into your n8n instance.

### 2. Configure Credentials

You will need to configure your own credentials for:

- Google Gemini
- Google Sheets
- Gmail

Do not use credentials included in the exported workflow.

### 3. Configure the Webhook

The webhook accepts:

- Resume PDF
- Job title
- Job description

Example request:

```text
POST /webhook/resume-screening
```

### 4. Test with Postman

Use `multipart/form-data`.

Example:

```text
data              → Resume PDF
job_title         → AI Automation Engineer
job_description   → Complete job description
```

---

## 🔐 Security

API keys, passwords, OAuth credentials, and other sensitive information are **not included** in this repository.

Users should configure their own credentials inside n8n.

---

## 💡 Example Use Case

A recruiter receives 50 resumes for an AI Automation Engineer position.

Instead of manually reviewing every resume:

```text
Resume
   ↓
Upload
   ↓
AI Screening
   ↓
Score
   ↓
SHORTLIST / REVIEW / REJECT
   ↓
Google Sheets
   ↓
HR Notification
```

This reduces repetitive manual screening work and gives recruiters a consistent initial evaluation process.

---

## 🎯 Future Improvements

Possible future enhancements include:

- Duplicate candidate detection
- Database integration
- Resume ranking dashboard
- Additional document formats
- Human approval workflow
- Candidate interview scheduling
- ATS integration

---

## 👨‍💻 Author

Built as an n8n automation portfolio project demonstrating:

- AI automation
- Workflow design
- Document processing
- LLM integration
- Structured AI output
- API/webhook integration
- Business process automation
