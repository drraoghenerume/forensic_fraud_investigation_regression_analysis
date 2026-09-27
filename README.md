# forensic_fraud_investigation_regression_analysis

![Python](https://img.shields.io/badge/Python-3.13-blue)
![License](https://img.shields.io/badge/License-All%20Rights%20Reserved-red)

Conducted in Python, this analysis tested seven hypotheses in three phases: whether AI, Blockchain Technology (BCT), and Big Data Analytics (BDA) are each *related* to the perceived effectiveness of Forensic Fraud Investigation (FFI) (H01–H03, Pearson correlation); whether each *individually predicts* FFI (H04–H06, simple linear regression); and whether the three *jointly predict* FFI (H07, multiple linear regression). All models were validated against classical OLS assumptions. N = 384.

---

## 🎯 Hypotheses Tested

| Phase | Hypotheses | Method | Question |
|---|---|---|---|
| Association | H01–H03 | Pearson correlation | Is each IV related to FFI? |
| Individual prediction | H04–H06 | Simple linear regression | Does each IV predict FFI on its own? |
| Joint prediction | H07 | Multiple linear regression | Do the three IVs jointly predict FFI? |

---

## 📊 Headline Results

**Correlation (H01–H03):** each technology is significantly related to FFI. AI is strongest (r = .623, 95% CI [.557, .680]), then BCT (r = .505, [.426, .576]), then BDA (r = .457, [.374, .533]). All p < .001.

**Individual prediction (H04–H06):** each predicts FFI on its own. AI explains the most variance (R² = .388, F(1, 382) = 241.75), then BCT (R² = .255, F = 130.75), then BDA (R² = .209, F = 101.03). All p < .001.

**Joint prediction (H07):** together the three explain 53.5% of the variance in FFI (R² = .535, Adj. R² = .531, F(3, 380) = 145.78, p < .001), and each retains a significant unique contribution.

**Model:** `FFI = 0.017 + 0.470(AI) + 0.248(BCT) + 0.269(BDA)`

**Decision:** all seven null hypotheses (H01–H07) rejected.

---

## 📈 Methods Used

| Method | Purpose |
|---|---|
| Pearson Correlation (r) | Test strength/direction of each IV ↔ FFI relationship |
| 95% Confidence Intervals (Fisher's z) | Bound the true population correlation |
| Simple Linear Regression | Estimate individual predictor effects on FFI |
| Multiple Linear Regression | Estimate simultaneous, adjusted predictor effects |
| Shapiro–Wilk Test | Assess normality of residuals |
| Breusch–Pagan LM Test | Assess homoscedasticity |
| VIF & Tolerance | Detect multicollinearity |
| Durbin–Watson | Detect residual autocorrelation |
| Cook's Distance/Leverage | Identify influential cases |

---

## 📊 Interpretation Guidelines

| Statistic | Range | Interpretation |
|---|---|---|
| Pearson's r | ±0.70 – ±1.00 | Very high |
| | ±0.50 – ±0.69 | High |
| | ±0.30 – ±0.49 | Moderate |
| | ±0.10 – ±0.29 | Low |
| R² (simple linear regression, 1 predictor) | ≥ .25 | Substantial |
| | .09 – .24 | Moderate |
| | < .09 | Weak |
| R² (multiple linear regression) | ≥ .26 | Substantial |
| | .13 – .25 | Moderate |
| | < .13 | Weak |
| VIF | < 10 | No multicollinearity concern |
| Durbin–Watson | 1.5 – 2.5 | Independence satisfied |
| Shapiro–Wilk | p > .05 | Residuals normal |

---

## 🔬 Key Findings

### Correlation (H01–H03)

| Hypothesis | Relationship | r | 95% CI | p | Strength | Decision |
|---|---|---|---|---|---|---|
| H01 | AI ↔ FFI | .623 | [.557, .680] | < .001 | High | Reject H₀ |
| H02 | BCT ↔ FFI | .505 | [.426, .576] | < .001 | High | Reject H₀ |
| H03 | BDA ↔ FFI | .457 | [.374, .533] | < .001 | Moderate | Reject H₀ |

### Simple Linear Regression (H04–H06)

| Hypothesis | Predictor | B | SE | β | t | p | R² | F | DW | Decision |
|---|---|---|---|---|---|---|---|---|---|---|
| H04 | AI | 0.640 | 0.041 | .623 | 15.55 | < .001 | .388 | 241.75 | 2.00 | Reject H₀ |
| H05 | BCT | 0.501 | 0.044 | .505 | 11.43 | < .001 | .255 | 130.75 | 2.08 | Reject H₀ |
| H06 | BDA | 0.454 | 0.045 | .457 | 10.05 | < .001 | .209 | 101.03 | 1.94 | Reject H₀ |

### Multiple Linear Regression (H07)

| Predictor | B | SE | β | t | p | 95% CI | VIF | Zero-order r |
|---|---|---|---|---|---|---|---|---|
| (Constant) | 0.017 | 0.615 | — | 0.027 | .978 | [−1.193, 1.226] | — | — |
| **AI** | 0.470 | 0.040 | .458 | 11.91 | < .001 | [0.393, 0.548] | 1.21 | .623 |
| **BCT** | 0.248 | 0.039 | .251 | 6.45 | < .001 | [0.173, 0.324] | 1.23 | .505 |
| **BDA** | 0.269 | 0.037 | .271 | 7.32 | < .001 | [0.196, 0.341] | 1.12 | .457 |

**Relative contribution (part correlations):** AI = .417, BDA = .256, BCT = .226.

### Assumption Diagnostics

**Multiple linear regression:** Shapiro–Wilk p = .822; Breusch–Pagan p = .114; max VIF = 1.23; Durbin–Watson = 2.00. All assumptions met.

**Simple linear regressions:** AI and BDA met all assumptions. BCT showed mild residual non-normality (Shapiro–Wilk p = .002), immaterial at N = 384 by the Central Limit Theorem.

**Influential cases:** 2 cases (IDs 17, 370) with |standardised residual| > 3; maximum Cook's Distance = 0.031. No case exerted undue influence.

### Practical Implication

The three technologies are not interchangeable. Each contributes unique predictive power after controlling for the others, and together they explain a substantial share of variance in FFI (R² = .535). Respondents appear to distinguish AI, BCT, and BDA as separate drivers rather than a single digital capability, so collapsing them into one construct would discard information the data preserve.

---

## 🖼️ Diagnostic Plots

Four-panel figure (`regression_diagnostics.png`): Normal Q–Q plot of standardised residuals; residuals vs. fitted; scale-location plot; histogram of residuals with normal curve overlay.

---

## ⚠️ COPYRIGHT NOTICE

**© 2026 Rioborue Alexander Oghenerume. All Rights Reserved.**
***This repository is for viewing purposes only. No part of this work may be copied, reused, modified, reproduced, or redistributed without prior written permission. Unauthorised use will be pursued legally.***

---

**BY ACCESSING THIS REPOSITORY, YOU AGREE TO THESE TERMS!**
