## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/147

**Issue title:** Resume section detection fails on text with leading whitespace

**Tier:** [X] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
When parsing resumes, the section header detection logic in `ResumeParser` (`ingestion/parsers/resume_parser.py`) uses regular expression patterns that strictly anchor headers to the start of a line without leading indentation. However, text extracted from PDFs or Markdown files commonly contains leading spaces or tabs before headers such as "Education:" or "Skills:". Because of this strict matching, indented headers fail to match and `detected_sections` returns empty. A successful fix will update the regex patterns in `_detect_sections()` to permit optional leading whitespace (`^[ \t]*`), enabling reliable section detection across all resume formats.

**Branch name:** fix/147-resume-fails-leading-whitespace

**Setup confirmation:** [X] App runs locally at localhost:5173

**Cohort ledger:** [X] Issue added to cohort ledger

## Week 8 — Reproduction & solution planning

**Reproduction commit link:** [\[link to commit documenting the reproduced issue\]](https://github.com/ascherj/pathreview/commit/79fa96fd168ebfdcaf993f494a968d81d69f186e)

**Reproduction summary:**
I reproduced the issue by running the unit tests (specifically `test_detect_sections_with_leading_whitespace`). I observed that 6 unit tests failed because both the section header detection and markdown header stripping regexes strictly anchored matches to the absolute beginning of a line without permitting leading indentation (whitespace/tabs).

**PLAN.md link:** [\[link to PLAN.md in your fork\]](https://github.com/AlgoriThai07/pathreview/blob/fix/147-resume-fails-leading-whitespace/PLAN.md)

**Walkthrough video (recommended):**

**Blockers or open questions:**