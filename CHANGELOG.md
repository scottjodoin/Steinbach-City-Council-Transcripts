# Changelog

Corrections and releases, newest first. Each release is a dated version you can cite.

## 2026-11-16

- Added the text of the city's agendas (`agendas/`, 77) and minutes (`minutes/`, 96) from November 2022 on, with
  members of the public's names withheld as in the transcripts. New agendas and minutes are now added
  automatically every day, including the agenda for the next meeting once the city posts it.
- `meetings.csv`: new columns `agenda_text` and `minutes_text`, and rows for upcoming meetings (`upcoming`) and for
  meetings with minutes but no transcript (`no transcript`). Meetings already transcribed but not yet
  speaker-checked show as `pending`.

## 2026-11-14 (update)

- Renamed the `substance` field to `line_type`, with values `statement`, `procedure` and `short` (were
  `substantive`, `procedural`, `minor`). It describes the form of a line, not the value of what was said.
- Added AGENT_GUIDE.md: how to point an AI agent at these transcripts.

## 2026-11-14

- First release: all 88 council meetings from November 1, 2022 to November 3, 2026, transcribed with a
  local-names vocabulary, speaker-identified, privacy-filtered, and checked word by word against YouTube's
  captions. Every line carries a speaker confidence level and a line type.
- Meetings before November 2022 are not included yet; `meetings.csv` lists them as `pending`.
