# Blumify for Claude

Transcripts, summaries and chapters of YouTube videos, Apple Podcasts episodes and Spotify episodes, right in Claude.

- **Transcribe a link.** Paste a YouTube, Apple Podcasts or Spotify link and get the transcript with timestamps, the summary, key points and chapters.
- **Ask about it.** Claude answers from the transcript and points to the exact moment, as [mm:ss].
- **Whole playlists.** Get a price first, then transcribe up to 200 videos.
- **Translate the notes** into another language.
- **Follow creators** and catch up on their new episodes with "what's new".

Everything you make is saved in your [Blumify workspace](https://blumify.io/app).

## Install (Claude Code)

```
/plugin marketplace add https://github.com/Sketchjar/blumify-claude-plugin.git
/plugin install blumify@blumify
```

If you use SSH with GitHub, the short form `/plugin marketplace add Sketchjar/blumify-claude-plugin` works too.

Then run `/mcp`, choose **blumify** and sign in in your browser, with an emailed code or Google. A new Blumify account is free and comes with 30 AI credits.

Then try:

- "Summarize https://www.youtube.com/watch?v=ji5_MqicxSo and give me the key moments with times."
- "What does the guest say about pricing in this episode? <Apple Podcasts or Spotify link>"
- "Transcribe this playlist, but tell me the price first: <playlist link>"
- "Follow Lex Fridman and the All-In Podcast. What's new from them this week?"

## What it costs

Reading a transcript that is already public on Blumify is free. New private transcripts, questions on long recordings, translations, speaker labels and playlists use AI credits. Claude tells you before a playlist spends anything. [Blumify Pro](https://blumify.io/pro) is US$29 a month for 3,000 AI credits and starts with a 7-day free trial. One-time top-ups are also available.

## What is inside

| Part | What it does |
| --- | --- |
| `.mcp.json` | Connects Claude to the Blumify MCP server at `https://blumify.io/api/media/v1/mcp`. You sign in with OAuth; there is no API key to paste. |
| `skills/transcripts` | How Claude gets transcripts, follows a job to the end, answers with timestamps, prices playlists before it runs them, and handles running out of credits. |
| `skills/follow-creators` | Follow, unfollow and "what's new" for creators. |

To use the MCP server without this plugin:

```
claude mcp add --transport http blumify https://blumify.io/api/media/v1/mcp
```

## What the plugin sends

The plugin contains no code that runs on your machine: only the two skills (instructions for Claude) and the address of the Blumify MCP server. When Claude uses a Blumify tool, it sends that tool's input to `https://blumify.io` and nowhere else: the link you asked about, your question, a language code, a creator's name, or a job or playlist id. You sign in with OAuth in your browser, so Claude never sees your password or email code. Blumify fetches the video's captions or audio from the platform to make the transcript.

## Privacy and support

- Privacy policy: https://blumify.io/privacy
- Terms: https://blumify.io/terms
- Developer docs: https://blumify.io/developers
- Support: gaurav@blumify.io or https://blumify.io/feedback

## License

MIT
