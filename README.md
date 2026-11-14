# Salary Compass — Software Developer Salary Prediction

A Streamlit app for exploring developer compensation and generating survey-based salary estimates. The app uses the Stack Overflow Developer Survey 2025 rather than treating the original three-input model as if it understood additional fields.

## Features

- **Predict:** Estimate annual USD compensation using country, education, professional experience, primary developer role, company size, work arrangement, industry, employment type, and selected programming languages/technologies.
- **Compare:** Compare three profile scenarios side by side while holding shared education, employer, industry, employment type and technologies constant.
- **Explore data:** Filter 2025 survey results by country and review salary distribution, experience bands, and role medians.
- **Career insights:** Explore salary associations by role, location, education and experience, plus model-wide feature-importance signals.
- **About & help:** Review data coverage, interpretation, validation metrics and limitations.

Estimates are trained using survey respondents with annual converted compensation between $10,000 and $300,000 who reported being employed or independent contractors/self-employed. The app shows a point estimate and an indicative 80% interval calibrated on held-out survey responses; neither is a guarantee or personalized compensation advice.

## Run locally

Python 3.10 or newer is recommended.

```bash
python -m venv .venv
# macOS / Linux
source .venv/bin/activate
# Windows PowerShell: .venv\\Scripts\\Activate.ps1
pip install -r requirements.txt
python train_model.py
streamlit run app.py
```

`train_model.py` reads `survey25_results.csv` (or `survey25_results.csv.gz`) and writes `salary_model.pkl` and `model_metrics.json`. The app needs the 2025 survey CSV alongside the source files for the Explore Data and Career Insights tabs. The provided archive includes the compressed survey source and a trained model, so retraining is optional unless you change the training data or code.

## Data and model notes

The model predicts the survey's yearly converted compensation in nominal USD. It uses survey fields for country, education, work experience, developer role, company size, remote/hybrid arrangement, industry, employment type and programming languages. Missing training values are imputed; infrequent categorical values are grouped by the encoder. Very high or low compensation outliers are excluded from training.

Survey responses are self-reported and may be affected by selection, reporting and geographic coverage bias. Associations shown by the app are descriptive, not causal. Pay also depends on factors not included here, including employer policy, seniority, local market conditions, bonuses, benefits and negotiation.

## Project files

The original notebook and assets are retained for reference. The active app is `app.py`; common survey cleaning is in `salary_data.py`; model inference is in `salary_model.py`; retraining is in `train_model.py`.
"# Developer-Salary-Compass" 
