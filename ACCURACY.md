# How accurate are these transcripts?

*Generated from the data in this repository; updated with every release.*

Short version: the words are right about 95 times in 100, council members' and staff names are spelled from the
official roster, and 91% of lines name the speaker with high confidence. Always check an exact
quote against the video (every line links to it).

## Speakers

89 meetings, 10,458 lines:

| Confidence | What it means | Lines |
|---|---|---|
| high | Two or more independent clues agree (e.g. the chair names the person, and the minutes record their motion) | 9,541 (91%) |
| medium | One clear clue, or the only person it could be. Shown as `[medium]` | 603 (6%) |
| low | A best guess. Shown as `Unidentified (possibly …) [low]`, never as a confident name | 314 (3%) |

### Line types

Getting the name right matters most where someone makes a statement or asks a question. Every line has a
`line_type`, set by fixed rules from the words in the line (not by a person, and not always right on long mixed
lines), so you can see where the uncertainty sits:

| Line type | What it means | Lines | high | medium | low |
|---|---|---|---|---|---|
| statement | A statement, question, explanation, presentation or reply | 4,850 (46%) | 95.1% | 3.9% | 1.0% |
| procedure | Running the meeting: moving, seconding, calling the vote, handing over the floor | 3,041 (29%) | 96.7% | 2.7% | 0.7% |
| short | A short reply or courtesy: "Thank you.", "Yes.", "Okay." | 2,567 (25%) | 77.5% | 13.0% | 9.5% |

Most of the uncertainty is on short replies, which are hard to place. Votes, motions and seconders come from the
city's minutes, never from who said "Yes." For anything you quote, use `confidence == "high"` and still check the
video.

**The line type describes the form of a line, not the value of what anyone said.** It is not a measure of any
council member and must not be used to compare people: a "Yes." can be a decisive moment, and the person chairing
speaks mostly in procedure because of the role.

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
