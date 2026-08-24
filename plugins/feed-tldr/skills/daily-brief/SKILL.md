---
name: daily-brief
description: Create a concise, organized briefing from the user's latest FeedTLDR summary. Use when the user asks for a daily brief, feed overview, important updates, key themes, or a quick summary of what their followed accounts discussed.
---

# Daily Brief

1. Call `get_latest_summary`, shown as `feed-tldr:get-latest-summary`, first.
2. Use the saved summary as the source for the briefing.
3. Call `get_feed_posts`, shown as `feed-tldr:get-feed-posts`, only for more detail or evidence.
4. Call `get_tracked_accounts`, shown as `feed-tldr:get-tracked-accounts`, only for coverage or freshness.

Write the briefing in this order:

- **Main developments:** Give up to five short items. Use fewer when the saved summary contains fewer real developments, and never add unsupported items.
- **Why they matter:** Explain the practical meaning of each item.
- **Worth watching:** List unresolved questions or developments to monitor.
- **Sources:** Keep the original links that FeedTLDR provides.

State the generation time near the start. Say that FeedTLDR has not generated a
summary yet only when the tool returns `No FeedTLDR summary exists yet.` If the
tool fails, times out, or is not authorized, say that the summary is unavailable
and give the returned reason. Do not replace missing data with general knowledge.

Keep the response concise unless the user requests a detailed report. Separate
facts from opinions. Do not claim that a source supports a statement unless the
FeedTLDR result includes that source.
