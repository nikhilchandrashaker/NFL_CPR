# Catch Point Rate (CPR)

A quarterback stat that asks: **how much of a QB's passing yardage is ball flight, and how much is the receiver after the catch?**

```
CPR = sum of air yards on completions / sum of passing yards on completions
```

A high CPR means the throw did the work (deep passing). A low CPR means receivers did (check-downs, screens, slants, YAC-heavy schemes). `1 - CPR` is the receiver's share.

## Key findings (2006 to Week 8 of 2026)

- League CPR is **54.5%**, down from 57.8% in 2006 to a low of 51.3% in 2024, as league ADOT fell from 8.5 to 7.7.
- CPR tracks average depth of target (ADOT) closely: **r = 0.77** across 57 QBs (2,000+ career attempts).
- Same-QB season-to-season correlation is **0.46** (374 pairs, 300+ attempts both years): a moderate tendency, not a fixed trait.
- **Highest career CPR:** Jameis Winston (64.4%), Peyton Manning (59.3%), Carson Palmer (59.2%).
- **Lowest career CPR:** Patrick Mahomes (46.1%), Jared Goff (49.1%), Alex Smith (49.2%).
- **Residual** (actual CPR minus what ADOT predicts) isolates YAC dependence beyond throw depth. Most YAC-dependent: Mahomes (-6.0), Rodgers (-3.6). Most air-dependent: Ryan (+4.0), Daniel Jones (+3.4).
- Lowest single season (300+ att): Aaron Rodgers, 2025 (36.2%).

## Files

| File | Contents |
|---|---|
| `catch_point_rate_paper.pdf` | 5-page paper: definition, charts, regression model, league trend, trajectories, limitations |
| `catch_point_rate_slides.pptx` | 7-slide deck summarizing the findings |
| `cpr_qb_career_2006_2026.csv` | Career CPR, ADOT, YAC per completion and residual for 57 QBs |
| `cpr_qb_seasons_2006_2026.csv` | Every QB-season with 200+ attempts |
| `cpr_league_by_season_2006_2026.csv` | League-wide CPR and ADOT by season |

### CSV columns

`att`, `cmp`, `adot` (average depth of target), `pass_yds`, `completed_air_yds`, `yac`, `CPR_pct`, `yac_per_cmp`, `resid` (career file only).

## Method

- **Source:** [nflverse](https://github.com/nflverse/nflverse-data) play-by-play (`pbp` release), regular season only.
- **Plays:** pass attempts excluding sacks and spikes. Yardage figures use completions only.
- **Years:** air yards are not recorded before 2006, so the stat cannot be computed earlier.
- **Model:** ordinary least squares of career CPR on career ADOT. The residual is actual minus fitted CPR, in percentage points.
- **2026** covers 8 weeks only.

## Limitations

- CPR cannot tell a receiver caught in stride from a play designed for YAC.
- It describes how yards were produced, not how good a QB is. A low CPR next to elite results (Mahomes) may mean receivers are earning the YAC.
- Pairing it with Next Gen Stats' YAC over expected would address both gaps. That data was not used here.
- The 2,000-attempt cutoff leaves out many recent QBs.
- Names use nflverse's initial-plus-surname format (for example `P.Mahomes`).

## Data and credit

Play-by-play data from nflverse. Check their data license before redistributing derived data.
