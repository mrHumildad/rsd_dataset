# Dataset Template Guide

Populate all five CSV files before importing this dataset:

```text
config.csv
players.csv
market.csv
transfers.csv
clubs.csv
```

The files must remain at the ZIP root. Do not ZIP an extra parent folder around them.

## Populate in this order

1. `config.csv` — one valid row defining the dataset name and date range.
2. `clubs.csv` — one row per club with stable `club_id` values.
3. `players.csv` — one row per player with stable `player_id` values.
4. `market.csv` — value history using IDs from `players.csv`.
5. `transfers.csv` — transfer history using IDs from both `players.csv` and `clubs.csv`.
6. Optional images — use `img/players/{player_id}.jpg|jpeg|png` and `img/clubs/{club_id}.png`.

## Required headers

### config.csv

```csv
db_name,updated,year,month,endYear,endMonth,description,unlock5,unlock10,unlockFULL
```

### players.csv

```csv
player_id,player_name,player_image_url,date_of_birth,place_of_birth,country_of_birth,citizenship,position,date_of_death,max_value,market_entries,first_entry,last_entry,days_span,years_span
```

### market.csv

```csv
player_id,date,value
```

### transfers.csv

```csv
player_id,date,from_team_id,from_team_name,to_team_id,to_team_name
```

### clubs.csv

```csv
club_id,club_name,country_name
```

## Important rules

- Dates use `YYYY-MM-DD`.
- Player IDs and club IDs must be unique.
- Every market and transfer player ID must exist in `players.csv`.
- Every transfer club ID must exist in `clubs.csv`.
- Player positions must begin with `G`, `D`, `M`, or `A`.
- Every player needs a `first_entry` date and market value history.
- Values must be numbers without currency symbols or commas.
- Use original or properly licensed data and images.

The blank template is intentionally not importable until these files contain valid data. See the repository-level `DATASET_TEMPLATE_GUIDE.md` and `DATASET_SPEC.md` for full details.
