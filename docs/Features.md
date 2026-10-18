# Features

[← Home](Home.md)

A league switch (LaLiga / Premier League) and four tabs. Light and dark themes follow the device; the choice of tab and club is remembered in the browser.

## Clubs

One club at a time, picked from the menu.

- **Verdict**: a one-line summary of the club's season, plus *What's going well* and *What's worrying*. It is worked out live from the latest table, luck and outlook.
- **Table position and season outlook**: chances of the title, top 4 (Champions League), Europe, mid-table and relegation, from 20,000 simulations of the rest of the season.
- **Luck**: points won minus the points their chances were worth (expected points from match xG). Positive means ahead of the football, negative means unlucky.
- **Next match**: win / draw / loss chances, the **most likely result**, and the **top scores** (club's goals first). Two separate forecasts: who wins, and the exact score.
- **Missing players**: injuries and suspensions with market value (from the snapshot; not refreshed live yet).
- **Squad and value for money**: players, ages, market values; bargains vs priciest relative to playing time; the age–value curve.
- **Season diary**: a short Claude-written take after every match, newest first (4 shown, *Show all* for the rest), with a line chart of luck through the season.

## Matchday

The next round of the selected league (the earliest round with games still to play; a lone postponed game doesn't count), plus the previous round with results.

Each match card shows:

- the **home / draw / away bar** (our model's chances);
- **Result**: the most likely outcome and its chance (e.g. *Barcelona win 55%*, or *Draw 31%*);
- **Top scores**: the three most likely scorelines with their chances;
- **xG**: expected goals for each side;
- **Bookies**: bookmaker chances, margin removed;
- **Value** flag when our chance × the price beats the price by more than 5%;
- after the match, ✓/✗ for whether the model's and the bookmakers' favourite was right.

Below it: the **track record**, i.e. how often model and bookmakers picked the right outcome, and the profit of the value flags. Genuine pre-match forecasts are kept apart from back-filled ones.

## Tables

The live league table with zone colours, and the season outlook for every club.

## Explorer

A Gapminder-style bubble chart of every club, built from `v_club_round` (club × matchday) and `v_club_squad`.

- **Axes (X and Y)**: points per game, win %, goals scored and conceded per game, goal difference, xG for / against / difference per game, expected points per game from xG, luck vs xG, bookies' expected points per game, points above the bookies' expectation, squad value, average age.
- **Bubble size**: same size, squad value or points. **Colour**: league or table zone.
- **League**: LaLiga, Premier League or both together. With both, each league stops at its own latest matchday.
- **Matchday slider and Play**: animate the season round by round.
- **Highlight** chosen clubs.
- **Questions** that set everything in one click: *Who is lucky?*, *Did the bookies see it coming?*, *Attack vs defence*, *Does money buy points?*
