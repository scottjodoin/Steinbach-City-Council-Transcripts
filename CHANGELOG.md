# Changelog

Corrections and releases, newest first. Each release is a dated version you can cite.

## 2026-11-14 (update)

- Renamed the `substance` field to `line_type`, with values `statement`, `procedure` and `short` (were
  `substantive`, `procedural`, `minor`). It describes the form of a line, not the value of what was said.
- Added AGENT_GUIDE.md: how to point an AI agent at these transcripts.

## 2026-11-14

- First release: all 88 council meetings from November 1, 2022 to November 3, 2026, transcribed with a
  local-names vocabulary, speaker-identified, privacy-filtered, and checked word by word against YouTube's
  captions. Every line carries a speaker confidence level and a line type.
- Meetings before November 2022 are not included yet; `meetings.csv` lists them as `pending`.
