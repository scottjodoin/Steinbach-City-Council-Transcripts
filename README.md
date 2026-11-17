# Steinbach City Council meeting transcripts

Searchable, speaker-labelled transcripts of City of Steinbach (Manitoba) council meetings, November 2022 onward,
made from the city's own meeting videos. Every line links to the moment in the video where it was said.

This is an independent civic project, not affiliated with the City of Steinbach. The official record is the
city's video and its published minutes. These transcripts are a way to search and read them.

- Reports built from this data: <https://steinbachcitycouncilreporting.ca/>
- How accurate it is: [ACCURACY.md](ACCURACY.md), and in plain language: <https://steinbachcitycouncilreporting.ca/data-accuracy/>
- Research it with your own AI agent: [AGENT_GUIDE.md](AGENT_GUIDE.md)
- Found an error? See [CORRECTIONS.md](CORRECTIONS.md) or email steinbachcitycouncilreporting@gmail.com

## What's here

| Path | What it is |
|---|---|
| `meetings.csv` | One row per meeting: date, type, video link, links to the city's minutes/agenda/package where known, the paths of the agenda and minutes text (`agenda_text`, `minutes_text`), the status (`published`, `pending` = transcript not yet speaker-checked, `upcoming`, `no transcript`), the speaker-confidence mix, and the share of statement lines with high confidence |
| `transcripts/<year>/<id>.txt` | The transcript to read: `[hh:mm:ss] Speaker (Role): what they said` |
| `transcripts/<year>/<id>.json` | The same transcript as data: one record per line (see below) |
| `speaker_maps/<year>/<id>.json` | Who each voice in the recording is, with the evidence and a confidence level |
| `agendas/<year>/<id>.txt` | The text of the city's agenda for the meeting, including upcoming meetings (see [below](#the-citys-agendas-and-minutes)) |
| `minutes/<year>/<id>.txt` | The text of the city's minutes: motions, votes, who moved and seconded, what was presented |
| `roster.csv` | Mayors, councillors and senior staff, with the dates they held each role |

A meeting `id` is its date (`2026-10-06`), with a suffix when there was more than one video that day
(`2025-02-18_financial-plan-hearing`, `_part2`).

### Reading a transcript

```
[00:04:17] Earl Funk (Mayor): Thank you, Councillor Hiebert. Council, we have the agenda in front of us...
[00:45:28] Damian Penner (Councillor) [medium]: We are in the middle of unprecedented growth...
[00:18:26] Unidentified (possibly Michael Zwaagstra) [low]: ...
[00:22:35] Resident 4: Hello. My name is [Resident 4], and I live on Example Street...
```

- No tag means the speaker is identified with **high** confidence. `[medium]` and `[low]` mark less certain
  identifications; low-confidence lines never show a confident name.
- Members of the public are **not named**. Each resident who speaks is `Resident 1`, `Resident 2`… within that
  meeting (numbers do not carry across meetings). Their names in the spoken text, and the names of other private
  individuals mentioned (applicants, letter writers, neighbours), are replaced with `[Resident N]` or
  `[name withheld]`. Phone numbers and email addresses are removed. Street addresses that people give are
  kept, because zoning, variance and development discussions depend on them. Residents appointed by council to a
  board or committee are named, as public appointments recorded in the minutes.
- The time `[hh:mm:ss]` is where the line starts in the video.

### JSON fields (`transcripts/<year>/<id>.json`)

```json
{
  "meeting": "2026-10-20",
  "title": "Regular City Council Meeting - October 20, 2026",
  "video_url": "https://www.youtube.com/watch?v=...",
  "lines": [
    {"time": "00:04:17", "seconds": 257, "speaker": "Earl Funk", "possibly": null, "role": "mayor",
     "title": "Mayor", "organization": null, "confidence": "high", "human_checked": false, "voice": "B",
     "label": "Earl Funk (Mayor)", "text": "...", "line_type": "procedure", "video_url": "https://www.youtube.com/watch?v=...&t=257s"}
  ]
}
```

