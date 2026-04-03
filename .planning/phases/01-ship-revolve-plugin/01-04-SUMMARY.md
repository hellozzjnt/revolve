---
phase: 01-ship-revolve-plugin
plan: 04
subsystem: skills
tags: [yt-dlp, youtube, transcript, research, skill]

requires:
  - phase: 01-ship-revolve-plugin
    provides: config-contract.md and config.md output_dir pattern established in plans 02-03

provides:
  - yt-search skill with English description and transcript extraction
  - Dependency check for yt-dlp at skill entry point
  - Config-driven output_dir path reading from config.md
  - 5-step workflow: check deps -> read config -> search -> select -> extract transcript -> save

affects:
  - research-pipeline (can receive yt-search transcript output)
  - any future skills that need yt-dlp dependency checking pattern

tech-stack:
  added: []
  patterns:
    - "Dependency check as Step 0 before any action"
    - "Config.md YAML frontmatter read for output_dir"
    - "Transcript saved with YAML frontmatter (source, url, title, date)"

key-files:
  created: []
  modified:
    - skills/yt-search/SKILL.md

key-decisions:
  - "Preserved original yt-dlp --flat-playlist --dump-json search approach from source skill (battle-tested)"
  - "Added transcript extraction as a natural extension of search, completing the research workflow"
  - "Abort on missing yt-dlp rather than fallback — dependency is non-negotiable for core function"

patterns-established:
  - "Step 0 dependency check pattern: which <tool> -> inform + abort if missing"
  - "Step 1 config.md read pattern: extract output_dir from YAML frontmatter"

requirements-completed: [R17, R18, R19]

duration: 3min
completed: 2026-04-03
---

# Phase 01 Plan 04: yt-search Skill Summary

**yt-search skill ported from ~/.claude with English description, yt-dlp dependency check, config-driven output path, and transcript extraction workflow**

## Performance

- **Duration:** ~3 min
- **Started:** 2026-04-03T01:45:00Z
- **Completed:** 2026-04-03T01:46:09Z
- **Tasks:** 2
- **Files modified:** 1

## Accomplishments

- Read and analyzed source skill at ~/.claude/skills/yt-search/SKILL.md
- Rewrote SKILL.md with full English description (frontmatter + body)
- Added Step 0 dependency check: `which yt-dlp` -> abort with install instructions if missing
- Added Step 1 config.md reading: extracts `output_dir` from YAML frontmatter, with fallback
- Added Steps 3-5: video selection, transcript extraction via yt-dlp subtitles, save with frontmatter

## Task Commits

1. **Task 1: Read source skill** - (no commit, read-only task)
2. **Task 2: Create ported SKILL.md** - `03028b7` (feat)

## Files Created/Modified

- `skills/yt-search/SKILL.md` - Full rewrite: English, dependency check, config path, transcript workflow

## Decisions Made

- Preserved `--flat-playlist --dump-json` search approach with python3 parsing from the source skill — it's well-tested and produces clean structured output
- Extended skill beyond search-only to include transcript extraction (Steps 3-5) per plan specification
- Used abort pattern for missing yt-dlp: better UX than silent failure on search

## Deviations from Plan

None - plan executed exactly as written.

## Issues Encountered

None - the worktree already had a skeleton SKILL.md that was replaced with the full implementation.

## User Setup Required

None - no external service configuration required.

## Next Phase Readiness

- yt-search skill ready for use in research workflows
- Integrates with /research-pipeline via saved transcript file path
- Any future skills requiring yt-dlp can follow the Step 0 dependency check pattern established here

---
*Phase: 01-ship-revolve-plugin*
*Completed: 2026-04-03*
