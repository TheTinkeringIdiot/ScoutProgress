# Scout Progress

A single web page that turns a Scoutbook **Pack Recognition Report** into a
den-by-den view of how Cub Scouts are progressing toward rank.

Open `index.html`, drop the report's CSV file on it, and you get:

- **Pack overview**: scouts, adventures earned, loops waiting to be handed
  out, and scouts who have met rank requirements, per den.
- **Den grids**: every scout against every adventure, required adventures
  first, with a required / elective count per scout.
- **Loops to hand out**: adventures that are completed but not yet awarded,
  grouped by adventure, for each den.
- **Download Excel**: one sheet per den.
- **Download PDF**: the whole report as one continuous page, as an image.
- **Print**: landscape, one den per page.

## Privacy

The report is read entirely in your browser. Nothing is uploaded, and the page
makes no network requests. The `.gitignore` in this repository blocks `.csv`,
`.xlsx` and `.pdf` files so that reports containing scouts' names are not
committed by accident.

## Getting the report from Scoutbook

1. Open the Pack Recognition Report in Scoutbook.
2. Set the start date to June 1 of the current scouting year and the end date
   to today.
3. Tick all four "Include" boxes.
4. Set **Sort By** to **All Sorts**. The page reads the "By Den" section.
5. Click **CSV** and drop the downloaded file on the page.

The same steps, with a screenshot, are shown on the page itself.

## How progress is counted

- Only entries dated on or after June 1 of the scouting year count. The year
  is taken from the date in the report's file name; the date can be changed at
  the top of the page.
- A rank needs all of its required adventures plus 2 electives.
- A trailing `%` on a recognition in the report means the loop has been handed
  out. Those cells are blue with a check mark; completed but not yet handed out
  is green.
- An adventure that is not in the built-in list still counts as an elective
  and is marked with `*`.
- Scouts with no den assigned are left out and listed in the notes. Scouts
  with nothing recorded do not appear in the report at all.

## Updating the adventure lists

The required and elective adventures for each rank are in the `DEFS` block near
the top of the script in `index.html`. They were last checked against the per-rank
pages at <https://www.scouting.org/programs/cub-scouts/adventures/> on
2026-11-15. Edit that block when the program changes. Names are matched
ignoring case and punctuation, so small spelling differences between the
website and Scoutbook do not matter.

## Hosting

The page works opened straight from disk. To give den leaders a link, enable
GitHub Pages for this repository (Settings, Pages, deploy from the `main`
branch root).

## Disclaimer

This is an unofficial tool. It is not affiliated with or endorsed by Scouting
America. Scoutbook is a product of Scouting America.

## License

MIT. See `LICENSE`.
