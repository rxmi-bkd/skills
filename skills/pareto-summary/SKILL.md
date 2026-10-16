---
name: pareto-summary
description: Summarizes one or more sources (links, documentation pages, videos, pasted text, local files, PDFs) using the Pareto principle (80/20) - the vital 20% that gives 80% of the value, each point explained with a concrete example.
disable-model-invocation: true
---

# Pareto summary

The user is learning and wants the few ideas that matter most, not a
compressed copy of the source. A summary that keeps everything in
miniature fails that goal, so ranking by value is the whole job. Every
vital point gets a concrete example because an abstract rule is easy to
read and hard to apply.

## 1. Gather the sources

Handle each source in the way that actually reads its content:

- **Links:** use WebFetch. If the result says it covered only part of the
  page, call it again with the suggested `offset` until you have the whole
  thing, or say clearly which part you did not read.
- **Videos:** you cannot watch them. If `yt-dlp` is installed, fetch the
  subtitles or auto-captions (`yt-dlp --skip-download --write-auto-subs
  --sub-langs en --convert-subs srt -o <scratchpad>/%(id)s <url>`) and
  work from the transcript. Otherwise, ask the user to paste the
  transcript or key notes. Never summarize a video from its title alone.
- **Pasted text:** use it directly.
- **Local files and PDFs:** use Read (PDFs need the `pages` parameter when
  long).
- **Several sources:** read all of them before writing anything, so the
  ranking reflects the whole set and not whichever source came first.

If a source fails to load, say so and continue with the rest. A missing
source stated plainly is better than a confident summary with a hidden
gap.

## 2. Find the vital few

Ask of each idea: if the reader only learned this, how much of the topic
would they be able to do or understand? Keep roughly the top 20%, which
is usually 3 to 5 points. The ratio is a rule of thumb, so let the source
decide: a narrow page may have only 2 vital ideas.

With multiple sources, merge overlapping ideas into one point, and when
sources disagree, say so and name which source says what. An idea that
several sources stress is a strong sign it is vital.

## 3. Write the answer

Use this structure, adapting headings to the topic:

```text
## The vital few
**1. <the idea, as a short claim>**
<one or two sentences on why it matters>
<concrete example: code, command, scenario, or numbers>

(repeat for each vital point)

## The useful extras
<short bullets for the next 30%, one line each, no examples needed>

## Gotchas
<traps, caveats, common mistakes>

## Try it
<one small first action the reader can do right now>
```

Add a line at the top or bottom listing the sources used and anything not
read.

## Concrete examples

Make examples specific to the user's context when you know it (their
project, language, tools). A generic example is acceptable only when
nothing about their context is known. The best examples are things the
reader can copy and run, or a real scenario with real numbers, e.g.
"about 20% of bugs cause 80% of crashes, so fix the top three crash
reports first" rather than "focus on what matters".

## Tone and length

Plain language. Define jargon in a few words the first time it appears.
The summary should be clearly shorter than the sources. End by offering
to go deeper on one specific part, naming the part, rather than asking a
generic "anything else?".
