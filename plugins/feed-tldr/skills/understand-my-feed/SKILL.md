---
name: understand-my-feed
description: Explain what data FeedTLDR used for the latest summary, how accounts were represented, which prompt and model were used, and what the coverage limits are. Use when the user asks how their summary was made, what data FeedTLDR has, whether an account dominated, or what may be missing.
---

# Understand My Feed

1. Call `get_summary_details`, shown as `feed-tldr:get-summary-details`, with `include_post_urls` set to `false` first.
2. Use only the saved details for claims about how this summary was made.
3. Call `get_tracked_accounts`, shown as `feed-tldr:get-tracked-accounts`, only when the user also asks about current scrape freshness.
4. Call `get_summary_details` again with `include_post_urls` set to `true` only when the user asks to inspect or verify the exact source posts.
5. Do not use current raw posts to guess what an older summary contained.

Write the explanation in this order:

- **Data used:** Name the source, post count, covered period, and post cap.
- **Account representation:** Show each account's share of input posts. Explain that this is posting volume, not a separate FeedTLDR ranking weight.
- **Summary settings:** Show the saved prompt and model in a compact form.
- **What may be missing:** Explain source, time-period, access, and cap limits.
- **Source posts:** Keep the exact X post links when the user asks to inspect or verify the input.

Use plain English and keep the first answer concise. Say clearly that FeedTLDR
currently uses X data only. Reddit and other sources are not included yet.
Separate facts saved by FeedTLDR from general limitations.

If provenance is unavailable, repeat the saved explanation from the tool. Say
that the summary may predate provenance tracking, or recommend generating a new
summary, only when the tool says so. Do not invent the missing prompt, account
shares, period, model, or post links.
