# 🏠 House Price Prediction System
**AlgoHub Software House — Machine Learning Internship Program (Week 1, Beginner)**

## 📌 Objective
Predict residential house prices using regression techniques, based on
property attributes: number of bedrooms, bathrooms, size (sq ft), and zip code (location).

## 📊 Dataset
- **Source:** Provided dataset (`final_dataset.csv`), renamed to `data/house_data.csv`
- **Rows:** 2,016 (after removing 1 duplicate/invalid row)
- **Columns:**
  | Column | Description |
  |---|---|
  | beds | Number of bedrooms |
  | baths | Number of bathrooms |
  | size | House size in square feet |
  | zip_code | Location (zip code) |
  | price | Target variable — sale price ($) |

No missing values were present in the raw data.

## 🧹 Data Preprocessing
1. Dropped duplicate rows and unused index column.
2. Removed invalid rows (zero/negative beds, baths, size, or price).
3. Removed price outliers using the IQR method.
4. **Feature engineering:**
   - `beds_baths_total` = beds + baths
   - `zip_code_freq` = frequency encoding of zip code (captures location popularity without one-hot blow-up across 28 zip codes)
5. Final model features: `beds`, `baths`, `size`, `zip_code_freq`, `beds_baths_total`

## 📈 Exploratory Data Analysis
See `screenshots/` for:
- `correlation_heatmap.png` — feature correlation with price
- `price_distribution.png` — right-skewed price distribution
- `size_vs_price.png` — strong positive relationship between size and price

## 🤖 Models Trained
| Model | MAE | RMSE | R² Score |
|---|---|---|---|
| Linear Regression | ~182,884 | ~242,067 | 0.5735 |
| **Random Forest Regressor (selected)** | **~156,850** | **~210,494** | **0.6775** |

Random Forest Regressor was selected as the final model based on higher R² and lower error on the test set (80/20 train-test split, random_state=42).

## 🛠️ Tech Stack
- Python, Pandas, NumPy, Scikit-Learn
- Matplotlib, Seaborn (EDA)
- Streamlit (deployment)
- Joblib (model persistence)

## 📂 Project Structure
```
AlgoHub_Task1_HousePricePrediction/
├── data/
│   └── house_data.csv
├── notebooks/
│   └── eda.py
├── src/
│   ├── preprocess.py
│   └── train.py
├── screenshots/
│   ├── correlation_heatmap.png
│   ├── price_distribution.png
│   └── size_vs_price.png
├── app.py
├── model.pkl
├── zip_freq_map.pkl
├── metrics.json
├── requirements.txt
└── README.md
```

## ▶️ How to Run

### 1. Clone the repository
```bash
git clone <your-repo-url>
cd AlgoHub_Task1_HousePricePrediction
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. (Optional) Re-train the model
```bash
cd src
python train.py
```
This regenerates `model.pkl`, `zip_freq_map.pkl`, and `metrics.json` in the project root.

### 4. Run the Streamlit app
```bash
streamlit run app.py
```
The app will open at `http://localhost:8501`.

## 🎯 Results & Screenshots
*(Add your Streamlit app screenshots here after running it locally / deploying it)*

## 🚀 Live Deployment
*(Add your live Streamlit Cloud URL here once deployed)*

## 🎥 Demo Video
*(Add your demo video link here — should cover: dataset overview, preprocessing, training, evaluation metrics, and live demo)*

## 👤 Author
Submitted as part of the **AlgoHub Software House Machine Learning Internship Program** — Week 1: House Price Prediction System.

#AlgoHub #MachineLearning #Internship #HousePricePrediction
