# Support Ticket Analyzer

A command-line tool written in Python that turns a customer support ticket export (CSV) into a KPI report: **AHT, FCR, CSAT and SLA compliance**, broken down by channel and category.

I built it from my experience in remote customer service (EU261, refunds, SLA/CSAT/FCR/AHT tracking), where these metrics drive daily decisions.

## Features

- Reads and validates CSV files (clear errors for missing columns or invalid values)
- Calculates the four core support KPIs, overall and per channel/category
- SLA targets by priority (high 15 min, medium 60 min, low 240 min)
- Outputs a Markdown report to the terminal or to a file
- Unit tests with `pytest`
- No external dependencies to run (standard library only)

## Quick start

```bash
git clone https://github.com/<your-username>/support-ticket-analyzer.git
cd support-ticket-analyzer

python generate_sample_data.py          # creates data/sample_tickets.csv
python -m ticket_analyzer data/sample_tickets.csv
python -m ticket_analyzer data/sample_tickets.csv -o report.md
```

## CSV format

| Column | Example | Notes |
|---|---|---|
| ticket_id | T0001 | |
| channel | email / chat / phone | |
| category | refund | |
| priority | high / medium / low | |
| first_response_minutes | 12.5 | |
| handle_minutes | 8 | |
| resolved_first_contact | yes / no | |
| csat | 4 | 1-5, empty if no survey answer |

## Run the tests

```bash
pip install -r requirements.txt
pytest
```

## Project structure

```
ticket_analyzer/
  loader.py    # CSV reading and validation
  metrics.py   # KPI calculations
  report.py    # Markdown report
  cli.py       # command-line interface
tests/         # pytest unit tests
data/          # sample data
```

## Possible next steps

- Charts with `matplotlib`
- Date-based trends (weekly/monthly)
- Export to Excel
- Simple web dashboard (Streamlit)

## License

MIT
