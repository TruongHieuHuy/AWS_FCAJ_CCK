<div align="center">

# 💰 Budget Tracker
### AI-Powered Personal Finance Management & Financial Intelligence Platform

[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![C# .NET](https://img.shields.io/badge/C%23-.NET_8-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/)
[![AWS Lambda](https://img.shields.io/badge/AWS_Lambda-Serverless-FF9900?style=for-the-badge&logo=awslambda&logoColor=white)](https://aws.amazon.com/lambda/)
[![DynamoDB](https://img.shields.io/badge/DynamoDB-NoSQL-4053D6?style=for-the-badge&logo=amazondynamodb&logoColor=white)](https://aws.amazon.com/dynamodb/)
[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-CI%2FCD-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)](https://github.com/features/actions)

---

🌐 **[Live Portfolio Website:](https://truonghieuhuy.github.io/AWS_FCAJ_CCK/)** &nbsp;|&nbsp; 🎥 **[Video Demo:](https://drive.google.com/file/d/1_q4sdSqufmfxGnCE7WsOOij97Xxfb1hk/view?usp=sharing)** &nbsp;|&nbsp; 
📄 **[Budget Tracker Website:](https://d3ja9nvtyjzo9o.cloudfront.net/)**

</div>

---

## 📖 Executive Summary

Managing personal finances is messy. Receipts pile up, categories blur, and budgets overflow — all because tracking is manual, tedious, and error-prone.

**Budget Tracker** solves this by combining an **AWS Serverless backend** with the cognitive power of **Google Gemini AI** to deliver an intelligent, fully automated personal finance platform. Users can add transactions via natural language, upload receipt photos for AI-powered auto-categorization, track budgets in real-time, and receive instant overspend alerts — all within a responsive React SPA.

> Built as the **capstone project** for the **AWS First Cloud AI Journey (FCAJ) Internship Program**, this project demonstrates end-to-end ownership across Cloud Engineering, System Architecture, and Business Analysis.

---

## 🏗️ System Architecture

> Architecture Diagram: The full system architecture shows the data flow from the React SPA client through CloudFront (CDN/Edge Security Layer) → S3 (Static Hosting) → API Gateway → Lambda C# (Business Logic) → DynamoDB (Data Layer) + Google Gemini AI (Intelligence Layer). SNS/SQS handles the asynchronous budget alert notification pipeline.

```
[Architecture Diagram Image Here]
```

### Key architectural decisions:
| Component | Technology | Design Rationale |
| :--- | :--- | :--- |
| **Frontend** | React + TypeScript on S3 + CloudFront | Edge caching eliminates origin latency; global CDN with WAF for security |
| **API Layer** | Amazon API Gateway (REST) | Managed throttling, CORS, and request validation at the entry point |
| **Business Logic** | AWS Lambda (C# .NET 8) | Stateless, event-driven compute — zero idle cost, auto-scales to zero |
| **Database** | Amazon DynamoDB (Single-Table Design) | Sub-millisecond P99 reads via GSI; no DB server provisioning required |
| **AI Engine** | Google Gemini 1.5 Flash | Multimodal (text + image) transaction analysis and smart categorization |
| **Identity** | Amazon Cognito User Pools | Managed OIDC/OAuth2 flow — eliminates password management complexity |
| **Notifications** | Amazon SQS + SNS | Decoupled, resilient async pipeline for budget overspend alerts |
| **IaC & CI/CD** | AWS SAM + GitHub Actions (OIDC) | Infrastructure as Code with keyless deployment — no long-lived secrets |

---

## ✨ Features Showcase

### 🤖 AI-Powered Transaction Categorization
Upload a receipt photo or describe a transaction in plain English/Vietnamese. Gemini AI automatically extracts the merchant, amount, and assigns the correct spending category.

```
[Feature Screenshot: AI Transaction Entry Here]
```

### 📊 Real-time Financial Dashboard
Visualize spending patterns with interactive charts. Filter by date range, category, or custom tags. All data updates live as new transactions are recorded.

```
[Feature Screenshot: Dashboard Here]
```

### 🔔 Smart Budget Alerting System
Set monthly spending limits per category. When 80% or 100% of a budget is consumed, an automated pipeline (SQS → SNS → Email/SMS) fires an instant alert — no polling, no delay.

```
[Feature Screenshot: Budget Alert Here]
```

### 🔐 Secure Authentication Flow
Full OIDC-compliant login and registration powered by Amazon Cognito. JWT tokens are validated at the API Gateway level on every request, enforcing IAM Least Privilege throughout the backend.

```
[Feature Screenshot: Login Page Here]
```

---

## 🔍 Dual-Perspective Analysis

This project was developed under a **T-shaped Engineer framework**: deep technical execution combined with business value analysis.

### 🛠️ Cloud Engineer Lens

| Problem | Solution Implemented |
| :--- | :--- |
| DynamoDB hot partition risk on high-cardinality writes | **Single-Table Design** with composite sort keys; write sharding via UUID prefix |
| Lambda Cold Start latency on C# runtime | Provisioned Concurrency on critical auth paths; ARM64 (Graviton2) for 19% cost reduction |
| API secret sprawl across Lambda environments | **AWS Secrets Manager** with auto-rotation; OIDC federated identity for CI/CD (zero static keys) |
| CloudFront cache invalidation complexity | Cache-busting via versioned S3 object keys on every CI/CD build |

### 💡 BA/SA Lens

| Business Metric | Impact |
| :--- | :--- |
| **User Friction** | Reduced transaction entry time from ~2 min (manual) to ~15 sec (AI-assisted photo upload) |
| **Operational Cost** | Pay-per-invocation model delivers ~$0 cost during development; scales linearly at production load |
| **Project Velocity** | SAM IaC + GitHub Actions OIDC eliminates ~45 min of manual deploy steps per release cycle |
| **Risk Management** | SQS dead-letter queue ensures zero missed budget alerts even during downstream SNS disruption |

---

## 🚀 Local Development Guide

### Prerequisites
- Node.js 20+, AWS CLI v2, AWS SAM CLI, .NET 8 SDK
- An active AWS Account with programmatic access configured

### 1. Clone the Portfolio Report Site
```bash
git clone --recurse-submodules https://github.com/TruongHieuHuy/AWS_FCAJ_CCK.git
cd AWS_FCAJ_CCK

# Run the Hugo dev server locally
hugo server -D
# → Open http://localhost:1313
```

### 2. Deploy Backend Infrastructure (Budget Tracker App)
```bash
# Navigate to the backend SAM project
cd budget-tracker-backend

# Build and deploy to AWS (first time: guided mode)
sam build
sam deploy --guided

# Subsequent deploys
sam deploy
```

### 3. Configure Frontend Environment
```bash
cd budget-tracker-frontend
cp .env.example .env.local
# Fill in API Gateway URL and Cognito Pool IDs from the SAM deploy output
npm install && npm run dev
```

---

## 📁 Repository Structure

```
AWS_FCAJ_CCK/                     # Hugo Portfolio (Internship Report)
├── .github/
│   └── workflows/
│       └── hugo.yml              # ← GitHub Actions: Auto-deploy Portfolio to GitHub Pages
├── content/
│   ├── 1-Worklog/                # 12-week internship worklog (EN + VI)
│   ├── 2-Proposal/               # Project proposal & system design
│   ├── 3-BlogsPosted/            # Translated AWS technical blogs
│   ├── 4-EventParticipated/      # AWS Community Day 2026 & FCAJ Community Day reports
│   ├── 5-Workshop/               # Step-by-step workshop guide (12 modules)
│   ├── 6-Self-evaluation/        # Competency self-assessment
│   └── 7-Feedback/               # Sharing & feedback
├── static/images/                # All embedded screenshots and diagrams
├── themes/hugo-theme-learn/      # Hugo theme (git submodule)
└── config.toml                   # Hugo multilingual (EN/VI) configuration
```

---

## 👤 About the Author

**Trương Hiếu Huy** — Information Systems student at HUTECH University, Cohort 22.

Combining a Business Analyst mindset with hands-on Cloud Engineering skills, I pursue the conviction that **"a great SA must have personally configured infrastructure and read real error logs to design business solutions that are not theoretical."**

- 📧 truonghieuhuy1401@gmail.com
- 🏢 **Internship:** AWS First Cloud AI Journey (FCAJ) — Workforce Bootcamp 2026
- 🗓️ **Duration:** 04/05/2026 – 30/07/2026

---

<div align="center">

*Built with ❤️ on AWS Serverless · Documented as Code · Deployed via GitHub Actions*

[![Deploy Hugo to GitHub Pages](https://github.com/TruongHieuHuy/AWS_FCAJ_CCK/actions/workflows/hugo.yml/badge.svg)](https://github.com/TruongHieuHuy/AWS_FCAJ_CCK/actions/workflows/hugo.yml)

</div>
