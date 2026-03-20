# Exoplanet Intelligence System

A production-ready full-stack web application for the Innorave Eco-Hackathon. This system provides machine learning-powered predictions for exoplanet classification and radius estimation using NASA Kepler mission data.

##Live Application: http://exoplanet-intelligence.vercel.app/

## 🚀 Features

### Classification Task
- Predict whether an exoplanet candidate is **CONFIRMED** or **FALSE POSITIVE**
- Based on transit and stellar properties
- F1-score optimized model
- ROC-AUC evaluation

### Regression Task
- Predict planetary radius in **Earth radii**
- Based on transit depth, orbital properties, and stellar characteristics
- RMSE and MAE evaluation
- 95% Confidence Intervals

### Full-Stack Features
- 🖥️ **Frontend**: React.js with modern UI
- ⚡ **Backend**: FastAPI for high-performance API
- 🤖 **ML Pipeline**: scikit-learn with XGBoost
- 💾 **Database**: PostgreSQL via Supabase
- 📊 **Visualization**: Interactive charts with Recharts
- ✅ **Validation**: Client-side form validation

## 📁 Project Structure

```
exoplanet-intelligence-system/
├── frontend/                 # React.js frontend
│   ├── src/
│   │   ├── components/      # UI components
│   │   ├── pages/           # Page components
│   │   ├── services/        # API services
│   │   └── utils/           # Utility functions
│   ├── package.json
│   └── vite.config.js
│
├── backend/                  # FastAPI backend
│   ├── app/
│   │   ├── main.py         # Application entry point
│   │   ├── routes.py       # API routes
│   │   ├── schemas.py      # Pydantic schemas
│   │   ├── database.py     # Database configuration
│   │   ├── crud.py         # Database operations
│   │   ├── model_loader.py # ML model loading
│   │   └── utils.py        # Utility functions
│   ├── models/             # Trained ML models
│   └── requirements.txt
│
├── ml/                       # ML pipeline
│   ├── download_data.py    # Data download script
│   ├── preprocessing.py    # Data preprocessing
│   ├── feature_selection.py # Feature selection
│   ├── train_classification.py
│   └── train_regression.py
│
├── database/                 # Database files
│   ├── schema.sql          # Database schema
│   └── seed_data.sql       # Sample data
│
├── docs/                     # Documentation
│   ├── api_docs.md         # API documentation
│   └── deployment_guide.md # Deployment guide
│
└── README.md
```

## 🛠️ Tech Stack

### Frontend
- **React 18** - UI framework
- **Vite** - Build tool
- **Tailwind CSS** - Styling
- **Recharts** - Data visualization
- **Axios** - HTTP client
- **Lucide React** - Icons

### Backend
- **FastAPI** - Web framework
- **Uvicorn** - ASGI server
- **Pydantic** - Data validation
- **Supabase** - PostgreSQL database
- **Joblib** - Model serialization

### Machine Learning
- **scikit-learn** - ML pipeline
- **XGBoost** - Gradient boosting
- **Pandas** - Data manipulation
- **NumPy** - Numerical computing

## 📋 API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/health` | GET | Health check |
| `/api/predict/classification` | POST | Classification prediction |
| `/api/predict/regression` | POST | Regression prediction |
| `/api/predictions/history` | GET | Prediction history |
| `/api/models/info` | GET | Model information |

## 🔧 Installation

### Prerequisites
- Node.js 18+
- Python 3.9+
- PostgreSQL database (Supabase)

### Backend Setup

```
bash
# Navigate to backend directory
cd backend

# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Copy environment variables
cp .env.example .env
# Edit .env with your configuration

# Run the server
uvicorn app.main:app --reload
```

### Frontend Setup

```
bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Copy environment variables
cp .env.example .env
# Edit .env with API URL

# Run development server
npm run dev
```

## 🧪 Usage

### Using the Web Interface

1. Open `http://localhost:5173` in your browser
2. Select task type (Classification or Regression)
3. Enter exoplanet features
4. Click Predict
5. View results and visualizations

### Using the API

```
bash
# Classification
curl -X POST http://localhost:8000/api/predict/classification \
  -H "Content-Type: application/json" \
  -d '{
    "features": {
      "koi_prad": 2.5,
      "koi_depth": 150,
      "koi_period": 45.3,
      "koi_srad": 1.2,
      "koi_steff": 5800,
      "koi_smass": 1.1,
      "koi_slogg": 4.3,
      "koi_lum": 0.1,
      "koi_impact": 0.6,
      "koi_duration": 3.5,
      "koi_dor": 22.5,
      "koi_model_snr": 25.0,
      "koi_kepmag": 14.2,
      "koi_score": 0.85
    }
  }'

# Regression
curl -X POST http://localhost:8000/api/predict/regression \
  -H "Content-Type: application/json" \
  -d '{
    "features": {
      "koi_prad": 2.5,
      "koi_depth": 150,
      "koi_period": 45.3,
      "koi_srad": 1.2,
      "koi_steff": 5800,
      "koi_smass": 1.1,
      "koi_slogg": 4.3,
      "koi_lum": 0.1,
      "koi_impact": 0.6,
      "koi_duration": 3.5,
      "koi_dor": 22.5,
      "koi_model_snr": 25.0,
      "koi_kepmag": 14.2,
      "koi_score": 0.85
    }
  }'
```

## 🎯 Model Performance

### Classification
- **Model**: RandomForest/XGBoost Classifier
- **F1-Score**: ~0.95
- **ROC-AUC**: ~0.98

### Regression
- **Model**: XGBoost Regressor
- **RMSE**: ~0.35 Earth radii
- **MAE**: ~0.28 Earth radii

## 📦 Deployment

### Backend (Render/Railway)
See [Deployment Guide](docs/deployment_guide.md) for detailed instructions.

### Frontend (Vercel)
1. Push code to GitHub
2. Import repository to Vercel
3. Configure build settings
4. Deploy

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🙏 Acknowledgments

- NASA Kepler mission for the exoplanet data
- scikit-learn and XGBoost communities
- FastAPI and React communities

---

Built with ❤️ for the Innorave Eco-Hackathon
