# Test Plan

## Observed manual checks
1. Existing Sheets lookup returned two saved application rows after Execute Once was enabled.
2. Merge3 returned four items: two candidate records and two existing rows.
3. Filter New Jobs returned no output, as expected for two duplicate URLs.
4. A synthetic test with two identical new URLs yielded one appended test row, which was later deleted.

## Additional tests before production
- First-run case: empty sheet with a new candidate.
- One new + one existing candidate in the same execution.
- Different URL case, trailing slash, query parameters, and missing URLs.
- Multiple Gemini results, invalid JSON, partial failures, and empty outputs.
- Verify the correct job is paired with its own evaluation and cover letter.
- Confirm Sheets statuses already marked Applied or Interview Scheduled remain unchanged.
- Confirm scheduled execution, timezone, error reporting, and no automated submission.

The checks above are limited functional tests, not proof of end-to-end production reliability.
