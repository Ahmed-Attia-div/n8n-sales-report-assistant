# n8n Sales Report Assistant

An automated n8n workflow that analyzes sales data using the Gemini API, generates charts via QuickChart, and sends a complete HTML email report containing AI-generated insights and visualizations.

This workflow turns a simple chat-style question such as **“What are the total sales in the West region?”** into a fully formatted report containing:

- 📊 Line, bar, and pie charts  
- 🧠 Gemini-written narrative summary  
- 📩 Automatically emailed HTML report  

---

## 🚀 Features

- **Chat-style inputs** — ask questions about regions, product categories, periods, etc.
- **Automatic data aggregation** from Google Sheets or CSV.
- **QuickChart visualization** (line, bar, pie) using generated image URLs.
- **Gemini AI summary** with totals, averages, highest/lowest performers, and commentary.
- **Stylish HTML email report** sent directly via Gmail.
- **Reusable + customizable prompts and chart templates.**

---

## 🧩 Workflow Overview (Node by Node)

The workflow consists of these main nodes:

### 1. **Trigger / Chat Input**
Starts execution through manual trigger, webhook, schedule, or chat-like input.

### 2. **Data Analyst (Gemini / AI Agent)**
- Understands the user question  
- Determines filters  
- Outputs:
  - `labels[]`
  - `values[]`

### 3. **Clean Data**
- Formats and sanitizes the arrays  
- Prepares them for chart URL generation and summary writing

### 4. **Write Report (Gemini)**
- Receives `labels` and `values`
- Produces a professional English summary (JSON)
- Includes:
  - Total  
  - Average  
  - Best / worst performer  
  - Short insights

### 5. **Write HTML**
- Builds QuickChart URLs:
  - Line chart  
  - Bar chart  
  - Pie chart  
- Combines everything into a JSON payload ready for Gmail

### 6. **Gmail: Send a Message**
Sends:
- Gemini summary
- 3 chart images
- Beautiful HTML layout

---

## 📁 Repository Structure

Recommended folder layout:

/
│ README.md
│ LICENSE
│
├── workflow/
│ └── sales-report-workflow.json
│
├── images/
│ ├── workflow-canvas.png
│ ├── gemini-node.png
│ ├── gmail-template.png
│ └── sample-email.png
│
└── data/ (optional)
└── sample-sales-data.csv

markdown
Copy code


---

## 📸 Screenshots

You may add screenshots for better documentation:

- **Workflow overview:** `images/workflow-canvas.png`
- **Gemini node:** `images/gemini-node.png`
- **Gmail template:** `images/gmail-template.png`
- **Final email:** `images/sample-email.png`

To embed images in your GitHub README later, use:

```markdown
![Workflow Overview](images/workflow-canvas.png)
---
```
## ⚙️ Setup

### **Prerequisites**
Before importing the workflow, make sure you have:

- n8n (cloud or self-hosted)
- Google Sheets data source **or** CSV file
- Gmail API credentials configured in n8n
- Gemini API access (Google AI Studio / PaLM)
- QuickChart (no account required)

---

## 🔧 Installation Steps

1. **Clone this repository**

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPO.git
```

2. **Import the workflow into n8n**
In n8n:
Menu → Import from File → select:

workflow/sales-report-workflow.json


3. **Configure necessary credentials in n8n**

Google Sheets (or CSV reading node)

Gemini API (for Data Analyst + Write Report nodes)

Gmail API (for sending the email)

4. **Update workflow parameters**

Spreadsheet ID or CSV path

Email recipient

Any environment variables

Prompts (optional)

5. **Activate the workflow**
Test with a question such as:

“What is the sales for the West region?”
