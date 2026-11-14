# How accurate are these transcripts?

*Generated from the data in this repository; updated with every release.*

Short version: the words are right about 95 times in 100, council members' and staff names are spelled from the
official roster, and 91% of lines name the speaker with high confidence. Always check an exact
quote against the video (every line links to it).

## Speakers

88 meetings, 10,337 lines:

| Confidence | What it means | Lines |
|---|---|---|
| high | Two or more independent clues agree (e.g. the chair names the person, and the minutes record their motion) | 9,443 (91%) |
| medium | One clear clue, or the only person it could be. Shown as `[medium]` | 584 (6%) |
| low | A best guess. Shown as `Unidentified (possibly …) [low]`, never as a confident name | 310 (3%) |

### Which lines matter

A wrong name on "Thank you." changes nothing; a wrong name on a councillor's argument puts words in someone's
mouth. Every line has a `substance` score, set by fixed rules from the words in the line (not by a person, and not
always right on long mixed lines), so you can weigh the uncertain lines by how much they matter:

| Substance | What it means | Lines | high | medium | low |
|---|---|---|---|---|---|
| substantive | Says something: a question, a position, an explanation, a presentation, a reply | 4,804 (46%) | 95.2% | 3.8% | 1.0% |
| procedural | Runs the meeting: moving, seconding, calling the vote, handing over the floor | 2,993 (29%) | 96.8% | 2.6% | 0.6% |
| minor | Courtesy and acknowledgement: "Thank you.", "Yes.", "Okay." | 2,540 (25%) | 77.7% | 12.8% | 9.6% |

Most uncertainty sits on short interjections, where it matters least. For anything you quote, filter to
`substance == "substantive"` and `confidence == "high"`, and still check the video.

46 lines were checked by a person listening to the video (`human_checked`).
Random listening check of ordinary lines so far: under way.

Known weak spots: a few words of one person attached to the start or end of someone else's line (the
transcription's turn boundaries slip); short interjections ("Second.", "Thank you."); and people who share a
surname (council has had two Hieberts and two Penners — the minutes' initials are used to tell them apart).

## Words

The transcript was compared word by word with YouTube's automatic captions for 88 of these meetings.
They agree on 93.0% of words on average (range 85.6–95.4%),
ignoring differences that don't change meaning ("2"/"two", "centre"/"center"). Where they disagree at least one
is wrong.

Random listening check of the disagreements so far (13 judged, across 2022–2026): the transcript used here
was right in 9, YouTube in 2. Most of the transcript's misses were local names, which is why
meetings from November 2022 on were re-transcribed with a vocabulary of council, staff and street names.

Known weak spots: names of residents, businesses and places that aren't on the vocabulary list; crosstalk; and
quiet speakers far from a microphone. The phrase "Your Worship" was inserted by the transcription service where
nobody said it; it is removed where YouTube's captions heard nothing there.

## Report an error

See [CORRECTIONS.md](CORRECTIONS.md).
