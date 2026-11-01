# LinkedIn Project Announcement

Built an AI-powered job-search and application-draft tracking workflow using **n8n, Google Gemini, Python, REST APIs, and Google Sheets**.

The connected workflow retrieves Remote OK job listings, filters relevant roles, estimates resume-to-job fit, ranks opportunities, generates and reviews tailored cover-letter drafts, and checks existing spreadsheet URLs to avoid duplicate entries.

**Validation:** In manual tests, two candidate jobs were correctly identified as already tracked, resulting in zero new rows. A separate synthetic duplicate test collapsed two identical URLs into one record.

The workflow is designed for **human review** and does not submit applications. The public GitHub version is a sanitized configuration template; scheduled production execution is not yet verified.

GitHub: https://github.com/Get-AZ/AI-Powered-Job-Search-Automation

#n8n #WorkflowAutomation #GenerativeAI #Python #GoogleGemini #MLOps #Portfolio
