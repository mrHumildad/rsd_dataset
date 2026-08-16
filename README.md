# Retro Soccer Dealer Dataset Template

This directory is the source repository for `retro-soccer-dealer-dataset-template.zip`.

Populate the CSV files, add any original or properly licensed images, and then ZIP the contents of this directory.

## Required files

- `config.csv`
- `players.csv`
- `market.csv`
- `transfers.csv`
- `clubs.csv`

The CSV files currently contain headers only. The template is not importable until it has been populated with valid data.

## Required ZIP layout

The CSV files must be at the ZIP root:

```text
config.csv
players.csv
market.csv
transfers.csv
clubs.csv
img/players/
img/clubs/
```

Do not add an extra folder level around these files when creating the final ZIP.

## ID relationships

- `players.csv:player_id` is referenced by `market.csv:player_id` and `transfers.csv:player_id`.
- `clubs.csv:club_id` is referenced by `transfers.csv:from_team_id` and `transfers.csv:to_team_id`.
- Local player images use `img/players/{player_id}.jpg` or `.png`.
- Local club images use `img/clubs/{club_id}.png`.

See `../DATASET_TEMPLATE_GUIDE.md` for the complete field reference and validation checklist.
