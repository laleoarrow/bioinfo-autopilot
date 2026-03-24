# Cohort / Clinical Epidemiology / Survival QC Gates

- Confirm eligibility criteria, time zero, follow-up window, censoring rules, and exposure/outcome definitions before modeling.
- Track participant counts from raw cohort to final analytic set, including exclusions, missingness, events, censoring, and person-time where applicable.
- Verify coding of exposures, outcomes, confounders, stratification variables, and any time-varying covariates against the study design rather than the spreadsheet defaults.
- Check whether matching, weighting, or adjustment actually achieved the intended balance/contrast when those methods are used.
- Review model assumptions appropriate to the analysis, such as proportional hazards, functional form, positivity, or competing-risk handling.
- Treat immortal time bias, reverse causation, leakage across baseline/follow-up, or drastic event-count collapse as blockers until explained.
