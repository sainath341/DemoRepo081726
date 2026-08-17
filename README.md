## How it works

```
disclosure files          scripts/build_list.py
        │                                  │
        └────────────────►  data/master.csv (every employer, ranked by filings)
                                            │
                                            ▼
                              data/top.csv (>= 5 filings, configurable)
                                            │
                             scripts/discover_ats.py (best-effort match to
                             Greenhouse/Lever job board APIs)
                                            │
                                            ▼
                          data/company_ats_mapping.csv  +  data/unmatched_companies.csv
                                            │
                             scripts/check_jobs.py  ◄── runs DAILY via GitHub Actions
                                            │
                          data/new_postings.csv (today's new matches)
                          + optional Slack notification
