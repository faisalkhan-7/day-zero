# Day Zero

A financial resilience engine for the Tangerine track, Sheridan Datathon 2026.

Type any account number. See how many months they last under any shock,
and the smallest change that would fix it.

**Live: <link>  ·  Demo video: <link>**

## The finding

Tangerine's highest earners are its most fragile customers.
Under a six-month job loss at EI 55%:

| Income quintile | Fail inside 6 months | Months of cover |
|---|---|---|
| Lowest | 4.4% | 8.5 |
| Highest | 70.4% | 1.8 |

A 15.8x risk ratio. Spending tracks income at 0.94 elasticity,
buffer at only 0.28. Bigger machine, same size tank.

## Run it

The app needs nothing installed. Open `app/index.html` in any browser.

To rebuild from the data:

    pip install -r requirements.txt
    # place the 9 track CSVs in data/
    python src/engine.py       # -> outputs/profiles.csv
    python src/verify.py       # -> proves the engine matches hand calculation
    python src/analysis.py     # -> the finding
    python src/validate.py     # -> default check and leakage test
    python src/export_app.py   # -> app/data.json

## Verification

`src/verify.py` recomputes five accounts by hand and tests nine edge cases
of the runway formula. Zero mismatches. Output in `outputs/verification_report.txt`.

We also found and reported leakage in our own result: all 76 loan defaulters
had previously ended a day below zero, and none of the 606 non-defaulters had.
A perfect separation is not a predictor. See `docs/findings.md`.

## Data

Track data is not committed. Download it and place the 9 CSVs in `data/`.

- PKDD'99 Discovery Challenge Financial dataset, CTU Prague Relational Dataset
  Repository: https://relational.fel.cvut.cz/dataset/Financial
- Statistics Canada and Government of Canada sources: see `docs/sources.md`

## Team

Faisal, Arham, Tausif
