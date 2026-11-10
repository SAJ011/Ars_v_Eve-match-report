# Arsenal 2–0 Everton — match report

Data analysis and visualisation of **Arsenal v Everton** (Premier League, 24 October 2026), built in Python from WhoScored event data using [`soccerdata`](https://github.com/probberechts/soccerdata) and [`mplsoccer`](https://mplsoccer.readthedocs.io/).

## What's in this repo

| File | What it is |
|---|---|
| `Arsenal_v_Everton.ipynb` | The working notebook. Downloads the match events and builds each chart step by step, with notes on the methods (shot maps, passing network, pass end zones, chance creation, defensive actions, progressive passes, Zone 14, high turnovers and expected threat). |
| `Match_Report.ipynb` | The finished report. The same analysis rewritten as reusable `draw_...` functions, combined into a one-page 5 × 3 match report with key takeaways. |
| `arsenal_everton.csv` | The match event data (1,502 events) saved from WhoScored, so the report runs without re-scraping. |
| `requirements.txt` | Python packages needed. |

## Key findings

- **Arsenal won 2–0 with both goals from centre-backs** inside the six-yard box: Konsa from a corner (6') and Gabriel with a header from open play (67').
- **Arsenal dominated the chances:** 20 shots to 8 (14 v 5 on target) and 15 key passes to 7.
- **They controlled the ball:** 569 passes to 401 (84.5% v 82.5% completed), and 162 completed passes into the final third v 85.
- **Expected threat (xT): 2.36 v 0.91.** Declan Rice (0.71) and Martin Ødegaard (0.56) created the most threat with their passing; Ødegaard was the hub of the passing network.
- **Arsenal attacked through the middle:** 20 of their 41 progressive passes went through the centre, with 36 passes into Zone 14 and 56 into the half-spaces (Everton: 15 and 22).
- **Everton defended deep:** 125 defensive actions to Arsenal's 94, made much closer to their own goal, and they went long more often (54 long balls v 44) despite having less of the ball.
- **Arsenal pressed high late on:** 5 high turnovers (ball won within 40 m of goal) to Everton's 3, all after the 73rd minute.

## Methods in brief

- **Pitch:** Opta coordinates (0–100 on both axes), each team attacking left → right; Everton is flipped when both teams share a pitch.
- **Progressive pass:** a completed pass (not a corner or throw-in) that ends at least 25% closer to goal than it started, with distances converted to metres (105 × 68 pitch).
- **Passing network:** average positions from completed passes before Arsenal's first substitution; the receiver is taken as the player in the next event.
- **High turnover:** a ball recovery, interception or won tackle within 40 m of the opponent's goal.
- **Expected threat (xT):** a 12 × 8 xT grid ([source](https://github.com/mckayjohns/youtube-videos/blob/main/data/xT_Grid.csv)); each completed pass scores the xT of where it ended minus where it started (negative values set to 0).

## How to run

```bash
pip install -r requirements.txt
jupyter notebook Match_Report.ipynb
```

`Match_Report.ipynb` reads `arsenal_everton.csv` from this folder. To download the data again, run section 1 of `Arsenal_v_Everton.ipynb` (it opens a browser window to scrape WhoScored).
