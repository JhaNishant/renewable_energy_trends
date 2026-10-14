# Renewable Electricity Trends

## Project description

This project compares renewable electricity trends in India, Germany, and Brazil from 2000 through 2024. The workflow loads a public energy dataset, cleans the country and year records, explores the results, and creates three charts. It provides a reusable starting point for later data and machine learning work.

## Project files

The project includes a runnable notebook, a written report, the full source dataset, and a pinned environment file. The analysis uses a focused slice of the full dataset so the results are easy to follow.

## Dataset

Our World in Data Energy dataset, updated September 10, 2026: [dataset catalog](https://catalog.ourworldindata.org/energy/owid_energy/). The included CSV has 19,494 rows and 130 columns, with observations through 2025. This analysis uses 2000 to 2024 and excludes 2025 to keep the comparison period fixed.

## Run the project

1. Install Python 3.11 or newer.
2. From this folder, install the recorded packages with `python -m pip install -r requirements.txt`.
3. Start Jupyter with `jupyter notebook`.
4. Open `data_workflow.ipynb` and run all cells from top to bottom.

The dataset is already included in `data/owid_energy.csv`. The requirements file was created with `pip freeze > requirements.txt` after installing the project packages.

## Reflection

**Where could poor cleaning introduce bias?** Dropping missing country years could overrepresent places with better historical reporting. Filling missing values could invent a trend, while keeping duplicate country year rows could give some years extra weight. This workflow keeps the three named countries, checks duplicate keys, and leaves unavailable values missing.

**How would a future machine learning workflow change?** It would define a prediction question and target first, then create time based training and test periods so later observations do not leak into training. A baseline model, a documented feature pipeline, suitable error measures, and validation across countries or years would be needed before any model claim.

**How should data be prepared for a neural network?** A larger set of aligned country year observations and relevant explanatory variables would be needed. Numeric features would be scaled using training data only, country labels would be encoded, missing values would receive a documented treatment, and the split would preserve time order. This small descriptive dataset alone is not enough to justify a neural network.

**Where could an agent help?** An agent could check for a new source release, compare its schema with the saved version, flag missing values or duplicate keys, and prepare a notebook rerun for review. A person should review changed definitions and unexpected results before interpretation or publication.
