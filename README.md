
# 📊 Customer Churn Prediction with FastAPI + GenAI

This FastAPI-based application predicts customer churn using machine learning models (Logistic Regression, Random Forest, XGBoost) and generates human-readable summaries using OpenAI's GenAI API.

---

## 🔧 Features

- Upload customer data (CSV)
- Clean & preprocess input
- Train and evaluate ML models
- Predict churn on new data
- Download predictions as CSV
- Generate GenAI-powered explanations for each prediction

---

## 🛠️ Setup Instructions

### 1. Clone the repository
```bash
git clone https://github.com/your-username/customer-churn-app.git
cd customer-churn-app
```

### 2. Create and activate virtual environment
```bash
python -m venv venv
venv\Scripts\activate  # Windows
source venv/bin/activate  # macOS/Linux
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Set your OpenAI API Key
Create a `.env` file in the root directory:

```
OPENAI_API_KEY=sk-your-api-key-here
```

### 5. Start the FastAPI app
```bash
uvicorn app.main:app --reload
```

Visit [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs) for interactive Swagger UI.

---

## 📁 Folder Structure

```
customer-churn-app/
├── app/
│   ├── routes/         # Upload, training, predict, cleaning APIs
│   ├── services/       # GenAI logic and utilities
│   ├── utils/          # Helper functions for ML & data processing
│   ├── models/         # ML models saving/loading
│   └── main.py         # FastAPI entry point
├── data/               # Sample CSVs and output files
├── .env                # API keys and secrets
├── requirements.txt
└── README.md
```

---

## 🧪 API Endpoints

### `/upload`
- Upload raw CSV data

### `/clean`
- Preprocess and encode data

### `/train`
- Train a selected model (`logreg`, `rf`, `xgb`)

### `/predict`
- Predict churn for uploaded data
- Returns JSON + downloadable CSV
- Includes GenAI-based prediction summary

### `/download/{filename}`
- Download prediction results

---

## 🤖 GenAI Prompt Structure

When generating summaries, we use a prompt like:

> “Given the customer data: {feature_dict}, explain why the model predicted {Yes/No} for churn. Keep the explanation short and intuitive.”

The OpenAI Chat API is used with this prompt format to produce human-readable insights.

---

## 📂 Sample Files

- ✅ `customer_churn_large.csv` - input data for prediction
- ✅ `cleaned_customer_churn_large.csv` - preprocessed version
- ✅ `predicted_customer_churn_large.csv` - output with predictions and GenAI summaries

---

## ⚠️ Common Errors

- **401 Error**: Invalid or expired OpenAI API Key
- **429 Error**: Exceeded OpenAI quota – check billing and usage
- **404 Error**: Wrong filename in `/download/{filename}` – use only filename (no URL)
