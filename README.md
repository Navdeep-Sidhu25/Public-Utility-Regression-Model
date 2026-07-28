# Public-Company-Utility-Regression-Model

Dummy Variable Regression (H&S Revenue Forecast)

Forecasts monthly revenue for the H&S dataset using OLS regression with seasonal dummy variables and interaction terms. Models are trained on 2011–2013 and evaluated on the unseen 2014 data.

Data

AICPA_regressionAnalysisData.csv — 48 monthly rows, Jan 2011 to Dec 2014.

Column	Meaning
type	dt4training (2011–2013) or dt4testing (2014)
date	Month-end date
revenue	Monthly revenue (target)
production	Units produced (main predictor)
coolDD	Cooling degree days
heatDD	Heating degree days
What the notebook does
Loads the CSV and converts date to datetime.
Builds season dummies: winter_DV (Dec/Jan/Feb) and fall_DV (Sep/Oct/Nov).
Builds interaction terms production × dummy, so production's slope can shift by season instead of just the intercept.
Splits the data into dt4training (2011–2013) and dt4testing (2014).
Fits two models and plots the fitted lines.
Models

Model 1 — revenue on production, winter_DV, winter_interaction

Fitted coefficients (training):

Term	Coefficient
const	5,629,257.08
production	13.51
winter_DV	−201,742.73
winter_interaction	14.16

The plot draws two lines: red = non-winter, blue = winter. Winter has a steeper production slope (13.51 + 14.16 ≈ 27.67), so revenue rises faster with production in winter months.

Model 2 — revenue on production, heatDD, fall_DV, fall_interaction

Adds heating demand and swaps the seasonal effect to fall.

Requirements
numpy
pandas
matplotlib
statsmodels
How to run

Open in Google Colab, upload AICPA_regressionAnalysisData.csv to the session, then run cells top to bottom.
