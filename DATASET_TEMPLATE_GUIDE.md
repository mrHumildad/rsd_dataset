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
club_id,club_name,country_name,club_short_name
```

`club_short_name` is optional: a short club name shown on player cards when the
full name doesn't fit (e.g. `Bayern`). When omitted, the app shortens the full
name automatically and the tooltip always shows the full name.

## Important rules

- Dates use `YYYY-MM-DD`.
- Player IDs and club IDs must be unique.
- Every market and transfer player ID must exist in `players.csv`.
- Every transfer club ID must exist in `clubs.csv`.
- Player positions must begin with `G`, `D`, `M`, or `A`.
- Every player needs a `first_entry` date and market value history.
- Values must be numbers without currency symbols or commas.
- Use original or properly licensed data and images.

## Before you publish: encrypt the ZIP

Packs published in the community subreddit must be password-protected. It is not
DRM (the password is public — it is in this guide), it just stops the accident
that fills a player's phone gallery: tapping an encrypted ZIP in a file manager
and hitting "extract" asks for a password instead of dumping every portrait into
the gallery.

**Password (all published packs):**

```text
rsd-community-pack
```

- **7-Zip (desktop)** — select everything in this folder (the 5 CSVs, `img` and
  `.nomedia`), *Add to archive* → format **zip** → *Enter password*.
- **ZArchiver (Android)** — select the files → **Compress** → format **zip** →
  set the password.

Choose **ZipCrypto** if your tool asks (it is 7-Zip's default). AES-256 works
too, but a big pack installs about three times slower, because AES has to derive
a key for every single file inside it.

Keep the two `.nomedia` files the template ships. They are empty markers Android
reads to skip a folder in the gallery, so even a player who extracts your pack
with the password does not end up with its photos in their gallery. The game
ignores them on import, and unencrypted packs still import too (older packs stay
installable), so encrypting is purely about keeping the community's packs tidy.

The blank template is intentionally not importable until these files contain valid data. See `README.md` for the ZIP layout and publishing notes.
