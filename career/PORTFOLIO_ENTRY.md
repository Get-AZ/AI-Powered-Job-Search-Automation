# AI-Powered Job Search Automation

**Category:** Generative AI / Workflow Automation / Data Integration

**Stack:** n8n, Python Code nodes, Google Gemini, Remote OK REST API, Google Sheets.

**Problem:** Manually locating relevant roles, assessing fit, drafting letters, and tracking applications is repetitive and prone to duplicate entries.

**Approach:** An n8n pipeline retrieves remote listings, filters titles, flags location eligibility for verification, asks Gemini to evaluate job fit against a verified profile, ranks candidates, drafts and reviews cover letters, and appends only previously unseen URLs to a Google Sheets tracker.

**Controls:** Applications remain drafts; human review is required. The workflow does not submit applications or claim verified eligibility.

**Observed testing:** Two existing applications produced zero new records; a separate duplicate test reduced two identical synthetic new jobs to one.

**Limitations:** The export was inactive, production scheduling has not been validated, and Remotive/Arbeitnow nodes are disconnected. The public workflow is a sanitized template requiring private configuration.

**Repository:** https://github.com/Get-AZ/AI-Powered-Job-Search-Automation
