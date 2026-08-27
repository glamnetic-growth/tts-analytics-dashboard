# tts-analytics-dashboard

Internal TikTok Shop performance dashboard for Glamnetic.

**Live dashboard:** https://glamnetic-growth.github.io/tts-analytics-dashboard/

Current period: **July 1 – August 25, 2026**

---

## What's in it

| Section | What it shows |
|---|---|
| Performance Overview | GMV, Orders, AOV, Ad Spend, Ad Revenue, ROAS, LIVE GMV, LIVE GPM |
| Daily GMV & Orders | Day-by-day chart, plus top 5 and lowest 5 days |
| Ads (GMV Max) | Daily spend/revenue/ROAS chart, plus a searchable table of every campaign |
| LIVE Performance | Views, Viewers, Watch Hours, LIVE GMV, and real Show GPM per day |
| Traffic Funnel | GMV, Impressions, Page Views, CTR, GPM by channel (Product Card / Video / LIVE) |
| Top Products | GMV, Items Sold, AOV, Impressions, CTR, GPM — searchable and sortable |
| Top Creators | GMV, Commission, Videos, LIVE Streams, Target vs Open plan — searchable and sortable |

---

## Date filter — important

There's a date filter at the top with presets (Full period, July, August, Last 7/14/30 days).

**It applies to:** Performance Overview, Daily GMV & Orders, Ads, LIVE Performance.

**It does NOT apply to:** Traffic Funnel, Top Products, Top Creators.

Those three come out of Omni as full-period aggregates rather than day-by-day rows, so they always show the complete Jul 1 – Aug 25 window no matter what the filter says. There's a banner at the top of the dashboard and a note under each of those sections saying so, so nobody misreads a filtered view.

---

## Data source

Everything comes from **Omni Analytics** (connected via MCP). No manual TikTok Seller Center exports are needed for the current version.

Topics used:
- TikTok Shop Orders — GMV, orders, AOV
- Marketing Performance — GMV Max spend, revenue, campaign names
- TikTok Shop LIVE Performance — views, viewers, watch time, Show GPM
- TikTok Shop Product Performance — product/SKU GMV, impressions, CTR, traffic funnel
- TikTok Shop Affiliate Creators — creator GMV, commission, videos, LIVE streams, plan type

---

## Known data caveats

These are flagged directly on the dashboard too, but noting them here:

- **Ad revenue for Aug 22–24 shows $0.** This is TikTok's attribution reporting lag, not a real drop.
- **BrandConsideration and Reach campaigns show 0 ROAS.** These are awareness campaigns with no conversion tracking, so that's expected, not underperformance.
- **Some LIVE days show 0 views but non-zero GMV.** View data didn't sync for those sessions; the GMV is still real and counted.

---

## Not currently available

A few things aren't in Omni yet, so they're not on the dashboard:

- Order cancellation reasons (only order status is available)
- Promotion names (only discount totals by order status)
- Creator follower counts and CTR

---

## How to update

1. Ask Claude to pull fresh data from Omni for the new date range
2. Claude returns two files: `index.html` and `data/YYYY-MM-DD.json`
3. Replace `index.html` at the repo root
4. Upload the new JSON into the `data/` folder
5. Commit, then hard-refresh the live link (Cmd+Shift+R) — GitHub Pages caches aggressively, so use an Incognito window if the old version is still showing

---

## Repo structure

```
index.html                  the dashboard itself (single file, no build step)
data/2026-08-25.json        current data snapshot
data/                       older snapshots kept for reference
```

Built as a static site on GitHub Pages. Charts use Chart.js loaded from CDN.
