# Wycliffe Bible (portions)

Wycliffe Bible (c. 1395), surviving portions. Public Domain (eBible.org).

This data uses the native addresses of WYC. The exact bundled books are listed in manifest.json. Text, layout, word tokens, inferred lookup, verified alignments and reviewed evidence use separate book files. Each JSON Lines array uses the column order in manifest.layers. Layout marks retain the edition’s UTF-16 offsets. The text is authoritative for punctuation, spacing and copying.

The initial migration uses the Open Bible Study v0.5.0 corpus (commit 302bb5f92f1e05bf4b96c894f96da77a4cf10845). The input snapshots and manifest checksums identify the available upstream revisions. The inventory lists additional source investigations. Coverage counts verified spans separately from inferred lookup and records verses without restoration data. The inference inputs are the KJV and BSB token layers and openscriptures/strongs lexicon at the migration revision. Verify new occurrence links against the named source row. Keep unconfirmed English matches out of restoration.

## Regeneration and review

Clone [Open Bible Study](https://github.com/mando222/bibleStudy) recursively, install its npm dependencies and run the following from the app checkout. To reproduce the initial book files, use the v0.5.0 database generated with the app at the migration commit and its checksum-pinned text snapshots.

```sh
node --experimental-sqlite --import tsx data-pipeline/editionPacks.ts export /path/to/v0.5.0/bible.sqlite wyc
node --experimental-sqlite --import tsx data-pipeline/editionPacks.ts seal wyc
node --experimental-sqlite --import tsx data-pipeline/editionPacks.ts validate wyc
npm run db:build
```

After manual corrections, run seal and validate, inspect the coverage and book-level diff, and propose a pinned submodule update in the app. Reviewed evidence uses UTF-16 offsets into the exact published verse. Published tags support dictionary lookup. Only corroborated evidence with a checked original token can add a restoration link.
