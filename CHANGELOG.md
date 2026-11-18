# Changelog

Corrections and releases, newest first. Each release is a dated version you can cite.

## 2026-11-18

- Added the November 17, 2026 regular meeting (121 lines: 81.0% high, 15.7% medium, 3.3% low confidence).
  Councillor Falk has no voice cluster of his own in this recording; four short replies are marked
  "Unidentified (possibly Ron Falk)". The two Councillors Hiebert are told apart by voice pitch only, so their lines
  are medium confidence.
- `meetings.csv`: package links filled in for 19 meetings, and the November 1, 2022 minutes link now points to that
  day's regular meeting minutes (it pointed to the inaugural meeting's).
- Document links now follow the meeting, not just the date: on days with two meetings each row links its own
  meeting's documents, and a meeting's main package wins over "additional information" or "supplemental" add-ons
  (April 1, 2025 now links the main package). Links to the city's old document addresses, which no longer work,
  were replaced with the Internet Archive's copy (January 16, 2024 minutes); the November 4, 2025 organizational
  minutes have no working copy online and now say so.

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
