# Apple App Store Success Prediction

A comprehensive data analysis and machine learning project that predicts the success of Apple App Store applications using historical app data and user ratings.

## Project Overview

This project analyzes Apple App Store data to understand factors that contribute to app success and builds machine learning models to predict whether an app will be successful (defined as having a user rating > 4.0).

## Dataset

The project uses Apple App Store data contained in the `input/` folder:
- `AppleStore.csv` - Main app data including ratings, prices, genres, etc.
- `AppleStore1.csv` - Additional app data
- `appleStore_description.csv` - App descriptions
- `appleStore_description1.csv` - Additional app descriptions

**Dataset Statistics:**
- Total apps analyzed: ~7,200
- Free apps: 4,056
- Paid apps: 3,141

## Key Features Analyzed

### Basic Features
- **App Size**: Size in MB (converted from bytes)
- **Pricing**: Free vs. paid apps, price analysis
- **Genre**: 23 different app categories
- **User Ratings**: Average user rating and rating counts
- **Device Support**: Number of supported devices
- **Language Support**: Number of supported languages

### Engineered Features
- **isNotFree**: Binary indicator for paid apps
- **rating_count_before**: Previous version rating counts
- **isGame**: Binary indicator for game-related apps (from description)
- **descLen**: Length of app description
- **Most frequent words**: Top 3 most frequent words in app descriptions

## Key Findings

### Genre Analysis
**Most Popular Genres:**
1. **Games** - Most popular across both free and paid apps
2. **Entertainment** - Second most popular for free apps
3. **Photo & Video** - Third most popular for free apps

### User Rating Insights
**Highest Rated Genres:**
- **Free Apps**: Productivity, Music, Photo & Video
- **Paid Apps**: Catalogs, Shopping, Productivity

**Key Observation**: Book, Catalogs, and Navigation apps have significantly higher ratings when they are paid vs. free.

### App Size Patterns
- **Medical apps** have the largest average size (~400MB)
- **Games** are second largest (~300MB)
- Paid apps in Book, Catalogs, and Medical categories are 2x+ larger than their free counterparts

### Pricing Analysis
- **Most expensive genre**: Medical apps (~$14 average)
- **Mid-range pricing**: Business, Reference, Music, Productivity, Navigation, Education (~$5 average)

## Machine Learning Models

### Problem Definition
- **Type**: Binary classification
- **Target**: App success (user rating > 4.0 = 1, ≤ 4.0 = 0)
- **Features**: 31-33 features including app metadata, pricing, and engineered features

### Models Evaluated
1. **Random Forest Classifier**
2. **LightGBM Classifier**
3. **XGBoost Classifier**

### Results
- **Accuracy**: ~70% across all models
- **Cross-validation**: 5-fold cross-validation used for model evaluation
- **Feature Impact**: Adding description-based features (isGame, descLen) improved model performance

## Technology Stack

### Data Analysis & Visualization
- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computations
- **matplotlib & seaborn** - Static visualizations
- **plotly** - Interactive visualizations

### Natural Language Processing
- **nltk** - Text processing and tokenization
- **stopwords** - Text cleaning

### Machine Learning
- **scikit-learn** - Model evaluation and preprocessing
- **xgboost** - Gradient boosting classifier
- **lightgbm** - Gradient boosting classifier

## How to Run

1. **Install Dependencies**:
   ```bash
   pip install pandas numpy matplotlib seaborn plotly nltk scikit-learn xgboost lightgbm missingno
   ```

2. **Download NLTK Data**:
   ```python
   import nltk
   nltk.download('stopwords')
   nltk.download('punkt')
   ```

3. **Run the Analysis**:
   Open `kernel.ipynb` in Jupyter Notebook and run all cells sequentially.

## Project Structure

```
App-success-prediction/
├── input/                          # Dataset files
│   ├── AppleStore.csv             # Main app data
│   ├── AppleStore1.csv            # Additional app data
│   ├── appleStore_description.csv  # App descriptions
│   └── appleStore_description1.csv # Additional descriptions
├── kernel.ipynb                    # Main analysis notebook
└── README.md                      # This file
```

## Future Improvements

- Add more sophisticated text analysis features
- Implement deep learning models for better accuracy
- Include temporal features (app release date, updates)
- Explore ensemble methods for improved predictions
- Add feature importance analysis

## Results Summary

The analysis successfully identifies key factors that contribute to app success in the Apple App Store:

1. **Genre matters**: Productivity, Music, and Photo & Video apps tend to have higher ratings
2. **Pricing strategy**: Some genres (Books, Catalogs, Medical) perform better as paid apps
3. **Size correlation**: Larger apps in certain categories (Medical, Games) often justify higher prices
4. **Description quality**: Apps with game-related keywords and optimal description length show different success patterns

The machine learning models achieve 70% accuracy in predicting app success, providing a solid foundation for further improvements and real-world applications.

