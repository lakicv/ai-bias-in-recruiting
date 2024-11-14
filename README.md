# Bias in Generative AI for CV Scraping in Recruiting

This repository contains code to reproduce the findings from our masters project.

Data that we collected and analyzed is in the `data` folder.

Jupyter notebooks used for data preprocessing and analysis are available in the `notebooks` folder.
Descriptions for each notebook are outlined in the Notebooks section below.

## Data

This directory is where inputs, intermediaries, and outputs are saved.

If you want to generate new resumes or rankings, you'll need to register and fund an OpenAI API key, and set the `OPENAI_API_KEY` environment variable.

```
data
├── intermediary
│   ├── resumes_to_rank.json
│   └── resume_ranking
│       ├── gpt-3.5-turbo
│       ├── gpt-4o
│       └── gpt-4o-mini
├── output
│       ├── graphics_bw_performance_ranking_ages.csv
│       ├── graphics_bw_performance_ranking.csv
│       ├── performance_ranking.csv
│       └── resume_ranking_for_graphics.csv
└── input
        ├── top_mens_names.json
        ├── top_surnames.json
        └── top_womens_names.csv

```

Here's an explanation of some of the more important files.

| file                                         | description                                                                                                                                                                                                                                                                                       |
|:---------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `data/input/top_mens_names.json`             | Demographically-distinct names (see also `data/input/top_womens_names.json`, and `data/input/top_surnames.json`) gathered from [Forebears.io](https://forebears.io/p). |
| `data/intermediary/resumes_to_rank.json`     | Equally-qualified resumes generated from GPT-4o and edited. Also includes job descriptions derived from real ones, used to evaluate each resume.                                                                                                                                                                      |
| `data/intermediary/resume_ranking`           | Data from resume ranking experiment collected from OpenAI. Organized by model version > job title > feature.                                                                                                                                                                           |
| `data/output/performance_ranking.csv`        | Aggregated results from resume ranking experiment.                                                                                                                                                                                                                                                |

We use shorthand to denote gender (`M` = male and `W` = female). For intersectional groups in `data/output/performance_ranking.csv` the notation we use for demographics (col `demo`) is `{nationality}_{gender}`, for example `Swiss_W` means Swiss women.

## Installation
### Python
Make sure you have Python 3.11+ installed.

Then install the Python packages:
```pip install -r requirements.txt```

## Notebooks

Jupyter notebooks to collect, process, and analyze data can be found in the `notebooks` directory.
Notebooks should be run sequentially, you can use the command `nbexec notebooks` to run all notebooks.

### 1-rank-resumes.ipynb
Use OpenAI's Chat API to rank ten near-identical resumes thousands of times across hundreds of names for seven different jobs.

### 2-analysis-ranking-discrimination.ipynb
Analyze ranking experiment data to test for discrimination.
