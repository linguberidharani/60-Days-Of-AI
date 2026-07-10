# 🏥 Hospital Admission Readiness Simulator

An interactive healthcare workflow simulation that helps users experience the role of a **Hospital Admission Coordinator** by managing admission readiness, prior authorization, documentation, insurance verification, and clinical workflow steps.

This project was built as part of the **60 Days of AI Challenge** to explore how AI-assisted development can create realistic industry workflow simulations using HTML, Tailwind CSS, and Vanilla JavaScript.

---

## 🚀 Project Overview

The Hospital Admission Readiness Simulator simulates the hospital admission preparation process.

Users can:

- Create an admission case
- Configure patient admission details
- Analyze admission readiness
- Manage Prior Authorization scenarios
- Complete workflow tasks
- Track operational risks
- Review governance insights
- Evaluate final admission decisions

The application follows a **task-first healthcare simulation design** rather than a traditional dashboard.

---

## 🎯 Objective

The goal of this simulator is to demonstrate how healthcare administrative workflows can be transformed into interactive learning experiences.

The user plays the role of:

> 🧑‍⚕️ Hospital Admission Coordinator

Responsible for ensuring all admission requirements are completed before patient admission.

---

# ✨ Features

## 1. Admission Setup

Users can configure:

- Provider (Illustrative Training Data)
- Attending Physician (Illustrative Training Data)
- Diagnosis
  - Acute MI
  - CHF
  - Pneumonia
  - Elective Surgery
  - Hip Fracture

- Admission Type:
  - Inpatient
  - Observation
  - Emergency
  - ICU
  - Same-Day Surgery

- Prior Authorization Status:
  - Approved
  - Pending
  - Denied

- Admission Date


---

# 📊 Readiness Analysis

The simulator generates an initial readiness score between:


Final admission decision is hidden initially.

The readiness score uses weighted healthcare workflow factors:

| Category | Weight |
|----------|--------|
| Prior Authorization | 25% |
| Clinical Documentation | 20% |
| Physician Orders | 20% |
| Insurance Verification | 15% |
| Consent | 10% |
| Bed Assignment | 10% |

---

# 🔐 Prior Authorization Workflow

Supports multiple PA scenarios:

### ✅ Approved

Continues admission workflow.

### ⏳ Pending

Required actions:

- Follow up with payer
- Upload supporting documents
- Contact physician


### ❌ Denied

Actions:

- Review denial reason
- Contact insurance
- Submit appeal

Successful appeals convert status to:

---

# 🏥 Workflow Actions

Users can complete:

- Assign Bed
- Verify Insurance
- Upload Documentation
- Complete Consent
- Contact Physician
- Notify Nursing
- Prepare Patient Arrival


Each action improves admission readiness.

---

# 📅 Admission Timeline

Tracks milestones:

---

# 👥 Care Coordination

Includes healthcare team roles:

### Attending Physician

Responsible for clinical decisions and orders.

### Case Manager

Coordinates resources and admission planning.

### Nursing

Ensures patient care readiness.

### Utilization Review

Handles:

- Concurrent review
- Denial risk identification
- InterQual criteria
- Milliman criteria

### Discharge Planner

Supports transition planning.

---

# ⚠️ Risk Tracking

Tracks:

- Documentation Risk
- Insurance Risk
- Bed Risk
- Clinical Risk

Clinical risk receives higher weighting for:

- Acute MI
- CHF
- ICU Admissions


---

# 📈 Governance Snapshot

Unlocked when readiness reaches:

Displays healthcare operational benchmarks:

- PA turnaround: 3–5 days
- Inpatient denial rate estimates
- PA rework cost estimates

*(All benchmarks are training estimates only.)*

---

# ✅ Final Decision Logic

Admission evaluation:

### Ready

### Not Ready

---

# 🛠️ Technologies Used

Frontend:

- HTML5
- Tailwind CSS CDN
- Vanilla JavaScript

AI Tools:

- Claude AI
- Prompt Engineering

Development Approach:

- Single-file application
- AI-assisted coding workflow
- Healthcare simulation design


---

# 📂 Project Structure

---

# 🧠 Key Learnings

During this project I learned:

- Designing real-world workflow simulations
- Translating business requirements into application logic
- Building interactive UI without frameworks
- Creating rule-based scoring systems
- Managing complex state transitions
- Using AI as a development assistant

---

# 📸 Screenshots

(Add screenshots here)

---

# 🔮 Future Improvements

Possible enhancements:

- Patient database integration
- Real-time hospital bed availability
- AI admission recommendation engine
- Authentication system
- Cloud deployment
- Analytics dashboard

---

# 👩‍💻 Created By

**Dharani**

60 Days of AI Challenge  
GitHub: https://github.com/linguberidharani
