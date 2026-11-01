# Detailed Technical CV Project Entry

**AI-Powered Job Search & Application Draft Tracker — Portfolio Project**

**Technologies:** n8n Cloud, Python Code nodes, Google Gemini, HTTP/REST APIs, Remote OK, Google Sheets, JSON.

**Responsibilities and implementation**
- Designed an event-driven workflow initiated by a daily Schedule Trigger.
- Integrated Remote OK job listings and applied keyword-based filtering and location-status flags.
- Created Gemini prompts for evidence-based candidate-job matching, gap analysis, estimated fit scoring, and personalized cover-letter drafts.
- Implemented a second Gemini review stage intended to remove unsupported claims and retain human approval.
- Parsed model responses, ranked opportunities, and applied a match-score threshold of 70.
- Combined proposed application records with existing Google Sheets rows and implemented normalized-URL duplicate detection in Python.
- Preserved manually updated application statuses by appending only new records rather than overwriting existing rows.
- Performed manual duplicate tests: two existing URLs were skipped, and two identical synthetic URLs were reduced to one appended test record.

**Governance and limitations:** Applications are not submitted automatically; work eligibility is not assumed. Connected job discovery currently uses Remote OK; other source branches are disconnected. Scheduled production operation is not yet verified. The published workflow is a sanitized template.
