# 🚀 SuperSQA Automation Dashboard

A modern, real-time **QA automation dashboard** built with Flask, HTMX, and TailwindCSS — designed to monitor CI/CD test pipelines with clean visuals, environment separation, and responsive performance.

✅ Supports both **GitLab CI/CD** and **GitHub Actions**  
✅ Live staging and production environments  
✅ Designed for real-world QA workflows and teaching automation best practices


---

## 🌐 Live Demos
- **Production**: [automationdashboard.supersqa.com](http://automationdashboard.supersqa.com/)
- **Staging**: [staging.automationdashboard.supersqa.com](http://staging.automationdashboard.supersqa.com/)

> 🔒 *Note: Normally these would be password preotected but for demo/education reasons, these are open to the public*

---

## 📸 Preview

<p align="center">
  <img src="automationdashboard/docs/assets/dashboard-main.png" alt="Main Dashboard Preview" width="600"/>
</p>

---

## 🧠 Project Purpose

This project was created as part of the **SuperSQA Automation Training** to:
- Provide learners and teams a clean way to monitor test results
- Showcase real-world CI/CD pipelines across GitLab and GitHub
- Demonstrate infrastructure deployment, test reporting, and status aggregation
- Encourage best practices in dev/test ops for automation engineers

It’s also used in training exercises to simulate real QA job experience.

---

## ✨ Features

- 🔄 **Auto-refreshing dashboard** (every 30 seconds)
- 🎯 **Pass rate logic**:
  - ✅ Green = 100% pass
  - ⚠️ Yellow = 90–99%
  - ❌ Red = <90%
- 📈 **Interactive trend charts** (Chart.js)
- 🌗 **Dark mode support**
- 📱 **Mobile-friendly UI**
- 🔄 **GitLab + GitHub CI/CD support**
- 🔐 **Staging vs Production isolation**

---

## 🛠 Tech Stack

### 🔧 Backend
- Python 3.10+
- Flask + Gunicorn
- MySQL
- Nginx
- Healthcheck endpoints

### 🎨 Frontend
- HTMX
- Tailwind CSS
- Chart.js

### 🚀 DevOps & Hosting
- GitLab CI/CD
- GitHub Actions
- Digital Ocean VPS (shared for stage/prod)

---

## 🔄 CI/CD Pipelines

### 📦 GitLab

<img src="automationdashboard/docs/assets/gitlab-pipeline.png" alt="GitLab Pipeline" width="500"/>

Stages:
1. **Pre-Deploy** – Code quality check using `pylint`
2. **Deploy to Staging** – Auto-deploy to port 9099
3. **Deploy to Production** – Deploys to port 9098 with health verification

### 🧪 GitHub Actions

<img src="automationdashboard/docs/assets/github-pipeline.png" alt="GitHub Actions Pipeline" width="550"/>

Mirrors GitLab functionality using native GitHub workflows.

> 💡 *The pipelines demonstrate different platform behaviors while delivering the same output — great for training comparisons.*

---

## 🏗 Architecture Overview

```
             ┌─────────────────┐
             │  GitHub Actions │
             └───────┬─────────┘
                     │
             ┌───────▼────────┐
             │  Digital Ocean │
             │      VPS       │
             └───────┬────────┘
                     │
             ┌───────▼────────┐
             │     Nginx      │
             │ Reverse Proxy  │
             └───────┬────────┘
                     │
         ┌───────────▼────────────┐
         │ Staging (Port: 9099)   │
         └────────────────────────┘
         ┌───────────▼────────────┐
         │ Production (Port: 9098)│
         └────────────────────────┘
```

> ⚠️ *Running both environments on the same VPS is a cost-saving measure for this educational project only. It is not a recommended enterprise practice.*

---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
# GitHub
git clone https://github.com/supersqa1/supersqa-automation-dashboard.git

# GitLab (same codebase)
git clone https://gitlab.com/ssqagroup1/supersqa-automation-dashboard.git

cd supersqa-automation-dashboard
```

### 2. Setup Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -e .[dev]
```

### 3. Configure Env Variables
```bash
export DATA_STORAGE=database
export DB_HOST=your_db_host
export DB_USER=your_user
export DB_PASSWORD=your_password
export DB_PORT=your_port
```

### 4. Run Locally
```bash
# Development
python automationdashboard/run.py

# Production
gunicorn -w 4 -b 0.0.0.0:9098 'automationdashboard:app'
```

---

## ⚡ Performance Highlights
- Lightweight app with optimized queries
- Minimal JS, HTMX-driven updates
- Asset minification for fast load

## 🔒 Security Features
- Input sanitation and injection protection
- Secure headers and CSRF handling
- Environment isolation

---

## 🧑‍💻 Author

Built with ❤️ by **Admas Kinfu**  
📘 [SuperSQA.com](http://supersqa.com)  
🔧 [GitHub](https://github.com/supersqa1) · 🧪 [GitLab](https://gitlab.com/ssqagroup1)

---

> ✨ *This dashboard demonstrates full-stack QA engineering skills including automation visibility, infrastructure, deployment pipelines, and modern frontend development — all in one project.*
