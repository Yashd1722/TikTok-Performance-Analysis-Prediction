## Yashkumar Dhameliya
## Performance Analysis & Prediction

## Overview

This project analyzes TikTok creators in the Tech Reviews niche to identify rising stars by engineering engagement and viral potential metrics, building a regression model, and generating actionable recommendations.

## For Virtual Environment
python3 -m venv .venv   
source .venv/bin/activate
pip install -r requirements.txt

## For XGBoost in Macos
brew install libomp


## Project Structure

- **Prepare_data.ipynb:**  
  Loads and cleans the raw CSV files (`creator_profiles.csv`, `creator_videos.csv`), handles missing data, and ensures proper types for analysis.
- **analysis.ipynb:**  
  Performs feature engineering, computes key metrics (e.g., comment-to-like ratio, hook retention rate, content diversity score), aggregates to creator level, and saves `creator_metrics.csv`.
- **Model.ipynb:**  
  Trains a regression model (XGBoost), predicts comment-to-like ratio for new videos, interprets results using feature importance and SHAP values, and produces insights and recommendations.
- **insight.md:**  
  Summarizes findings, provides interpretability plots, and offers a recommendation for improving engagement.
- **requirements.txt:**  
  Lists required Python libraries.

## Methodology

### 1. Data Preparation
- Loaded `creator_profiles.csv` and `creator_videos.csv`.
- Cleaned data by removing or imputing missing values, ensuring correct types, and dropping irrelevant columns.

### 2. Feature Engineering
- Calculated:
  - **Engagement Depth:** `comment_to_like_ratio = comment_count / like_count` (per video, then averaged per creator)
  - **Viral Potential:** 
    - `hook_retention_rate = like_count / view_count`
    - `content_diversity_score` = number of distinct topics/themes per creator
- Aggregated all metrics to the creator level and saved as `creator_metrics.csv`.

### 3. Modeling & Interpretation
- Trained an XGBoost regressor using features like `daily_profile_views`, `avg_like_count`, `avg_view_count`, etc.
- Evaluated feature importance using the model's built-in attribute.
- Applied SHAP to understand the contribution of each feature to model predictions.

### 4. Insights & Recommendations
- Created plots of feature importance and SHAP impact (see `insight.md`).
- Provided practical, personalized recommendations to help creators improve engagement.

## Results

- **Most impactful features:**  
  - `daily_profile_views` and `avg_like_count` are most critical for engagement prediction.
  - SHAP analysis supports the significance of `avg_like_count`, `engagement_velocity`, and `trend_resonance`.
- **Actionable recommendation:**  
  - Creators should focus on increasing daily profile views and average likes, plus experiment with content trends and upload consistency.

## How to Use

1. **Install dependencies:**  
pip install -r requirements.txt


2. **Run Notebooks:**  
- Open and run `Prepare_data.ipynb` to generate clean data.
- Run `analysis.ipynb` to compute metrics and generate `creator_metrics.csv`.
- Run `Model.ipynb` for model training, interpretation, and final recommendations.

## Files Included

- `Prepare_data.ipynb`
- `analysis.ipynb`
- `Model.ipynb`
- `creator_metrics.csv`
- `insight.md`
- `requirements.txt`
- `feature_importance.png`, `shap_summary_bar.png`

## Assumptions

- All CSV files are located in the working directory.
- Video themes are extracted using keyword or phrase analysis from descriptions.
- No external APIs or proprietary tools required.
