# Steinbach City Council meeting transcripts

Searchable, speaker-labelled transcripts of City of Steinbach (Manitoba) council meetings, November 2022 onward,
made from the city's own meeting videos. Every line links to the moment in the video where it was said.

This is an independent civic project, not affiliated with the City of Steinbach. The official record is the
city's video and its published minutes. These transcripts are a way to search and read them.

- Reports built from this data: <https://steinbachcitycouncilreporting.ca/>
- How accurate it is: [ACCURACY.md](ACCURACY.md), and in plain language: <https://steinbachcitycouncilreporting.ca/data-accuracy/>
- Found an error? See [CORRECTIONS.md](CORRECTIONS.md) or email steinbachcitycouncilreporting@gmail.com

## What's here

| Path | What it is |
|---|---|
| `meetings.csv` | One row per meeting: date, type, video link, links to the city's minutes/agenda/package where known, whether a transcript is published, its speaker-confidence mix, and the share of substantive lines with high confidence |
| `transcripts/<year>/<id>.txt` | The transcript to read: `[hh:mm:ss] Speaker (Role): what they said` |
| `transcripts/<year>/<id>.json` | The same transcript as data: one record per line (see below) |
| `speaker_maps/<year>/<id>.json` | Who each voice in the recording is, with the evidence and a confidence level |
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
     "label": "Earl Funk (Mayor)", "text": "...", "substance": "procedural", "video_url": "https://www.youtube.com/watch?v=...&t=257s"}
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
| `substance` | How much the line matters if its speaker is wrong: `substantive` (a question, position, explanation or reply), `procedural` (moving, seconding, calling the vote, handing over the floor) or `minor` ("Thank you.", "Yes."). Set by fixed rules from the words, so approximate. |
| `voice` | The voice-cluster letter from the transcription service; useful only within one meeting |
| `video_url` | Opens the video at this line |

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
  Most uncertain lines are short interjections; `substance` lets you set those aside.
- **Cite it** as: *Steinbach City Council meeting transcripts (independent), version <date>, from the City of
  Steinbach's meeting videos.* Versions are listed in [CHANGELOG.md](CHANGELOG.md).

## Licence

The transcripts, speaker maps and other files in this repository are dedicated to the public domain under
[CC0 1.0](LICENSE.md): use them for anything, no permission needed. The meeting videos and minutes belong to the
City of Steinbach and are linked, not copied.
