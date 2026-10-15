# NVIDIA GPU Performance & Value Analysis

An end-to-end Data Science project analyzing NVIDIA RTX 40 and RTX 50 Series GPUs through statistical analysis, machine learning, and price-to-performance evaluation.

## Project Overview

This project aims to understand the relationships between GPU hardware specifications and computational performance, compare GPU product generations, and develop a recommendation system that helps users select graphics cards based on budget and performance priorities.

The project combines exploratory data analysis (EDA), linear regression, KMeans clustering, feature engineering, and a rule-based recommendation system.

## Dataset

The dataset contains **18 GPU configurations and 29 features**, covering NVIDIA RTX 40 and RTX 50 Series graphics cards, including separate 8GB and 16GB variants.

The main hardware specifications include:

- CUDA Cores and Architecture
- AI TOPS and Ray Tracing TFLOPS
- Base and Boost Clock Speeds
- VRAM Capacity and Memory Type
- Memory Interface Width and Bandwidth
- MSRP (USD)

GPU specifications were collected primarily from NVIDIA's published comparison tables, with supplementary specifications added where needed.

## Dataset: (GPU_Specs_MSRP.csv)

## Data Cleaning and Preprocessing

Used Python and pandas to transform raw specification tables into a structured dataset.

- Extracted GPU specifications from web-based tables.
- Cleaned and standardized numerical and categorical values.
- Parsed mixed strings containing units and performance measurements.
- Combined RTX 40 and RTX 50 Series data.
- Handled multiple VRAM configurations.
- Created additional features for statistical analysis and value comparisons.

## Exploratory Data Analysis

Performed descriptive and comparative analysis to investigate differences between GPU models and product generations.

The analysis includes:

- Summary statistics and GPU rankings
- Generation-level specification comparisons
- Percentage differences between generations
- Correlation matrix and heatmap
- Relationships between computational performance and hardware specifications

## Statistical Analysis

Applied Simple and Multiple Linear Regression using `statsmodels` to examine relationships between GPU specifications and AI performance.

## Simple Linear Regression

- Dependent variable: AI TOPS
- Independent variable: CUDA Cores
- R²: 0.762

## Multiple Linear Regression

- Dependent variable: AI TOPS
- Independent variables: CUDA, VRAM, Memory Interface Width, and Memory Bandwidth
- R²: 0.977
- Adjusted R²: 0.970

Evaluated regression coefficients, standard errors, t-statistics, p-values, confidence intervals, and model fit.

These regression results describe relationships within the dataset and should not be interpreted as causal effects or validated out-of-sample prediction accuracy.

## KMeans Clustering

Applied KMeans clustering to segment GPUs based on similarities in hardware specifications.

Selected features include CUDA cores, VRAM, memory interface width, memory bandwidth, AI TOPS, and TFLOPS.

- Standardized numerical features using `StandardScaler`.
- Applied KMeans with four clusters.
- Examined cluster assignments and hardware characteristics.
- Interpreted the clusters as performance tiers: Entry, Mid-range, High-end, and Enthusiast.

## Price-to-Performance Analysis

Engineered five price-to-performance metrics using GPU specifications and MSRP:

- CUDA Cores per Dollar
- AI TOPS per Dollar
- TFLOPS per Dollar
- Memory Bandwidth per Dollar
- VRAM per Dollar

Applied Min-Max normalization to create an overall Value Score, allowing different performance metrics to contribute on a comparable scale.

GPU models were also grouped into product cohorts for separate comparisons.

## GPU Recommendation System

Developed an interactive, rule-based recommendation system that accepts three user inputs:

1. GPU product cohort
2. Maximum budget in USD
3. Performance priority: CUDA, AI, TFLOPS, Bandwidth, VRAM, or Balanced

The system first removes GPUs that exceed the user's budget, then ranks the remaining candidates using a weighted scoring system.

## Recommendation Score:

- 60% Budget Fit
- 25% User-Selected Priority Score
- 15% Overall Value Score

The system returns the top three recommended GPUs.

## Technologies Used

**Language:** Python

## Libraries and Tools:

- pandas and NumPy — Data manipulation and preprocessing
- Matplotlib and Seaborn — Data visualization
- statsmodels — Statistical modeling and linear regression
- scikit-learn — Feature scaling, normalization, and KMeans clustering
- Google Colab — Development environment
- GitHub — Version control and project documentation

## Project Files

** GPU_Performance_Value_Analysis.ipynb

Contains the complete Data Science workflow, including data cleaning, exploratory data analysis, statistical modeling, KMeans clustering, price-to-performance analysis, and the GPU recommendation system.

** GPU_Specs_MSRP.csv

Contains the cleaned NVIDIA GPU dataset, including hardware specifications, MSRP prices, clustering results, and engineered value metrics.

** README.md

Provides an overview of the project, methodology, technologies, results, and instructions for running the notebook.

## How to Run

1. Open the Jupyter Notebook in Google Colab.
2. Install any required Python libraries if necessary.
3. Run the notebook cells in order.
4. Review the visualizations and statistical results.
5. Enter a product cohort, budget, and performance preference in the recommendation section.

The notebook includes data collection steps that may depend on changes to external website structures. The provided CSV contains the saved analytical dataset.

## Limitations

- The analysis uses a relatively small dataset of 18 configurations.
- MSRP values are reference prices, not current retail market prices.
- Product cohorts are used for comparison and do not necessarily represent each model's exact release year.
- Hardware specifications are proxies for GPU capabilities and do not replace real-world application benchmarks.
- The recommendation system uses manually designed scoring weights rather than learned user preferences.

## Conclusion

This project demonstrates an end-to-end Data Science workflow, from data collection and cleaning to exploratory analysis, statistical modeling, clustering, feature engineering, and recommendation development.

The final system provides a structured approach to comparing NVIDIA GPUs and recommending products based on budget constraints and user-defined performance priorities.
