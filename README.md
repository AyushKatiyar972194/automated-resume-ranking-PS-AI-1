# 🧠 Automated Resume Information Extraction, Scoring, and Ranking System  
Problem Statement ID: PS-AI-1  
Track: AI  
Hackathon: SMART ABES Hackathon 2.0  
Team Name: WebSpark  

## 📌 Problem Context

Modern recruitment systems receive resumes in large volumes and highly variable formats (PDF, DOC, DOCX).
Manual screening is time-consuming, inconsistent, non-scalable, and prone to bias.

Existing automated systems often rely on template-based parsing or keyword counting, which fails on:
- Unstructured layouts
- Missing sections
- Resume verbosity bias (more content ≠ better candidate)

## 🎯 Objective

Design a fully automated, deterministic system that:
1. Extracts structured information from unstructured resumes
2. Applies a consistent and explainable scoring mechanism (Max score = 100)
3. Ranks 25+ resumes objectively
4. Handles format variability, ambiguity, and missing data
5. Produces reproducible and unbiased rankings

## 🏗️ System Architecture

Resume Files (PDF / DOC / DOCX)
        ↓
Text Extraction Layer
        ↓
Text Cleaning & Normalization
        ↓
Section Segmentation
        ↓
Information Extraction (NER + Rules)
        ↓
Scoring Engine (Max 100)
        ↓
Ranking Module
        ↓
Structured Output (JSON / CSV)

## 🧩 Core Modules

### 1️⃣ Resume Parsing
- Converts resumes into raw text
- Supports PDF and DOCX
- Removes layout artifacts

### 2️⃣ Section Identification
Identifies sections like:
Education, Skills, Experience, Internships, Projects, Achievements, Languages, Online Presence

### 3️⃣ Information Extraction
- Regex + NLP (NER)
- Skill normalization
- Numeric detection for CGPA and achievements

### 4️⃣ Scoring Engine (Max Score = 100)

| Category | Weight |
|--------|--------|
| Prior Internships | 20 |
| Skills & Certifications | 20 |
| Projects | 15 |
| College Marks (CGPA) | 10 |
| Quantifiable Achievements | 10 |
| Experience | 5 |
| Extra-curricular | 5 |
| Language Fluency | 3 |
| Online Presence | 3 |
| Degree Type | 3 |
| College Ranking | 2 |
| School Marks | 2 |

Each category has a hard upper limit to prevent bias.

### 5️⃣ Ranking Module
- Sort resumes by total score
- Deterministic tie-breakers:
  1. Internship score
  2. Skills score
  3. CGPA

## ⚙️ Tech Stack

- Python 3.10+
- spaCy
- pdfminer.six
- python-docx
- pandas
- FastAPI
- SQLite / PostgreSQL

## 📈 Performance

- Parsing & Extraction: O(n)
- Scoring: O(n)
- Ranking: O(n log n)

## 🛡️ Robustness

- Handles missing sections safely
- No system crash on malformed resumes
- Header-independent parsing

## 👥 Team WebSpark

- Ayush Katiyar (Team Leader)
- Akash Gupta
- Devesh Kumar
- Pratyush Shahi

## 📌 Engineering Principle

Correctness, fairness, explainability, and scalability over cosmetic features.
