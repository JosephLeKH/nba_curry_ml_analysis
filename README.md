# The Curry Effect: Modeling the Ripple of One Player in a 15-Year Dataset

**Author:** Joseph Le   
**Date:** June 2025  

---

## Overview

In 2016, Stephen Curry set the NBA record for most 3-pointers in a season (402) while leading the Golden State Warriors to an all-time best 73-win campaign. Yet Curry’s impact extends beyond points: his presence alters defensive schemes, spacing, and ultimately the Warriors’ probability of winning.  

This project investigates **15 seasons of Golden State Warriors data** to ask a single guiding question:  

> **How much does Steph Curry actually matter to the Warriors’ success?**

Using NBA game logs, play-by-play data, and machine learning models, we quantify Curry’s measurable contribution across contexts, seasons, and simulated scenarios.

---

## Repository Structure

- **`Data_Collection.ipynb`**  
  Collects Warriors game data and Curry box scores via the [`nba_api`](https://github.com/swar/nba_api). Saves season-level datasets for downstream analysis.

- **`Feature_Engineering.ipynb`**  
  Cleans and structures the data into features:  
  - Home vs. Away  
  - Opponent strength (`W/L% >= 0.6`)  
  - Curry’s personal box score stats (PTS, AST, REB, FG%, FT%, 3P%, +/–, etc.)  

- **`Analysis.ipynb`**  
  Core analysis notebook, containing:  
  - Conditional win-rate calculations  
  - Longitudinal trends (by season)  
  - Monte Carlo simulations of “if Curry played every game” seasons  
  - Machine learning models predicting win outcomes from Curry’s stats  

- **`NBA_Curry_ML_Analysis.pdf`**  
  Formal report including visuals (Figures 1–4) and extended discussion.

---

## Methodology

### 1. Conditional Win Rates
- Grouped games by **Curry presence**, **home/away**, and **opponent strength**.  
- Result: The Warriors win **20–30% more often with Curry**, with amplified effects in high-stakes games (home vs. strong teams).  

### 2. Longitudinal Analysis
- Split by season to observe how Curry’s impact evolved.  
- Findings:  
  - Consistent 20–30% boost across most of his career.  
  - Dips during injury years (e.g., 2019 broken hand).  
  - Subtle underestimation in “superteam” years with Kevin Durant.  

### 3. Simulation of Alternate Timelines
- Built a lookup table of conditional win probabilities from games Curry played.  
- Simulated **1,000 alternate seasons** by treating each missed game as a Bernoulli trial with Curry’s conditional win rate.  
- Provided distributions of “expected wins if Curry played every game.”  

### 4. Machine Learning Modeling
- Features: 18 Curry-specific stats + contextual variables (home/away, opponent strength).  
- Model: **Gradient Boosting Classifier** within a `Pipeline` tested with multiple scalers.  
- Validation: **GridSearchCV** (5-fold cross-validation, F1-macro scoring).  
- Results:  
  - Predictions within **1–3% of actual win rates** most seasons.  
  - Undershot slightly in years with additional star talent, confirming Curry alone explains the bulk of team success.  

---

## Results

- **Presence matters:** Warriors win 20–30% more often with Curry, especially against strong opponents.  
- **Seasonal consistency:** Curry’s contribution persists despite roster turnover and injuries.  
- **Simulations confirm value:** In “always-healthy Curry” universes, Warriors gain multiple extra wins per season.  
- **Model validation:** Team outcomes can be predicted surprisingly well using *only Curry’s stats*.  

---

## Significance

This work demonstrates how **probability and data modeling can quantify the ripple effects of one participant in a complex system**.  
While applied here to basketball, similar techniques could be used to measure:  

- A teacher’s influence on classroom outcomes  
- A lead engineer’s effect on product timelines  
- A policy’s impact on public health trajectories  

The broader question: **how do we measure influence?**
