<h1>Status.im QA Defect Analysis & Exploratory Testing 🐞 </h1>

<b>Focus Areas: Mobile Performance Profiling (ADB Logcat), Desktop Backend Debugging, and AI-Assisted QA Workflows.</b>
<h3>📋 Executive Summary</h3>
This repository contains the results of an unscripted, exploratory testing session across the Status.im ecosystem (Android and Windows Desktop). <br>
The objective was to move beyond surface-level UI testing and identify high-impact system defects, extract the underlying error logs, and document them using industry-standard Agile methodologies (Jira).

<h3>🧪 Testing Scope & Findings</h3>
During this session, I conducted performance profiling via ADB on the Android mobile client, successfully isolating <b> a P1 10.7-second UI thread freeze caused by a Slow Binder warning.</b><br>
Additionally, through data sync verification and backend log monitoring on the Windows Desktop application, I uncovered a P1 functional crash in the Market tab triggered by JSON.parse and IndexDefect errors.

<h4>📱 Bug 1:Mobile UI Freeze (Performance)Issue:</h4> 
The main UI thread locks up completely for ~10.7 seconds during login/navigation. <br>
<b>Root Cause Analysis: Extracted adb logcat data reveals a severe Slow Binder warning on app.status.mobile.ipc.IStatusGoService.</b> <br>
The background data sync monopolizes the main thread, resulting in a temporary Application Not Responding (ANR) state.
Artifacts Provided: Screen recording, raw .txt system logs, and formal Jira ticket.
📂 [View Mobile Bug Artifacts Here]

<h4>💻 Bug 2: Market Tab Crash & Sync Failure (Functional)Issue:</h4>
Navigating to the Market tab triggers an unhandled IndexDefect, causing a fatal crash.
<b>Root Cause Analysis: Desktop logs reveal upstream failures during initial state loading, specifically a JSON.parse syntax error while handling revealed addresses and an ENS resolver failure (ens_getName).</b><br>
Artifacts Provided: UI error stack trace screenshot, background electron logs, and formal Jira ticket.
📂 [View Desktop Bug Artifacts Here](Link to your Desktop_Market_Bug folder)

<h4>🤖 QA Workflow Optimization: AI-Assisted Reporting</h4>
To optimize the manual testing lifecycle and reduce administrative overhead, the defect reports in this repository were structured using an AI-assisted pipeline.<br>
<b>* The Methodology: </b> I captured raw, unstructured testing notes, hypotheses, and messy system logs during exploration. 
I then engineered strict prompts using a Large Language Model to automatically parse, format, and structure this raw data into the production-ready Jira tickets included above.<br>
<b>* Impact: </b>This approach allows for continuous, uninterrupted exploratory testing while ensuring the resulting documentation remains highly technical, readable, and perfectly formatted for development teams.
