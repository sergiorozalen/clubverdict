# How the site gets its data

[← Home](Home.md)

## Two sources, one page

1. **Embedded snapshot.** `index.html` carries a JSON block (`<script id="data">`) with a full snapshot: clubs, squads, values, absences, verdicts. It is generated on the Mac by `site/update_site.py` from the DuckDB warehouse. The page always works from it, even offline.
2. **Live layer.** On load, the page queries Supabase directly (PostgREST over HTTPS) with the **publishable key**, which is read-only by design. Live data replaces the snapshot wherever it exists. If Supabase can't be reached, the page says *"Live data unavailable, showing snapshot"* and carries on.

The page never has write access. Writes happen only in the pipeline, with the secret key.

## What each tab reads

| Tab | Database objects |
|---|---|
| Clubs | `v_league_table`, `v_current_squad`, `zone_forecast` + `forecast_run` (outlook), `v_club_round` (luck, verdict), `match_forecast` (next match), `match_commentary` (Season diary) |
| Matchday | `match_forecast` with `match` + `match_result` embedded, `forecast_run`, `v_track_record` |
| Tables | `v_league_table`, latest `zone_forecast` |
| Explorer | `v_club_round` (club × matchday), `v_club_squad` |

Requests are paged 1,000 rows at a time (`Range` header). Plotly.js for the Explorer is loaded only when that tab opens, from jsDelivr with unpkg and cdn.plot.ly as fallbacks.

## Freshness

The pipeline runs every day at 06:17 UTC. The site shows whatever is in the database when the page loads; reload to pick up a new run. Matchday forecasts are rewritten each morning until kick-off.
