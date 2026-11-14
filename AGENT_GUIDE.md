# Researching these transcripts with an AI agent

You can point your own AI coding agent at this repository and ask it questions about Steinbach City Council:
what was said about a topic, how a discussion developed over the years, what a council member said on an issue.
This guide explains how to do that and how to keep the answers fair and checkable.

## 1. Get the files

- **With git:** `git clone https://github.com/scottjodoin/Steinbach-City-Council-Transcripts.git`
- **Without git:** on the repository page, press **Code → Download ZIP** and unzip it.

## 2. Open the folder in a coding agent

Any AI agent that can read files and run small scripts on your computer will work, for example Claude Code,
OpenAI Codex, Gemini CLI, Cursor or GitHub Copilot in agent mode. Open the unzipped folder in it, so the agent
can read `transcripts/`, `speaker_maps/` and `meetings.csv`.

## 3. Start with these ground rules

Paste this first, then ask your question (also on the website, with a copy button:
<https://steinbachcitycouncilreporting.ca/ask-your-ai/>):

```text
You are helping me research Steinbach City Council meetings using the transcripts in this folder.
Read README.md, ACCURACY.md and AGENT_GUIDE.md first. Then follow these rules:

1. Be neutral. Report what was said and decided. Don't guess at motives, don't take sides, and when people
   disagreed, give each side's strongest points in their own words.
2. Back every point with specific evidence: the exact quote, the speaker as labelled, the meeting date, and the
   line's video_url so I can watch it.
3. Only say a named person said something when the line's confidence is "high". For "medium", say "probably".
   Never attribute "low" or unidentified lines to anyone.
4. Votes, motions and decisions: check them in the city's minutes (minutes_url in meetings.csv where
   filled in, otherwise steinbach.ca). Transcripts do not record votes reliably.
5. Residents appear as "Resident 1", "Resident 2" and so on. Never try to work out who they are.
6. Say what you could not find or confirm. Not finding something is not proof it was never said: earlier years
   are not in this folder yet, and machine transcription misses some words.
7. Don't use line_type, line counts or speaking time to rank or compare people.
8. Keep quotes and your own summary clearly separate.

My question:
```

## 4. Example questions

- "What has council said about parking requirements for apartments since 2022? Show how the discussion changed."
- "Find every time a public hearing led council to change or defeat an application, with the quotes."
- "What questions did council members ask the RCMP in their reports to council?"
- "List the times council discussed the Main Street bypass and summarize each meeting's discussion."

## 5. The data, for agents and scripts

Each `transcripts/<year>/<id>.json` holds the meeting's details and a `lines` list. Each line has `time`,
`speaker`, `role`, `title`, `confidence`, `human_checked`, `line_type`, `text` and `video_url` (see
[README.md](README.md) for every field). A minimal Python example:

```python
import glob, json

for path in sorted(glob.glob("transcripts/*/*.json")):
    meeting = json.load(open(path, encoding="utf-8"))
    for line in meeting["lines"]:
        if "parking" in line["text"].lower() and line["confidence"] == "high":
            print(meeting["meeting"], line["speaker"], "-", line["text"][:120], line["video_url"])
```

`speaker_maps/` explains who each voice is and why (the evidence behind each name), which helps when an answer
depends on a single attribution.

## 6. Before you share an answer

- Open the video links for the quotes you rely on. The video and the city's minutes are the official record.
- If you find an error in the transcripts, please report it: see [CORRECTIONS.md](CORRECTIONS.md).
