# Status.im QA Defect Analysis & Exploratory Testing 🐞

**Focus Areas: Mobile Performance Profiling (ADB Logcat), Desktop Backend Debugging, and AI-Assisted QA Workflows.**

### 📋 Executive Summary
This repository contains the results of an unscripted, exploratory testing session across the Status.im ecosystem (Android and Windows Desktop). <br>
The objective was to move beyond surface-level UI testing and identify high-impact system defects, extract the underlying error logs, and document them using industry-standard Agile methodologies (Jira).

### 🧪 Testing Scope & Findings
During this session, I conducted performance profiling via ADB on the Android mobile client, successfully isolating **a P1 10.7-second UI thread freeze caused by a Slow Binder warning.** <br>
Additionally, through data sync verification and backend log monitoring on the Windows Desktop application, I uncovered a P1 functional crash in the Market tab triggered by `JSON.parse` and `IndexDefect` errors.

#### 📱 Bug 1: Mobile UI Freeze (Performance)
* **Issue:** The main UI thread locks up completely for ~10.7 seconds during login/navigation. 
* **Root Cause Analysis:** Extracted `adb logcat` data reveals a severe Slow Binder warning on `app.status.mobile.ipc.IStatusGoService`. The background data sync monopolizes the main thread, resulting in a temporary Application Not Responding (ANR) state.
* **Artifacts Provided:** Screen recording, raw `.txt` system logs, and formal Jira ticket. <br>
📂 **[View Mobile Performance Bug Resources Here](./Mobile_Performance_Bug)**
<details>
  <summary><b><u>🎥 Click here to expand and watch the Mobile Screen Freeze Video.</u></b></summary>
  <br>
  
  https://github.com/user-attachments/assets/3a9195b6-c7c5-4c81-a62f-e2c58e689ba8

</details>
<br>
#### 💻 Bug 2: Market Tab Crash & Sync Failure (Functional)
* **Issue:** Navigating to the Market tab triggers an unhandled `IndexDefect`, causing a fatal crash.
* **Root Cause Analysis:** Desktop logs reveal upstream failures during initial state loading, specifically a `JSON.parse` syntax error while handling revealed addresses and an ENS resolver failure (`ens_getName`).
* **Artifacts Provided:** UI error stack trace screenshot, background electron logs, and formal Jira ticket. <br>
📂 **[View Desktop Bug Resources Here](./Desktop_Market_Bug)**

#### 🤖 QA Workflow Optimization: AI-Assisted Reporting
To optimize the manual testing lifecycle and reduce administrative overhead, the defect reports in this repository were structured using an AI-assisted pipeline.
* **The Methodology:** I captured raw, unstructured testing notes, hypotheses, and messy system logs during exploration. I then engineered strict prompts using a Large Language Model to automatically parse, format, and structure this raw data into the production-ready Jira tickets included above.
* **Impact:** This approach allows for continuous, uninterrupted exploratory testing while ensuring the resulting documentation remains highly technical, readable, and perfectly formatted for development teams.
