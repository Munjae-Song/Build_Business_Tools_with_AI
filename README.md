# Build Business Tools with AI

Companion repository for the Medium series **Build Business Tools with AI** — real, working examples of the **3Q + TCREI** method for turning everyday business problems into practical data tools.

Every example runs in **Google Colab**. No local setup, no paid API keys — just a Google account.

## The method

Each tool in this series is built the same way:

- **3Q** — three questions that define the problem *before* any code is written: what exactly is the problem, what approach fits it, and what solution should be built.
- **TCREI** — a structure for asking AI to build the solution: **T**ask, **C**ontext, **R**eferences, **E**valuate, **I**terate.

The point of this repository is not the code itself — it is showing that a well-defined problem plus a well-structured prompt produces a working business tool, even if you are not a developer.

## What's inside

| # | Folder | Tool | Domain |
|---|--------|------|--------|
| 001 | [`001_interactive_dash_board`](001_interactive_dash_board) | Interactive quality dashboard — 21-day inspection trends, Cpk/Ppk process capability, distributions (Gradio + Plotly + SQLite) | Manufacturing / QA |
| 002 | [`002_Collect_price_data`](002_Collect_price_data) | Commodity price collector — pulls WTI crude oil, aluminum, and copper from Yahoo Finance into a SQLite database on Google Drive, with incremental updates and validation | Purchasing / Finance |
| 003 | [`003_commodity_dashboard`](003_commodity_dashboard) | Commodity analysis dashboard — candlestick charts with Bollinger Bands, moving averages, MACD, weekly/monthly views, and AI-generated commentary (uses the database from 002) | Purchasing / Finance |
| 004 | [`004_voice_memo`](004_voice_memo) | Field sales voice memo — record a post-meeting summary, Whisper transcribes it, AI extracts a structured meeting note, then it is saved to Drive and emailed | Sales |
| 005 | [`005_monthly_workbook`](005_monthly_workbook) | Monthly workbook generator — takes a raw transactions Excel file and reproduces the prior month's management workbook format, with aggregation, review flags, and self-validation | Accounting / Operations |
| 006 | [`006_discrepancy_investigator`](006_discrepancy_investigator) | Parts discrepancy investigator — cross-checks six operational CSV files, applies detection and scoring rules, and produces a prioritized investigation queue | Service / Inventory |

Article links will be added here as each installment is published on Medium.

## Folder structure

Each folder follows the same pattern:

```
NNN_tool_name/
├── NNN_tool_name.ipynb   # the Colab notebook (the finished tool)
├── TCREI_prompt.txt      # the actual TCREI prompt used to build it
└── data / *.db           # sample data, when the tool needs it
```

The `TCREI_prompt.txt` file is the interesting part — it is the exact prompt that produced the notebook, so you can compare the request with the result.

## How to run an example

1. Open the folder's `.ipynb` file in [Google Colab](https://colab.research.google.com) (File → Open notebook → GitHub, or download and upload it).
2. Upload the folder's sample data to your Google Drive under `MyDrive/Colab Notebooks/data/` — that is where the notebooks look for it.
3. Run all cells and follow the Gradio link that appears.

Folder-specific notes:

- **001** — the notebook expects `quality_data.db`; rename the included `quality_data_small.db` or adjust `DB_PATH` in the first cell.
- **003** — needs `commodity_prices.db`. Either run 002 first to build it, or upload the sample database included in the folder.
- **004** — sending email requires your own Gmail address and an [app password](https://myaccount.google.com/apppasswords). The notebook contains placeholders; **never commit real credentials.**
- **005** — upload the files in `data/` (prior workbook + raw transactions) to your Drive data folder before running.
- **006** — upload one of the CSV sets in `data/` (`small_*` or `large_*`) plus a `*_list_*.md` file naming the six CSVs, as described in the article.

Some notebooks use `google.colab.ai` for AI analysis — it is built into Colab and needs no API key.

## Sample data

All sample data in this repository is **synthetic** and provided for educational purposes only. It does not represent any real company, process, or market position. The commodity price tools are learning examples, not investment advice.

## License

Code is licensed under [Apache-2.0](LICENSE). Sample data is provided for educational use only.
