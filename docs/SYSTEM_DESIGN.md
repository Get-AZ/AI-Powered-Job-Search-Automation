# System Design

## Objective
Create a human-reviewed job application draft tracker using n8n, Remote OK, Google Gemini, Python Code nodes, and Google Sheets.

## Connected path
Schedule Trigger → Remote OK HTTP Request → keyword/title filter → location flag → Gemini job evaluation → parse and rank → score >=70 → Gemini cover-letter draft → Gemini review → application record preparation → existing Sheets lookup + Merge3 → URL deduplication → append new drafts.

## Data contracts
Job candidate: title, company, location, url, description, source.
Evaluation: match_score, matching_skills, missing_or_unverified_skills, location_eligibility, recommendation, reason.
Application draft: rank, company, title, location, match_score, recommendation, application_url, location_eligibility, final_cover_letter, application_status, review_required, source.

## Control points
- No application submission action.
- Work authorization and geographic eligibility are unverified until human review.
- Google Sheets lookup is configured to execute once and return all rows.
- Deduplication lowercases URLs and strips trailing slashes.
- A no-output result prevents an append when all candidates already exist.

## Risks
Position-based merges can misassociate records if model responses change cardinality. JSON parsing by string splitting is fragile. API quotas, source schema changes, and empty results need explicit regression tests. Remotive and Arbeitnow are disconnected.
