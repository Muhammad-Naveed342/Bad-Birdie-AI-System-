<div align="center">
  <h1>⛳ Bad Birdie Swatch Merge AI</h1>
  <p><strong>AI-Powered Image Processing & Garment Merging Application</strong></p>

  [![Python 3.11+](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/downloads/)
  [![Flask](https://img.shields.io/badge/Framework-Flask-black.svg?logo=flask)](https://flask.palletsprojects.com/)
  [![Docker](https://img.shields.io/badge/Deployment-Docker%20%7C%20Dokploy-blue.svg?logo=docker)](#deployment)
  [![AI: Segmind & Gemini](https://img.shields.io/badge/AI_Engine-Segmind%20%7C%20Gemini-orange.svg)](#tech-stack)

</div>

<hr/>

## 🌟 Executive Summary

The **Bad Birdie Swatch Merge Project** is an innovative, internal AI-powered web application designed to significantly accelerate fashion design visualization.

By taking an image of a fashion model and a separate swatch of a fabric pattern, our AI engine seamlessly merges the two. The result? High-quality visual mockups of the model wearing the new fabric pattern—all generated in seconds, at a fraction of the cost of a traditional photoshoot (under 40 cents per image).

---

## ✨ Key Functionalities

### 🎨 Intelligent Image Merging

- **Seamless Integration**: Combines model photos and fabric swatches into hyper-realistic mockups.
- **Garment Context**: Specify garment types (e.g., polo shirt, shorts) to guide the AI's generation.
- **Auto-Resizing**: Automatically scales and crops inputs to optimize the output resolution.

### 💻 Intuitive Web Dashboard

- **Drag-and-Drop Batch Creation**: Easily upload model and swatch combinations.
- **Live Tracking**: Real-time status updates on image generation progress.
- **Results Gallery**: Built-in lightbox for reviewing, downloading, and favoriting high-quality generations.

### ⚙️ Robust Job Management

- **Background Queueing**: Handles multiple users and large batch requests asynchronously without slowing down the UI.
- **Automated Retry System**: Quickly re-run failed or unsatisfactory generations.
- **Usage Tracking**: Automatically compiles and sends monthly usage reports to management.

### 🔐 Secure & Managed Access

- **Magic Link Authentication**: Passwordless, secure email-based login system for internal staff.
- **Role-Based Access**: Granular control over administrative features and developer tools.

---

## 🛠️ Technology Stack

Our platform leverages a modern, scalable, and highly available architecture:

- **Core Application**: Python 3.11+, Flask, HTML/Tailwind CSS
- **Primary AI Engine**: Segmind API (Optimized for fabric pattern merging workflows)
- **Secondary AI Engines**: Google Gemini (Image analysis) & Azure OpenAI (LLM inference)
- **Background Processing**: Model Context Protocol (MCP) server via stdio, APScheduler
- **Deployment**: Fully containerized using Docker, managed via **Dokploy** and Traefik routing.

---

## 🚀 Getting Started

### Prerequisites

- **Python 3.11+**
- **Docker** & **Docker Compose**
- **uv** package manager (recommended)

### 1. Local Development Setup

```bash
# Clone the repository
git clone <repository-url>
cd badbirdie-swatch-merge-2025

# Install dependencies
uv sync

# Create a local environment file
cp .env.example config._LOCAL_ENV_.sh
```

Ensure you populate your configuration file with the necessary API keys (`SEGMIND_API_KEY`, `GEMINI_API_KEY`, etc.).

### 2. Running the Application

```bash
# Start the web interface and background processors
python run_web_app.py
```

Access the application at `http://localhost:35469`.

---

## 🚢 Production Deployment (Dokploy)

This application is configured for modern, zero-downtime deployment using **Dokploy**.

1. In your Dokploy dashboard, create a new Docker Compose application.
2. Link this repository.
3. Use the included `docker-compose.dokploy.yml` file.
4. Set the following required environment variables in the Dokploy UI:
   - `APP_DOMAIN` (e.g., swatchmerge.badbirdiegolf.com)
   - `BASE_URL`
   - `FLASK_SECRET_KEY`
   - `ENV_LABEL=PROD`
   - `SEGMIND_API_KEY`
   - `SMTP_*` configurations for magic link emails.
5. Deploy! Traefik will automatically provision SSL certificates via Let's Encrypt and route traffic securely.

---

## 📊 Administration & Monitoring

The system includes a powerful CLI utility for system administrators:

```bash
# Check system health
python developer_tool.py health-check

# View database statistics
python developer_tool.py db-stats

# Create a new administrator
python developer_tool.py create-user admin@badbirdiegolf.com --role admin
```

## 📚 Further Documentation

- **[Web Application Guide](WEB_APP_README.md)** - Detailed UI architecture and API routes.
- **[Image Size Validation](IMAGE_SIZE_VALIDATION.md)** - AI input constraints and optimizations.
- **[Testing &amp; QA](testing_suggestions.md)** - Guide for running the test suite and ensuring application stability.

---

*Developed with ❤️ by Mohammad Naveed for Bad Birdie Golf.*
