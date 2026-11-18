# Ireland Goods Trade Visualisation

An interactive Tableau dashboard exploring Ireland’s goods imports and exports for **2023–2025**, using CSO table TSA14.

![Ireland goods trade dashboard](Dashboard%20preview_Ireland%20Goods%20Trade.png)

## Explore the dashboard

Download and open [`goods_trade_dashboard_final.twbx`](Visualisation%20implementation/goods_trade_dashboard_final.twbx) in Tableau Desktop or Tableau Reader. The packaged workbook includes its data extract.

The dashboard compares imports and exports across three years, ranks the top 10 named trade partners and product groups, and supports year, trade flow, partner and product selections.

## Project files

- [`Design Document.pdf`](Design%20Document.pdf): design documentation.
- [`Video demonstration.mp4`](Video%20demonstration.mp4): dashboard demonstration (download to watch).
- [`Visualisation implementation/`](Visualisation%20implementation/): packaged Tableau workbook.
- [`Visualisation implementation/data/`](Visualisation%20implementation/data/): original TSA14 JSON, cleaning notebook, prepared dashboard CSV and data coverage CSV.

## Reproduce the data preparation

Use Python 3 with `pandas` and Jupyter Notebook installed:

```sh
python3 -m pip install pandas notebook
python3 -m notebook "Visualisation implementation/data/goods_trade_data_cleaning.ipynb"
```

Run all cells in order. The notebook reads the adjacent `TSA14.json` and writes the prepared CSV files and `processing_manifest.json` to the same data directory. Re-running replaces the prepared CSV files.

## Data and interpretation

Source: [Central Statistics Office Ireland — TSA14](https://data.cso.ie/table/TSA14). The repository contains a saved snapshot; it does not automatically fetch updated data.

Values are converted from thousand euro to billion euro. Missing observations stay missing, and all-missing selections stay blank. Aggregates are sums of available values, rather than verified national totals. Missing observations can affect rankings and comparisons across years. Special partner categories and unclassified product estimates are retained in the data but excluded from named rankings; Great Britain and Northern Ireland remain separate.
