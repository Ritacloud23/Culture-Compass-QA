# 🧪 Culture Compass — QA & Test Automation

> Automated frontend testing for [culturecompass.co](https://culturecompass.co) — built from scratch with Robot Framework, SeleniumLibrary, and GitHub Actions CI/CD.

---

## 📌 Overview

When I joined the Culture Compass project, there was **zero test coverage**. I built the entire QA layer from the ground up — automated UI tests, CI/CD integration, scheduled runs, and failure alerting — so the team could ship with confidence.

**What this repo covers:**
- Recording and automating browser test flows with Katalon Recorder + Robot Framework
- Fixing broken locators and stabilizing flaky test scripts
- Integrating tests into the existing GitHub Actions pipeline
- Setting up daily scheduled runs and failure notifications
- Handling a Gitleaks false positive safely

---

## 🛠️ Tools & Technologies

| Tool | Version | Purpose |
|------|---------|---------|
| Katalon Recorder | 7.1.0 | Recording browser test flows |
| Robot Framework | 7.4.2 | Test automation framework |
| SeleniumLibrary | 6.8.0 | Browser automation library |
| Python | 3.11.9 | Runtime environment |
| WebDriver Manager | latest | Browser driver management |
| GitHub Actions | — | CI/CD and scheduled execution |

---

## 📁 Test Structure

```
tests/
├── Homepage.robot           # Homepage load + title validation
├── Blog.robot               # Blog page navigation
├── ExplorePage.robot        # Countries page + modal interaction
└── WaitListSignupTest.robot # Waitlist signup flow
```

---

## ⚙️ Installation & Setup

### Prerequisites
- Python 3.11+
- Google Chrome
- Katalon Recorder Chrome extension

### Install Dependencies

```bash
pip install robotframework
pip install robotframework-seleniumlibrary
pip install webdriver-manager
```

---

## ▶️ Running the Tests

### Run All Tests
```bash
robot tests/
```

### Run a Single Test File
```bash
robot tests/Homepage.robot
robot tests/Blog.robot
robot tests/ExplorePage.robot
robot tests/WaitListSignupTest.robot
```

### View Results

After running, open these files in your browser:
- `report.html` — test summary
- `log.html` — detailed execution log
- `output.xml` — raw output data

---

## 🔁 CI/CD Integration

Tests are fully integrated into the GitHub Actions pipeline.

**Workflow file:** `.github/workflows/cicd.yaml`

### Triggers
- ✅ Push to `main`
- ✅ Pull request to `main`
- ✅ Daily scheduled run at **08:00 UTC**
- ✅ Manual trigger via `workflow_dispatch`

```yaml
schedule:
  - cron: "0 8 * * *"
```

### Failure Notifications
- GitHub notifications enabled
- Email notifications enabled
- Alerts limited to **failed workflows only**

> **Note:** Notifications are user-based. Each team member needs to enable workflow notifications on their own GitHub account.

---

## ✅ Test Coverage

### Homepage
- [x] Page loads successfully
- [x] Title validation

### Blog Page
- [x] Navigation works
- [x] Page content is visible

### Explore Page
- [x] Navigation to Countries/Explore section
- [x] Grid/card interaction
- [x] Modal open and close flow

### Waitlist Flow
- [x] Navigation to Blog page
- [x] Form input
- [x] Submission flow

---

## 🔒 Security Note

The pipeline flagged a **Gitleaks false positive** in `app.js`. After reviewing, I confirmed it was not a real secret and added a `.gitleaks.toml` config to handle it safely without suppressing real secret scanning.

---

## 📝 Best Practices Used

- Kept locators simple and reliable
- Preferred focused, single-flow test scripts over large unstable ones
- Avoided committing result files (`log.html`, `report.html`, `output.xml`) to keep the repo clean
- Documented everything so any team member can pick it up and run it

---

## 🚀 What's Next

- Expand test coverage to more pages and edge cases
- Add tests for new features as they ship
- Explore Playwright for cross-browser testing

---

## 👩🏾‍💻 About

Built by **Rita Ugwanyi** — Cloud & DevOps Engineer with a focus on quality, automation, and shipping things that actually work.

🔗 [LinkedIn](https://linkedin.com/in/your-linkedin) • [GitHub](https://github.com/Ritacloud23)