| Field | Meaning |
|---|---|
| `speaker` | The person's name, or `null` when unidentified or low confidence. Residents appear as `Resident N`. |
| `possibly` | For low-confidence lines, the best guess (otherwise `null`) |
| `role` | `mayor`, `councillor`, `staff`, `delegation` (speaking for an organization or applicant), `resident`, `group` (several people at once), `unknown` |
| `confidence` | `high`, `medium` or `low` (see [ACCURACY.md](ACCURACY.md)) |
| `human_checked` | `true` if a person listened to this line and confirmed or corrected the speaker |
| `line_type` | The form of the line: `statement` (a statement, question, explanation or reply), `procedure` (moving, seconding, calling the vote, handing over the floor) or `short` ("Thank you.", "Yes."). Set by fixed rules from the words, so approximate. It describes form, not the value of what was said: don't use it to compare people. |
| `voice` | The voice-cluster letter from the transcription service; useful only within one meeting |
| `video_url` | Opens the video at this line |

### The city's agendas and minutes

`agendas/` and `minutes/` hold the text of the City of Steinbach's own agenda and minutes PDFs (from
<https://events.steinbach.ca/council>, and the city's old website through the Internet Archive), so that people and
AI tools can search and read them next to the transcripts. They are checked for new and revised documents every
day: an agenda appears here once the city posts it, usually the week before the meeting, and the minutes once
council has approved them.

- **The PDF is the official record.** Each file starts with a link to it. The text is copied as the PDF lays it out
  (line breaks and page numbers kept); tables can come out jumbled.
- **Names of members of the public are withheld**, as in the transcripts: `[Resident N]` is the same person as
  Resident N in that meeting's transcript; `[name withheld]` is anyone else (property owners, applicants, letter
  writers, people on permit and licence lists). Street addresses are kept. Pages that list property tax roll
  entries are left out. Council, staff, people speaking for an organization or an applicant, board and committee
  appointees and officials of other governments are named.
- The names are withheld by an automatic filter that errs toward withholding, so it sometimes hides a name that is
  public (and the filter can miss one: please report it, see [CORRECTIONS.md](CORRECTIONS.md)).
- Agendas before mid-2025 were published inside the meeting package; where only the package was available, the
  agenda text is the agenda pages of the package. Some 2022–2024 agendas were never archived and are missing.

## How it was made

1. **Transcription.** Each meeting video on the city's YouTube channel was transcribed by
   [AssemblyAI](https://www.assemblyai.com/) (Universal-3.5 Pro) with speaker separation, using a vocabulary of
   council members' and staff names and every Steinbach street name so local names are heard correctly.
2. **Word check.** The transcript was compared word by word with YouTube's automatic captions of the same video.
   A known transcription habit, inserting "Your Worship" where nobody said it, is removed where YouTube heard
   nothing there. Council members' and staff names are spelled as in the city's minutes.
3. **Speaker identification.** Each voice was matched to a person from the meeting itself (the chair handing the
   floor to a councillor by name, people introducing themselves) and from the city's minutes (who moved and
   seconded each motion, who asked which question), with AI assistance. Every match records its evidence and a
   confidence level in `speaker_maps/`. Recorded votes are never used to decide who is speaking.
4. **Human review.** A person listened to uncertain spots and to random samples, and corrected errors. Lines a
   person checked are marked `human_checked`.
5. **Privacy filter.** Residents' names are removed as described above, then every transcript is checked for
   anything that still looks like a private individual's name before it is published here.

## Using this data

- **Quote the video, not just the transcript.** Transcription errors happen. Follow the `video_url` before
  relying on an exact quote, and use the minutes for decisions and votes.
- **Watch the confidence.** For analysis by speaker, consider using only `high` (and perhaps `medium`) lines.
  Most uncertain lines are short replies (`line_type` `short`).
- **Cite it** as: *Steinbach City Council meeting transcripts (independent), version <date>, from the City of
  Steinbach's meeting videos.* Versions are listed in [CHANGELOG.md](CHANGELOG.md).

## Licence

The transcripts, speaker maps and other files made for this repository are dedicated to the public domain under
[CC0 1.0](LICENSE.md): use them for anything, no permission needed. The meeting videos belong to the City of
Steinbach and are linked, not copied. The text in `agendas/` and `minutes/` is the City of Steinbach's public
record, copied (with members of the public's names withheld) so it can be searched; it is the city's material and
is not covered by the CC0 dedication.
