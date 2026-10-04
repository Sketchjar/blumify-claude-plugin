---
name: transcripts
description: Get the transcript, summary, key points or chapters of a YouTube video, Apple Podcasts episode or Spotify episode with the Blumify tools, and answer questions about it. Use when the user shares such a link, asks what a video or podcast says, wants quotes, notes or timestamps from one, or wants a YouTube playlist transcribed.
---

# Blumify transcripts

The `blumify` MCP server acts for the user's Blumify account. Each tool description says when the tool costs AI credits. A new free account gets 30 AI credits.

## When the tools are missing or ask for sign-in

Tell the user to connect Blumify once: run `/mcp`, choose **blumify** and sign in in the browser (an emailed code or Google). The account is free.

## Get a transcript

1. Call `get_transcript` with the `url`. This is free when the transcript is public on Blumify or already in the user's workspace.
2. If the result has `found: false`, call `transcribe_link` with the `url`. This makes a private transcript in the user's workspace and costs AI credits. A public transcript that already exists is saved for free. Set `speakers: true` only when the user asks who said what, because labels cost extra.
3. Call `get_job` with the `jobId` every 15 seconds or so until the state is `succeeded`. Videos with captions usually take under a minute. Audio takes about a minute per 15 minutes of recording.
4. Call `get_transcript` with the `key` from the job.
5. If a job fails, give the user its message. Failed work costs nothing.

## Answer from the transcript

- Answer most questions yourself from the `get_transcript` result. Quote the speaker's words and give times as [mm:ss].
- If the result has `truncated: true` (a long recording), use `ask` for questions about the whole recording. `ask` works on private transcripts in the workspace and costs a few credits per started hour of the recording.
- `translate_notes` gives the title, summary, key points and chapters in another language. The first translation costs credits; after that it is stored and free.

## Playlists

Call `quote_playlist` first and tell the user the quote: how many videos are free, how many are new, and the most it can cost. Call `confirm_playlist` only after the user agrees. Follow it with `get_batch`.

## Credits

- `get_usage` shows the credits available and the plan.
- When a tool says there are not enough credits, do not try the call again. Tell the user, and give both choices at https://blumify.io/pro: Blumify Pro (US$29 a month for 3,000 AI credits, with a 7-day free trial) or a one-time top-up.
