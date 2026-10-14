# Renewable Electricity Trends

This project follows renewable electricity in India, Germany, and Brazil from 2000 through 2024. A Python notebook prepares the source data, compares the annual trends, and presents three charts of renewable share, generation, and source mix. The report explains the findings and the choices behind the analysis.

## Main findings

Germany records the largest increase in renewable share, from 6.22% to 58.64%. Brazil stays highest across the study period and reaches 87.33% in 2024. Renewable output grows in all three countries, showing why generation and percentage share need to be read together.

## Dataset

The project uses the September 10, 2026 release of the [Our World in Data Energy dataset](https://catalog.ourworldindata.org/energy/owid_energy/). The [dated CSV download](https://catalog.ourworldindata.org/garden/energy/2026-09-10/owid_energy/owid_energy.csv) is included as `owid_energy.csv`, with 19,494 rows and 130 columns. The notebook studies 75 country and year records from 2000 through 2024. The file also contains 2025, which falls outside the defined 25 year study period.

## Files

| File | Contents |
| --- | --- |
| `data_workflow.ipynb` | Complete analysis with executed outputs and three charts |
| `module_summary.pdf` | Report with the figures, methods, findings, and references |
| `owid_energy.csv` | Complete source dataset |
| `requirements.txt` | Package versions recorded with pip freeze |

## Run the notebook

Python 3.14 was used, with the final run on Python 3.14.6. Open a terminal in the project folder and create an environment:

```bash
python3.14 -m venv .venv
```

On Windows, create the environment with `py -3.14 -m venv .venv`. Activate it on macOS or Linux with `source .venv/bin/activate`, or on Windows with `.venv\Scripts\activate` in Command Prompt. Then install the recorded packages and start Jupyter:

```bash
python -m pip install -r requirements.txt
jupyter notebook
```

Open `data_workflow.ipynb`, select the environment's Python kernel, and restart the kernel before running all cells from top to bottom. Keep `owid_energy.csv` beside the notebook. The existing outputs can also be read without running the code.

The package file was created with:

```bash
pip freeze > requirements.txt
```

## Reflection

**Where could poor cleaning introduce bias?** Removing years with missing data could favor countries with better reporting. Replacing unknown values with zero or averages could distort the trends. This workflow checks annual coverage and missing values, removes only duplicate records that agree, and stops when records conflict.

**How would a future machine learning workflow change?** Predicting next year's renewable share would require a defined target, additional explanatory data, and training and test periods ordered by time. A forecast that repeats the previous year's share would provide a baseline for judging a model's error. Data preparation would use the training period only to prevent future information from entering training.

**How should the data be prepared for a neural network?** A stronger training dataset would need more countries or more detailed observations and useful explanatory features. Numeric inputs would be scaled from training data, country labels encoded, and missing values handled with a documented method. The time split would stay in place, and the current 75 observations give limited support for a complex model.

**Where could an agent help?** An agent could look for a new dataset release, compare the columns and source notes, flag quality changes, and rerun the notebook. A person would still need to decide whether a new release changes the meaning of a comparison and whether unexpected results make sense.
