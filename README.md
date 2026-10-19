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
.nomedia
img/.nomedia
img/players/
img/clubs/
```

Do not add an extra folder level around these files when creating the final ZIP.

Only the files listed above belong in the ZIP — see the note on `privacy.html`
at the end of this file.

The two `.nomedia` files are empty markers Android's media scanner reads: a
folder containing one (and its subfolders) is skipped by the gallery. Keep them
in the ZIP you publish, so a player who extracts the pack does not get its
portraits in their photo gallery. The game ignores them on import.

## Encrypt the ZIP before publishing

Password-protect the ZIP you upload with the pack password below (see
`DATASET_TEMPLATE_GUIDE.md` for the 7-Zip / ZArchiver steps). Players who tap
the ZIP in a file manager then get a password prompt instead of an accidental
extraction into their gallery.

```text
rsd-community-pack
```

## ID relationships

- `players.csv:player_id` is referenced by `market.csv:player_id` and `transfers.csv:player_id`.
- `clubs.csv:club_id` is referenced by `transfers.csv:from_team_id` and `transfers.csv:to_team_id`.
- Local player images use `img/players/{player_id}.jpg` or `.png`.
- Local club images use `img/clubs/{club_id}.png`.

See `DATASET_TEMPLATE_GUIDE.md` for the complete field reference and validation checklist.

## Privacy policy (hosted here, not part of the template)

`privacy.html` is the Terms of Service & Privacy Policy for the Retro Soccer
Dealer Android app. It lives here because Google Play requires the policy at a
public URL, and this repository is already public, so it can serve it without
exposing the game's own repository:

<https://mrhumildad.github.io/rsd_dataset/privacy.html>

- **Source of truth:** `docs/LEGAL.md` in the game repo, which ships the same
  page as `public/privacy.html`. Edit it there and copy it over — never the
  other way round.
- **The four icon files** beside it (`favicon.ico`, `favicon-32x32.png`,
  `apple-touch-icon.png`, `android-chrome-192x192.png`) are used by that page
  only. The page references them with relative paths so it renders correctly
  when served from the `/rsd_dataset/` subpath.
- **None of these files belong in `retro-soccer-dealer-dataset-template.zip`.**
  The ZIP carries only the five CSVs and `img/`, per the layout above.
