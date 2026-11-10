# Two Windows, One Throw

**[Live demo](https://shubhzam.github.io/nyuxnfl/)** · **[Notebook](two_windows_one_throw.ipynb)** · built at the NFL Big Data Bowl NYU Edition

[![Two synchronized field replays with receiver timelines](screenshot.png)](https://shubhzam.github.io/nyuxnfl/)

Two wide receivers can each be open for the same amount of time and still give the quarterback very different options. It depends on whether they are open at the same moments or take turns. Using 2021 Next Gen Stats tracking data (Weeks 1–8, 1,788 eligible plays with exactly two WR route runners), we measured **time with receiver space**: in the last second before the throw, how long at least one of the two receivers had the closest defender 2 or more yards away. In two Cover-3 plays where every receiver was in space for 0.6 s, the receivers in ATL vs TB were open at the same moments (0.6 s with someone open), while those in DEN vs LV took turns (the full 1.0 s). Across all plays where both receivers got some space but neither was open the whole second, the windows chained like this half the time, adding 0.19 s on average. A coach can use it to judge whether a route combination spreads its open moments across the quarterback's drop or bunches them together. Limitation: "in space" is distance to the nearest defender only, so it ignores passing lanes, leverage, pressure, and the quarterback's read (in both featured plays the ball went to a tight end).

## Run it

```bash
pip install pandas numpy jupyter
jupyter nbconvert --to notebook --execute two_windows_one_throw.ipynb   # or open it in Jupyter
```

The notebook downloads the [official data](https://github.com/ThompsonJamesBliss/nfl-big-data-bowl-regional-event-data) into `data/` (about 870 MB, first run only), runs the metric sanity checks, screens every play, picks the pair, checks threshold sensitivity (1.5 / 2.0 / 2.5 yd), and writes `index.html` (D3 v7).
