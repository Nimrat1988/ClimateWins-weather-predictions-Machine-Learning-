# ClimateWins: Weather prediction (Machine Learning)

## Presentation (PDF)
- [View the Presentation](./Presentation.pdf)


## 1) Executive Summary
This project analyzes historical European weather data to help **ClimateWins** explore how machine learning can support climate-related insights. Using data from 18 weather stations (late 1800s–2022), I tested multiple supervised learning models to predict whether a day is **“pleasant”** or **“unpleasant.”** I compared model performance across stations and reviewed potential bias and limitations to ensure results are used responsibly.

## 2) Business Problem
ClimateWins wants to understand how climate change may impact weather patterns and decision-making. The main business questions are:
- Can we reliably classify days as **pleasant/unpleasant** using historical weather station data?
- Which machine learning model performs best across different stations?
- What data risks (bias, coverage gaps, changing measurement quality over time) could affect conclusions?

## 3) Methodology
1. **Data loading & cleaning**
   - Loaded the prepared/scaled dataset and validated station variables and labels.
   - Checked for missing values and consistency across stations and years.

2. **Feature selection**
   - Used station temperature features (mean temperatures by location) as inputs.
   - Removed non-scaled columns such as **DATE** and **MONTH** when needed.

3. **Optimization (Gradient Descent)**
   - Used gradient descent to observe convergence behavior and understand how **loss decreases over iterations**.
   - Tested learning rates (step sizes) and iterations to achieve stable convergence.

4. **Supervised learning models**
   - **KNN**
   - **Decision Tree**
   - **Artificial Neural Network (MLPClassifier)**
   - Evaluated using **train/test accuracy** and **multi-station confusion matrices**.

5. **Bias & ethics review**
   - Considered geographic bias (Europe-only stations), label bias (“pleasant” definition), and risk of incorrect predictions for extreme events.

## 4) Skills / Tools Used
- **Python** (pandas, numpy)
- **scikit-learn** (KNN, DecisionTreeClassifier, MLPClassifier, StandardScaler, metrics)
- **Matplotlib / Seaborn** (visuals, confusion matrices)
- **Plotly** (3D loss surface / optimization visuals)
- **Jupyter Notebook**
- **GitHub** (version control, documentation)

## 5) Results & Business Recommendations
### Key results
- **KNN performed strongly overall**, with an average accuracy around **88%** across stations.
- Accuracy varied by station (some locations were easier to classify than others).
- **Decision Trees** were easy to interpret but can **overfit** when the tree becomes very deep.
- **Scaled ANN (Neural Network)** is a strong option when accuracy is the main priority, especially after feature scaling.

### Business recommendations
- Use **Scaled ANN** as the primary model when the goal is best overall predictive performance.
- Keep **KNN** as a reliable baseline because it performs consistently well across stations.
- Monitor results by station to ensure the model is not strong in some locations and weak in others due to data quality differences.
- Treat “perfect” accuracy results cautiously (they may be caused by **imbalanced data** rather than true generalization).

## 6) Next Steps
- Improve reliability with **cross-validation** instead of a single train/test split.
- Tune hyperparameters further:
  - K in KNN
  - Tree depth / min samples in Decision Tree
  - Layers/nodes/iterations/tolerance in ANN
- Address class imbalance using **class weights** or resampling.
- Test the models on **new years/stations** to confirm generalization.
- Add more climate-related features (if available) to study longer-term trends and extreme events.
