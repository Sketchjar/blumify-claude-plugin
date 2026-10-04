---
name: follow-creators
description: Follow YouTube channels, podcasts and speakers on Blumify and catch up on their new episodes. Use when the user wants to follow or unfollow a creator, asks what is new from the shows they follow, or wants a short briefing on recent episodes.
---

# Follow creators on Blumify

Following is free. A follow works for any creator that has public transcripts on Blumify. When the user follows a creator, they also get one email a day at most when that creator has new transcripts.

## Follow and unfollow

- Call `follow_creator` with the creator's name as it appears on their transcripts, for example the YouTube channel or podcast name.
- If the answer says there are no public transcripts from that creator yet, tell the user. A private transcript made with `transcribe_link` does not count. The user can make a free public transcript of one episode at https://blumify.io (paste the link) and then follow.
- Free accounts follow up to 3 creators. When the user reaches the limit, say that Blumify Pro (https://blumify.io/pro) follows as many as they like and also transcribes new episodes of followed YouTube channels by itself.
- `unfollow_creator` stops a follow. `list_following` shows the follows, with how many transcripts each creator has.

## Catch up

1. Call `whats_new`. Without `since`, it covers the last 7 days.
2. For each new transcript, give the title, the creator and a one-line summary.
3. Offer to read any of them in full with `get_transcript`.
4. Keep the `next` value from the answer. Pass it as `since` next time to get only newer transcripts.
