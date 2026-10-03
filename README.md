# QC Automation Toolkit

A small Python toolkit that automates data-quality checks (schema, missing values,
duplicates, value ranges, IQR outliers) and produces a JSON QC report. Built to
reduce manual data/test verification and to run automatically in CI.

## Run

    pip install -r requirements.txt
    python -m qc_toolkit.cli data/sample.csv --report qc_report.json

Exit code is 0 on PASS and 1 on FAIL, so it can gate a pipeline.

## Test

    pytest -v

## CI

`.github/workflows/ci.yml` runs the test suite on Python 3.10 and 3.12 for every push
and pull request, runs the checks on the sample data, and uploads the QC report as a
build artifact.

## Structure

    qc_toolkit/validators.py   reusable check functions
    qc_toolkit/report.py       report builder / writer
    qc_toolkit/cli.py          command-line entry point
    tests/                     pytest suite
