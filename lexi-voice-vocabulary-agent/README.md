# 🎙️ Lexi — Voice Vocabulary Agent

> A modern browser-based voice vocabulary learning prototype built to demonstrate **QA Testing + Data Analytics + Frontend Engineering** in one portfolio project.

[![Live Demo](https://img.shields.io/badge/Live-Demo-7C5CFF?style=for-the-badge)](#-live-demo)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Web Speech API](https://img.shields.io/badge/Web%20Speech%20API-Voice-20D3A7?style=flat-square)](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API)

---

## 📌 Project Overview

**Lexi** is an interactive vocabulary coach where a learner:

1. Selects a vocabulary deck.
2. Sees a target word, pronunciation and clue.
3. Speaks the word into the microphone.
4. Lexi converts speech to text using the browser's Speech Recognition API.
5. A similarity algorithm compares the recognized speech with the target word.
6. The learner receives immediate feedback.
7. Attempts are stored locally and converted into analytics.
8. QA smoke tests and a manual bug tracker are available inside the same application.

The project is intentionally designed as a **portfolio case study**, not just a UI demo.

---

## 🎯 Why I Built This

This project demonstrates how one product can be approached from multiple professional perspectives:

| Area | What the project demonstrates |
|---|---|
| 🧪 QA Testing | Functional testing, negative scenarios, browser compatibility, validation and smoke tests |
| 📊 Data Analytics | Event logging, KPIs, accuracy, attempts, word-level performance and CSV export |
| 💻 Frontend | Responsive UI, DOM manipulation, state management and browser APIs |
| 🐞 Bug Tracking | Severity, status, reproduction steps, expected vs actual results |
| 🎙️ Voice UX | Speech recognition and text-to-speech interaction |

---

## ✨ Features

### 🎙️ Voice Vocabulary Coach

- Multiple vocabulary decks:
  - GRE-style / Advanced
  - Business English
  - Everyday Essentials
- Microphone-based word recognition
- Text-to-speech pronunciation
- Pronunciation feedback
- Similarity scoring
- Streak tracking
- Mastered-word tracking
- Skip / next-word workflow
- Browser capability detection

### 🧪 QA Testing Dashboard

The application contains an executable smoke-test suite.

Example checks include:

- Deck selector population
- Levenshtein distance calculation
- Similarity scoring
- Microphone button accessibility
- Next-word state
- Speech synthesis support
- Speech recognition support
- Unsupported-browser warning
- `localStorage` read/write
- CSV escaping

The tests run against the current browser session instead of displaying only hardcoded results.

### 📊 Data Analytics Dashboard

Each voice attempt can be stored with:

```text
timestamp
deck
word
heard
similarity
correct
```

The dashboard calculates:

- Accuracy %
- Total attempts
- Words mastered
- Current streak
- Performance by vocabulary word
- Hardest word / lowest success rate
- Actionable learning insight

The raw attempt dataset can be exported as CSV.

### 🐞 Manual Bug Tracker

A lightweight QA defect-management workflow is included.

A tester can record:

- Test ID
- Module
- Steps to reproduce
- Expected result
- Actual result
- Severity
- Status
- Logged date

Supported severity levels:

`Low` · `Medium` · `High` · `Critical`

Supported statuses:

`Open` · `Retest` · `Fixed`

Bug records can also be exported to CSV.

---

## 🧠 How the Pronunciation Scoring Works

Lexi uses **Levenshtein distance** to compare the browser's recognized speech with the target word.

Conceptually:

```text
similarity = 1 - (edit distance / maximum string length)
```

The prototype then classifies the attempt into three levels:

```text
≥ 0.82  →  Correct
≥ 0.55  →  Close
<  0.55  →  Try again
```

This is a lightweight prototype approach. It is **not a phoneme-level pronunciation assessment system**.

---

## 🏗️ Architecture

```text
┌─────────────────────────────────────────────┐
│                Lexi Web App                 │
├─────────────────────────────────────────────┤
│                                             │
│  Vocabulary Decks                           │
│        │                                    │
│        ▼                                    │
│  Voice Input ───────► Speech Recognition    │
│        │                                    │
│        ▼                                    │
│  Text Cleaning / Normalization              │
│        │                                    │
│        ▼                                    │
│  Levenshtein Similarity                     │
│        │                                    │
│        ├──────────────► Learner Feedback     │
│        │                                    │
│        ▼                                    │
│  Attempt Event Log                          │
│        │                                    │
│        ├──────────────► Analytics Dashboard │
│        │                                    │
│        └──────────────► CSV Export           │
│                                             │
│  QA Smoke Tests ─────────► Test Results      │
│  Manual Bug Tracker ─────► Bug CSV           │
│                                             │
│  localStorage = lightweight local datastore │
└─────────────────────────────────────────────┘
```

---

## 🛠️ Technology Stack

### Frontend

- HTML5
- CSS3
- Vanilla JavaScript
- Responsive design
- CSS gradients / animations

### Browser APIs

- Web Speech API
- Speech Recognition
- Speech Synthesis
- `localStorage`
- Blob / client-side CSV export

### Testing Concepts

- Functional testing
- Positive testing
- Negative testing
- Compatibility testing
- UI/state testing
- Smoke testing
- Accessibility-oriented checks
- Defect reporting

### Analytics Concepts

- Event-level data collection
- KPI calculation
- Aggregation
- Segmentation by word
- Success-rate analysis
- Insight generation
- CSV extraction

---

## 🚀 Run Locally

### Option 1 — VS Code + Live Server

1. Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/lexi-voice-vocabulary-agent.git
```

2. Open the folder in VS Code.
3. Open `index.html`.
4. Right-click the file.
5. Select **Open with Live Server**.
6. Allow microphone access when the browser asks.

### Option 2 — Simple local server

Python:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

> Chrome or Edge is recommended because browser speech-recognition support varies by browser.

---

## 🎮 How to Use

### Step 1 — Select a deck

Choose:

- GRE-style
- Business English
- Everyday Essentials

### Step 2 — Read the target

Lexi displays:

- Word
- Pronunciation
- Meaning / clue

### Step 3 — Speak

Click the microphone and pronounce the word.

### Step 4 — Review feedback

Lexi reports whether the recognized speech:

- Matches
- Is close
- Needs another attempt

### Step 5 — Generate analytics

After several attempts:

**Data Analytics → View analytics dashboard**

You can see real attempt data stored in the browser.

### Step 6 — Test the application

Open:

**QA Testing → View QA test report**

The application executes its smoke-test suite against the current session.

### Step 7 — Report a defect

Open:

**Manual Bug Tracker → Open bug tracker**

Add reproduction details and severity/status.

---

## 🧪 QA Test Strategy

### Functional Testing

| Test Area | Example |
|---|---|
| Deck selection | Switch between vocabulary decks |
| Voice input | Speak a target word |
| Feedback | Verify correct / close / incorrect states |
| Navigation | Verify Next and Skip |
| Text-to-speech | Verify "hear it spoken" |
| Persistence | Verify attempt and bug records survive refresh |

### Negative Testing

Examples:

- No speech detected
- Microphone permission denied
- Incorrect pronunciation
- Unsupported browser
- Empty bug reproduction steps
- Storage unavailable
- Speech recognition unavailable

### Compatibility Testing

Recommended browsers:

- Chrome
- Edge
- Firefox
- Safari

> Speech recognition support is browser-dependent, so compatibility results can differ.

---

## 📊 Analytics Example

The project treats each learner interaction as an event:

```json
{
  "timestamp": "2026-09-13T12:00:00.000Z",
  "deck": "business",
  "word": "leverage",
  "heard": "leverage",
  "similarity": 100,
  "correct": true
}
```

From these events, the dashboard calculates metrics such as:

```text
Accuracy
Total Attempts
Words Mastered
Current Streak
Success Rate by Word
Hardest Vocabulary
```

### Example analytical insight

> If a vocabulary word repeatedly has the lowest success rate, the product could resurface that word more frequently using spaced repetition.

---

## 🐞 Bug Reporting Example

A manual defect can be recorded using:

```text
Test ID: TC-11
Module: Voice input
Steps:
1. Select Business English
2. Click microphone
3. Speak the target word

Expected:
Correct pronunciation feedback is displayed.

Actual:
Incorrect result is displayed.

Severity: Medium
Status: Open
```

---

## 📁 Repository Structure

```text
lexi-voice-vocabulary-agent/
│
├── index.html          # Complete working prototype
├── README.md           # Project documentation
└── .gitignore          # Git ignore rules
```

The current prototype is intentionally lightweight and uses **no external build system or npm dependency**.

---

## 🔐 Data & Privacy

The prototype stores attempt and bug data using browser `localStorage`.

No backend database is required.

This means:

- Data is local to the browser.
- Clearing browser storage removes the stored records.
- CSV export is performed client-side.
- The prototype does not require a login or server.

> Note: Browser speech-recognition behavior can depend on the browser's implementation and permissions. Do not treat this prototype as a production privacy/security architecture.

---

## ⚠️ Limitations

This is a portfolio prototype, so there are intentional limitations:

- Pronunciation scoring is based on recognized text similarity, not acoustic/phoneme analysis.
- Speech recognition support varies by browser.
- Data is stored locally rather than in a production database.
- Analytics are based only on interactions recorded in the current browser storage.
- No authentication or multi-user backend exists.
- QA smoke tests are browser-side checks, not a replacement for a full CI/CD test suite.

---

## 🔮 Future Improvements

### QA

- Add Playwright / Selenium automation
- Add API testing if a backend is introduced
- Add CI test execution with GitHub Actions
- Add cross-browser automated testing
- Add accessibility testing with automated tooling
- Add structured test-case management

### Data Analytics

- Store events in PostgreSQL / MySQL
- Build a Python ETL pipeline
- Create a Power BI dashboard
- Add cohort analysis
- Add retention metrics
- Add learning-progress trends
- Add spaced-repetition recommendations

### Product

- User accounts
- Cloud synchronization
- More vocabulary decks
- Difficulty adaptation
- Phoneme-level pronunciation analysis
- Personalized learning paths
- Mobile-first PWA
- AI-powered conversational practice

---

## 💼 Portfolio / Interview Value

This project can be presented differently depending on the role.

### For a QA Tester role

> "I built a browser-based voice vocabulary application and created an executable smoke-test suite covering functional behavior, browser capabilities, state changes, local storage and CSV handling. I also added a manual defect tracker with severity, status, expected/actual results and reproduction steps."

### For a Data Analyst role

> "I instrumented the application at the attempt level, captured learner events and transformed them into KPIs such as accuracy, attempts, mastered words and word-level success rates. I also added CSV export and generated actionable insights from the aggregated data."

### For a Frontend role

> "I built a responsive vanilla JavaScript application using browser speech APIs, client-side state management, local persistence, dynamic DOM updates and a modern responsive UI."

---

## 📸 Suggested GitHub Screenshots

For the repository, add screenshots such as:

```text
docs/
├── hero.png
├── voice-agent.png
├── qa-dashboard.png
├── analytics-dashboard.png
└── bug-tracker.png
```

A strong README hero screenshot should show the main voice-agent interface.

---

## 👤 Author

**Souvik Chakraborty**

Built as a portfolio project demonstrating:

**QA Testing · Data Analytics · Frontend Development · Voice UX**

---

## 📄 License

This project is provided for portfolio and educational purposes.
