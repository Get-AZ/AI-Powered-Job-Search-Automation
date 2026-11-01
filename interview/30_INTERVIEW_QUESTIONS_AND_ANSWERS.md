# 30 Interview Questions and Model Answers

These answers describe the uploaded workflow and observed manual tests. They do not claim a verified production deployment.

## 1. What problem does this project solve?

It reduces repetitive job discovery, preliminary fit assessment, cover-letter drafting, and duplicate tracking while retaining human review.

## 2. Why n8n?

It connects APIs, model calls, transformations, scheduling, and Google Sheets in an inspectable node-based workflow.

## 3. What triggers the pipeline?

A Schedule Trigger configured for a daily run; the exported workflow was inactive, so a production schedule is not verified.

## 4. Which job sources are active?

The connected path uses Remote OK. Remotive and Arbeitnow nodes exist but are disconnected.

## 5. How is job data retrieved?

An HTTP Request node calls the Remote OK API, then Python Code nodes normalize and filter fields.

## 6. How are relevant titles selected?

Python checks job titles for predefined data, AI, ML, cloud, and related role keywords.

## 7. Why check location?

Remote roles can restrict hiring geography. The workflow flags locations for verification rather than assuming eligibility.

## 8. What does Gemini do first?

It compares the job description against a verified candidate profile and returns an estimated match and supporting reasons.

## 9. Is match_score an employer score?

No. It is an AI-generated screening estimate for prioritization, not a hiring probability or employer assessment.

## 10. Why use a threshold of 70?

The workflow uses 70 as a configurable heuristic to limit downstream letter generation; it has not been calibrated statistically.

## 11. How are jobs ranked?

A Python Code node sorts records by numeric match_score in descending order and assigns ranks.

## 12. How are cover letters drafted?

A Gemini prompt combines the job title, employer, description, and verified candidate qualifications.

## 13. Why a second Gemini pass?

It reviews the draft for unsupported claims, inaccurate experience, and professional tone.

## 14. Why still require human review?

Models can omit application instructions, hallucinate achievements, or misinterpret work authorization and job eligibility.

## 15. How are candidate records represented?

The final draft record includes company, title, location, score, recommendation, URL, eligibility flag, cover letter, status, and source.

## 16. Why use Google Sheets?

It offers an accessible tracker for reviewing drafts and manually updating application statuses.

## 17. How does duplicate detection work?

The workflow reads existing sheet rows, merges them with proposed records, and compares normalized application URLs.

## 18. How are URLs normalized?

The Python filter strips surrounding whitespace, lowercases, and removes trailing slashes.

## 19. What URL edge cases remain?

Tracking parameters, redirects, alternate domains, and job reposts may still bypass simple normalization.

## 20. What does Execute Once change?

The Google Sheets lookup reads the sheet once per workflow execution instead of once for each candidate item.

## 21. Why enable Always Output Data on lookup?

It allows a placeholder item if the lookup returns nothing, so a downstream comparison may still proceed; empty-sheet behavior needs a dedicated test.

## 22. Why disable Always Output Data on Filter New Jobs?

If there are no new jobs, the append node should receive zero items and skip writing.

## 23. What manual duplicate tests passed?

Two existing candidate URLs produced zero new rows; two identical synthetic new URLs produced one appended test row.

## 24. What is the risk of Merge by Position?

If one branch drops or reorders items, job evaluations and letters can be attached to the wrong candidate.

## 25. What is fragile about the Gemini parser?

String splitting assumes a particular JSON layout and may fail when Gemini changes formatting or escapes.

## 26. How would you improve parsing?

Use validated JSON parsing with required-field checks, numeric bounds, and error handling.

## 27. How would you improve observability?

Log execution IDs, source counts, model failures, duplicate counts, append counts, and alert on exceptions.

## 28. What security precautions matter?

Do not publish credentials, private CV prompts, Google Sheets identifiers, or application drafts; use scoped n8n credentials.

## 29. Does the workflow submit job applications?

No. It generates and tracks drafts; the applicant reviews and submits manually.

## 30. What is the next production milestone?

Test a new job through the complete connected path, verify sheet writes and job-letter pairing, then publish and observe a scheduled run.
