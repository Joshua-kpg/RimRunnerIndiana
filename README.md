# RimRunnerIndiana

Unofficial Indiana HS boys basketball ratings. Not affiliated with IHSAA or MaxPreps.

## Nightly scores

`.github/workflows/nightly-scores.yml` runs `scripts/update_scores.py` at 04:30 and 12:00 UTC
(11:30 pm / 7:00 am Eastern standard time) and on manual dispatch. It reads boys basketball finals
for the last 3 days from the MaxPreps Indiana scores-by-date page, matches them to the schedule by
MaxPreps team id + date, records them in `data/results.json` and bakes scores and W-L records into
`index.html`. The page recomputes Elo from those finals. It commits only when data changed, then
deploys to Cloudflare Pages if the `CLOUDFLARE_API_TOKEN` repository secret is set.
