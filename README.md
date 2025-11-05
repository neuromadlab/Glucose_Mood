<h2>Script: glmo_LME</h2>

This repository contains the R Markdown workflow used to run the core mixed-effects and mediation analyses for the Glucose ↔ Metabolic State ↔ Mood project, as well as to export tables/figures for the manuscript.

The following script computes the linear mixed-effects model for the manuscript: Glucose levels are associated with mood, but the association is mediated by ratings of metabolic state.
What the notebook does

1. Loads and cleans study data (glucose, metabolic state ratings, mood facets).
2. Creates standardized variables (grand-mean centered).
3. Runs mixed-effects models (lmerTest::lmer) for:
    ◦	Mood ~ Glucose
  
    ◦	MetState ~ Glucose
  	
    ◦	Mood ~ MetState

  	◦	Mood ~ MetState × Glucose (interaction)

  	◦	additional models (Happy ~ Glucose, Sad ~  glucose, Hunger -Mood, Satiety)

  	◦	Covariate adjustments (residualized log-HOMA, BMI, Sex, Age)

  	◦	meand/sd mood ~ Interoceptive Accuracy
   
5. Mediation analysis using mediation::mediate (experimental with lmer objects).
6. Computes person-level “interoceptive accuracy” slope (MetState → Glucose) and tests its associations with mood level/variability and covariates.
7. Exports publication-ready tables to Excel.

