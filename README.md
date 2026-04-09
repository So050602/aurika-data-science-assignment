# Aurika Data Science Assignment

## 📌 Objective
Predict:
- **covers_count** → number of guests
- **avg_check** → average spend per guest

---

## 🧠 Approach

### Data Cleaning
- Removed incomplete days using `is_complete`
- Filtered invalid values (zero covers / avg_check)
- Excluded anomaly rows and special events (buyouts)
- Removed cancelled and pending reservations
- Handled missing timestamps and derived lead time

---

### Feature Engineering
- **Time Features**: day of week, month, weekend  
- **Reservation Features**: total reservations, total party size, VIP count, lead time  
- **Lag Features**: 7-day and 14-day lag  
- **Rolling Features**: 7-day mean and standard deviation  
- **Behavior Features**: reservation per person, VIP ratio  

---

## 🤖 Models Used
- XGBoost Regressor for both targets

---

## 📊 Results

### Covers Model
- **MAE:** 10.7  
- **wMAPE:** 6.2%  
- ~40% improvement over baseline (MAE reduced from ~18.4 to 10.7)

### Avg Check Model
- **MAE:** 6.03  
- **wMAPE:** 7.2%  

---

## 🔍 Key Insights
- Reservation volume is the strongest predictor of demand  
- Party size significantly impacts guest count  
- Strong weekly seasonality observed  
- Lag and rolling features help stabilize predictions  
- Model struggles with extreme spikes due to lack of external features (e.g., events, holidays)

---

## 🧠 Why the Model Works
The model performs well because it combines:
- Reservation-based signals (leading indicators of demand)
- Temporal features capturing weekly seasonality
- Lag and rolling features capturing time-series dependencies

This allows the model to learn both short-term fluctuations and recurring patterns.

---

## 📁 Files
- `analysis.ipynb` → complete workflow  
- `covers_model.pkl` → trained demand model  
- `avg_check_model.pkl` → trained revenue model  

---

## ▶️ How to Run

1. Open `analysis.ipynb`
2. Run all cells sequentially
3. Models are already saved as `.pkl` files

### Dependencies:
- pandas  
- numpy  
- scikit-learn  
- xgboost  
- matplotlib  

---

## 🚀 Notes
This project focuses on building a practical and reliable forecasting solution by combining time-series features with reservation-based signals. The approach emphasizes both predictive performance and interpretability.