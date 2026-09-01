# Data Skills Beyond Data Jobs

Exploring career opportunities across U.S. states using BLS wage and employment data.

## Background

If someone has data analysis skills, where can those skills lead besides a job title that directly says "data analyst"? This project uses the U.S. Bureau of Labor Statistics' May 2024 State Occupational Employment and Wage Estimates to look beyond the narrow list of traditional data-job titles, toward the broader set of roles — in business, technology, research, operations, purchasing, logistics, and management — where data-related work regularly shows up.

## Data source

[May 2024 State Occupational Employment and Wage Statistics](https://www.bls.gov/oes/current/oessrcst.htm), U.S. Bureau of Labor Statistics (public domain, U.S. government work). The workbook used here (`data/state_M2024_dl.xlsx`) is the "state_M2024_dl" download from that page; it reports employment, wages, job density (`JOBS_1000`), and location quotient (`LOC_QUOTIENT`) by occupation and state.

## Methodology

Occupations are grouped into three tiers by how central data work is to the role:

- **Core Data Jobs** — data work is the main focus (data scientists, database roles, statisticians, operations research analysts).
- **Data-Adjacent Jobs** — data is a major part of decision-making or technical work (systems analysts, information security analysts, management analysts, market research analysts).
- **Data-Applicable Jobs** — data skills are useful in daily work even though the role isn't primarily a data job (operations, logistics, facilities, purchasing, retail supervision, transportation, property management).

Within each tier, the project compares total employment, employment-weighted wages (`A_MEDIAN`, `A_PCT10`), job density, and location quotient across states, then turns those comparisons into practical job-search takeaways: which specific occupations and which states look most worth targeting.

## Limitations

**The three job tiers are a manually curated framework, not a statistical or data-driven classification.** Occupations were assigned to a tier by matching keywords in their BLS titles and then applying my own judgment about how "data-centric" each role is — there's no clustering, scoring model, or validation step that derives the categories from the data itself. Two reasonable people could draw the tier boundaries differently.

Everything built on top of that framework — the employment totals, the employment-weighted wage comparisons, the state rankings, the "balanced" and "hidden opportunity" scores — is real, reproducible quantitative analysis. But it should be read as *analysis conditioned on a subjective starting framework*, not as an objective ranking of "data jobs" in general. Employment-weighted averages of occupation-state wage figures are also an approximation of a true worker-level wage distribution, since BLS reports summary statistics per occupation-state cell rather than individual wage records.

## Key findings

- **Data-Applicable Jobs** account for the largest employment base (~12.6M), far more than Data-Adjacent (~3.0M) or Core Data Jobs (~515K) — the broadest set of openings is in roles where data skills help but aren't the headline requirement.
- **Core Data Jobs** have the highest employment-weighted median wage (~$110K) and the highest weighted 10th-percentile wage (~$65K), so the smaller job base pays a premium at both the median and the entry-level end.
- Washington, DC, Washington state, and California consistently rank at or near the top for wages across all three tiers; California, Texas, New York, and Florida lead on raw job volume.
- Looking beyond the largest states, places like Maryland, Massachusetts, Colorado, and Georgia show up as "hidden opportunity" markets — smaller in raw employment but with an above-average concentration (location quotient) of relevant roles.

See the notebook for the full breakdown by occupation and state.

## Repo structure

```
.
├── bls_data_skills_career_analysis.ipynb   # full analysis
├── data/
│   └── state_M2024_dl.xlsx                 # BLS source data (May 2024)
├── requirements.txt
└── README.md
```

## Running it

```bash
pip install -r requirements.txt
jupyter notebook bls_data_skills_career_analysis.ipynb
```

The notebook reads the data from `data/state_M2024_dl.xlsx` (a relative path), so run it from the repo root.
