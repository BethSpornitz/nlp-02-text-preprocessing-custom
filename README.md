# NLP 02 - Job Description Text Preprocessing

[![Python 3.14](https://img.shields.io/badge/python-3.14%2B-blue?logo=python)](pyproject.toml)
[![CI](https://github.com/BethSpornitz/nlp-02-text-preprocessing-custom/actions/workflows/ci-python-zensical.yml/badge.svg)](https://github.com/BethSpornitz/nlp-02-text-preprocessing-custom/actions/workflows/ci-python-zensical.yml)
[![Documentation](https://img.shields.io/badge/docs-site-blue?logo=github)](https://bethspornitz.github.io/nlp-02-text-preprocessing-custom/)

[![uv managed](https://img.shields.io/badge/uv-managed-DE5FE9)](https://docs.astral.sh/uv/)
[![ty type checked](https://img.shields.io/badge/ty-type_checked-2F80ED)](https://docs.astral.sh/ty/)
[![Zensical docs](https://img.shields.io/badge/Zensical-docs-purple)](https://zensical.org/)
[![MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](LICENSE)

> Analyze data analysis job descriptions using Python text preprocessing to identify commonly requested skills and qualifications.

## Project Overview

Author: Beth Spornitz

Date: 2026 October

Second project in the Web Mining and Applied NLP course.

The project applies text preprocessing techniques to job descriptions for Data Analyst, Business Analyst, and Data Governance positions.

The goal is to identify frequently requested skills and qualifications while exploring how cleaning decisions affect the results.

The project is configured in
[pyproject.toml](pyproject.toml).


## Data

The project uses two datasets:

- `data/text_data.txt` — The original example dataset containing five short text records.
- `data/job_descriptions.csv` — A custom dataset containing 12 paraphrased job posting summaries, with four each from Data Analyst, Business Analyst, and Data Governance positions.

Each job description record includes the role, job title, employer, source URL, and summarized description.

The custom dataset was used to compare frequently occurring terminology across three data related career paths.


## Approach

This project applies Python text preprocessing techniques to both the original example dataset and a custom dataset of job descriptions.

The analysis includes:

- Reading text data from local CSV and TXT files.
- Tokenizing text into individual words.
- Converting text to lowercase.
- Removing punctuation and special characters.
- Filtering common stop words.
- Calculating word frequencies.
- Comparing frequently occurring terms across job categories.
- Visualizing results using Matplotlib.

First, I modified the original preprocessing script by adding `text` and `language` to the stop-word list. This reduced the number of cleaned tokens from 46 to 38.

I then created a custom Jupyter notebook to compare word frequencies across Data Analyst, Business Analyst, and Data Governance job descriptions. Short technical terms such as AI and BI were retained during preprocessing.  I verified that AI appeared once in the Business Analysts descriptions and BI appeared once in the Business Analyst descriptions, however, those terms do not appear in my charts because they are not in the top 5.

### Project Components

Explore these important project components:

- [pyproject.toml](pyproject.toml) - Project identity, dependencies, and tool configuration.
- [data/](data/) - Input text data, including job descriptions.
- [src/nlp/text_preprocessing.py](src/nlp/text_preprocessing.py) - Executable Python preprocessing analysis.
- [notebooks/text_preprocessing.ipynb](notebooks/text_preprocessing.ipynb) - Interactive Jupyter notebook example.
- [tests/](tests/) - Automated tests.
- [.github/workflows/](.github/workflows/) - Automated testing and documentation deployment.
- [docs/](docs/) - Project documentation.
- [zensical.toml](zensical.toml) - Documentation configuration.
- [notebooks/text_preprocessing_modification.ipynb](notebooks/text_preprocessing_modification.ipynb) - Comparison of original and modified stop-word filtering.
- [notebooks/job_description_analysis.ipynb](notebooks/job_description_analysis.ipynb) - Custom job-description analysis and visualizations.

## Run the Project

Follow the [Professional Python Workflow Guide](https://denisecase.github.io/pro-analytics-02/)
to set up your machine and project environment.

From a VS Code terminal in the project root:

```shell
uv run python -m nlp.text_preprocessing
```

**Close each visualization window** after viewing
so the script can continue executing.

The Jupyter notebook provides an additional
interactive version of the analysis.

## Results

### Original Preprocessing Modification

The original example produced 46 cleaned tokens. After adding two additional stop words, the count decreased to 38, a reduction of approximately 17.4%.

### Job Description Analysis

The custom analysis produced the following results:

| Job Category | Cleaned Tokens | Five Most Frequent Terms |
|---|---:|---|
| Business Analyst | 85 | business, requirements, user, document, collaborate |
| Data Analyst | 92 | data, develop, dashboards, sql, power |
| Data Governance | 88 | data, governance, metadata, quality, support |

The results show differences in terminology across the three career paths.

### Custom Visualization

![Most frequent terms across three job categories](docs/images/job_description_comparison.png)

### Project Notebooks

- [Text Preprocessing Modification](notebooks/text_preprocessing_modification.ipynb)
- [Job Description Analysis](notebooks/job_description_analysis.ipynb)


### Original Script Execution

The modified Python preprocessing script generates token counts,
frequency summaries, and visualizations.

Successful execution displays:

```text
========================
Pipeline executed successfully!
========================
```

The script also creates a `project.log` file containing execution
details.


## Verification

Run the automated tests:

```shell
uv run python -m pytest
```

## Project Documentation

The [hosted documentation site](https://bethspornitz.github.io/nlp-02-text-preprocessing-custom/)
is published using Zensical and GitHub Pages.

The documentation site is used to present the project report,
covering such sections as data, methods, results, visualizations,
interpretation, and conclusions.

## CI/CD and GitHub Actions

This project includes continuous integration and continuous deployment (CI/CD)
to check project files and publish the docs.

GitHub Actions include:

- [CI: Python and Documentation Checks](https://github.com/BethSpornitz/nlp-02-text-preprocessing-custom/actions/workflows/ci-python-zensical.yml)
- [CD: Documentation Deployment](https://github.com/BethSpornitz/nlp-02-text-preprocessing-custom/actions/workflows/deploy-zensical.yml)

## Developer Reference

Follow the
[Professional Python Workflow Guide](https://denisecase.github.io/pro-analytics-02/)
for **detailed instructions and troubleshooting**.

### Initialize and Update the Python Environment

With the project open in VS Code, open a VS Code terminal.
Paste each command and hit Enter or Return after to run it.

```shell
uvx pup-clean --delete
uv self update
uv python pin 3.14
uv python install
uv lock --upgrade
uv sync
uv audit
```

### Set Up and Run Git Hooks

Set up and run the git hooks to perform
basic checks automatically before
any changes get pushed to GitHub.

In the VS Code terminal,
paste each command and hit Enter or Return after to run it.

```shell
uvx prek install --force
uvx prek update --freeze --cooldown-days 7

git add -A
uvx prek run --all-files
# repeat if changes were made
uvx prek run --all-files
```

### Run Common Chores

Run linters, formatters, type checks, tests, and
build the documentation.

```shell
uv run ruff check . --fix
uv run ruff format .

uv run ty check
uv run python -m pytest
uv run python -m zensical build
```

### Git add-commit-push to GitHub

After making useful changes, save your work to GitHub.

```shell
git add -A
git commit -m "describe your changes in quotes"
git push -u origin main
```

## Developer Notes

- Use the **UP ARROW** and **DOWN ARROW** in the terminal to scroll through past commands.
- Use `CTRL+f` to find (and replace) text within a file.

## Developer Tools

This project uses professional Python tools to support development,
testing, documentation, and code quality.

- [uv](https://docs.astral.sh/uv/) - Python environments and dependencies.
- [Ruff](https://docs.astral.sh/ruff/) - Python linting and formatting, configured in [.ruff.toml](.ruff.toml).
- [ty](https://docs.astral.sh/ty/) - Python type checking.
- [pytest](https://docs.pytest.org/) - automated Python testing, configured in [.pytest.toml](.pytest.toml).
- [prek](https://prek.j178.dev/) - Git hooks and automated checks, configured in [prek.toml](prek.toml).
- [Zensical](https://zensical.org/) - project documentation, configured in [zensical.toml](zensical.toml).

## Links

- [Hosted Documentation](https://bethspornitz.github.io/nlp-02-text-preprocessing-custom/)
- [Professional Python Workflow Guide](https://denisecase.github.io/pro-analytics-02/)
- [Citation](CITATION.cff)
- [License](LICENSE)
- [Original Example Project](https://github.com/denisecase/nlp-02-text-preprocessing)
- [Custom Job Description Dataset](data/job_descriptions.csv)
