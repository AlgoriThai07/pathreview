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

**Reproduction commit link:** [link to commit documenting the reproduced issue]

**Reproduction summary:**


**PLAN.md link:** [link to PLAN.md in your fork]

**Walkthrough video (recommended):** [link to your Loom video, ≤2 min — recommended, not graded]

**Blockers or open questions:**
[Anything you're still uncertain about going into Week 9, or leave blank]