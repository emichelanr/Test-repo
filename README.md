# Where is Fabio?

Open `index.html` in a browser. This self-contained interactive map has no dependencies or build step and works offline. Alternatively, run `python -m http.server 8000` from this directory.

## Sourced data

The default map now uses published estimates rather than invented sample counts.

- **Fabio estimates:** [Nomix national distribution table](https://www.nomix.it/mappe-dei-nomi-italiani/FABIO), retrieved 11 October 2026. All 20 regional estimates sum to **160,957**, matching the national figure on that page. The reference date and estimation methodology are not stated on the page. These are approximate estimates, not an official register of residents named Fabio. The national table is used consistently; separate regional detail pages may round differently.
- **Resident population:** [ISTAT demographic indicators for 2024](https://www.istat.it/comunicato-stampa/indicatori-demografici-anno-2024/), [statistical workbook](https://www.istat.it/wp-content/uploads/2025/03/Tavole-indicatori-demografici.xlsx), Table 1, `Totale (P)`, at **1 January 2025**. These are provisional figures published in thousands to one decimal place; multiplying by 1,000 yields population figures rounded to 100 residents. Regional rounding means their sum can differ slightly from ISTAT's separately rounded national total.

The two sources cannot be confirmed to use the same reference date or population scope. Regional prevalence is therefore an approximate comparison, not an official same-date statistic. The map displays this limitation prominently. Name estimates have not been independently verified. No newborn-name data is used.

## Measures

- Regional prevalence: estimated Fabios in the region / ISTAT regional resident population × 100.
- National distribution: estimated Fabios in the region / sum of Nomix's regional Fabio estimates × 100.

For example, Lombardia has an estimated 34,446 Fabios and 10,035,500 residents in the population table: about **0.343%** locally and **21.401%** of the estimated nationwide Fabios.

`data/fabio-regions.csv` contains the source figures and their separate reference dates. `data/fabio-sources.json` records provenance and limitations. The same figures are embedded in the HTML so downloads work offline. Source content is subject to its respective terms; Nomix permits copying for personal, noncommercial use and requires authorization for other reproduction: [source terms](https://www.nomix.it/disclaimer.php).

## Bring your own data

“Import real data” accepts a UTF-8 CSV with exactly one row per ISTAT region code 1–20. Required columns: `region_code,fabio_count,population`. Optional `source,as_of` columns must contain consistent metadata across rows. Use a common reference date and population scope. The page offers a blank template. Imported files stay in the browser and are not retained after reload. “Restore sourced data” restores the bundled estimates.

Regional boundaries: [Openpolis geojson-italy](https://github.com/openpolis/geojson-italy/blob/master/geojson/limits_IT_regions.geojson), CC BY 4.0, simplified for display.

## Validation

Browser checks passed for all 20 regions, source-to-region mapping, Lombardia's local and national percentages, national shares summing to 100%, CSV import, incomplete-data rejection, restoring sourced data, and mobile layout. JavaScript syntax validation also passed.
