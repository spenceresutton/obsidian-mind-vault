---
description: "Review pending Navigator sanity test cases one at a time. Approve to move to approved/, revise inline, or reject. Mirrors the LinkedIn post approval workflow."
---

Review Navigator sanity test cases in `reference/Navigator/Cases/pending/`.

**Arguments (optional):** specific case file path or case number to review. If none, review all pending cases in order.

$ARGUMENTS

## Steps

1. **List pending cases.** Glob `reference/Navigator/Cases/pending/*.md`. If none found, report "No pending cases." and stop.

2. **For each pending case** (or the specified case):

   a. **Display the full case** — show all sections including Expected Output.

   b. **Present review options:**
      - **Approve** — case is correct as-is
      - **Revise** — make specific edits, then approve
      - **Reject** — discard this case
      - **Skip** — come back to this one later

   c. **If Approve:**
      - Update frontmatter: `status: approved`, `author: Spencer` (if originally `Claude`)
      - Move file from `pending/` to `approved/` using `git mv` to preserve history
      - Confirm: "Case {case_number} approved and moved to approved/."

   d. **If Revise:**
      - Ask Spencer what to change, or apply edits if Spencer describes them inline
      - Show the revised case
      - Loop back to review options

   e. **If Reject:**
      - Confirm before deleting: "Delete {filename}? This cannot be undone."
      - On confirmation: delete the file
      - Log rejection: note the case number and reason in the review summary

   f. **If Skip:**
      - Leave the file in pending/ with no changes
      - Move to the next pending case

3. **After all cases are reviewed**, report:
   - Cases approved: list with case numbers and file paths
   - Cases revised and approved: list
   - Cases rejected: list with reasons
   - Cases skipped: list

4. **Prompt:** "Would you like to run `/om-case-export` to format the newly approved cases for the Google Doc?"
