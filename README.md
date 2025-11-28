# n8n-sales-report-assistant
Chat-driven n8n workflow that aggregates sales data, generates charts, and sends a narrative email report.

n8n Sales Report Assistant
Automated n8n workflow that analyzes sales data with Gemini, generates charts, and sends a visual email summary.
The workflow turns a simple chat-style question (like “What is the sales for the West region?”) into an AI-written report with line, bar, and pie charts embedded in an HTML email.

Features
Chat-style input to request specific sales insights (e.g. by region, category, or time period).

Automatic aggregation of sales data from a spreadsheet (Google Sheets or CSV via n8n).

Generation of line, bar, and pie charts using QuickChart image URLs.

Gemini-powered narrative summary describing totals, averages, best and worst performers.

HTML email report sent through Gmail with charts and written commentary.

Workflow overview
The workflow consists of several nodes executed in sequence:

Trigger / Chat input

Starts the workflow when a chat message or manual execution is received.

Data Analyst (AI Agent)

Interprets the user’s request.

Selects the right filters (e.g. region = “West”) and prepares two arrays: labels and numeric values.

Clean Data

Cleans and formats labels and values into a structure that can be passed to the reporting model and chart URLs.

Write Report (Gemini)

Receives the labels and values arrays.

Produces a concise, professional English summary (totals, averages, highest/lowest performer, and brief commentary).

Write HTML

Builds QuickChart URLs for line, bar, and pie charts using the cleaned data.

Combines chart URLs and the Gemini summary into a single JSON object ready for email.

Gmail: Send a message

Uses an HTML template that embeds:

The Gemini summary.

The three chart images (line, bar, pie).

Sends the final email report to the configured recipient.
