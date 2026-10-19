# 🌾 AgriTrade Analyst

**An AI-powered agricultural financial assistant for Indian farmers**

---

## 📖 Introduction

**AgriTrade Analyst** is a comprehensive decision-support platform designed to empower Indian farmers with data-driven insights for maximizing agricultural profitability. Built with cutting-edge Machine Learning and AI technologies, this platform addresses critical challenges faced by farmers in crop pricing, market selection, financial planning, and crop health management.

### What Does AgriTrade Analyst Do?

- **Predicts Crop Prices** using Machine Learning (SARIMAX time-series forecasting)
- **Calculates Financial Metrics** including estimated revenue, cost, and net profit
- **Identifies Profitable Markets** through intelligent arbitrage analysis across districts
- **Provides Weather-Based Advisories** with real-time risk assessments
- **Computes Farmer Credit Scores** to evaluate financial health (0-1000 scale)
- **Supports Voice-Based Interaction** including Telugu language support for accessibility
- **Detects Crop Diseases** using Gemini Vision AI for early intervention
- **Forecasts 30-Day Price Trends** with daily profit predictions

This platform bridges the gap between traditional farming practices and modern technology, enabling farmers to make informed decisions that maximize their returns while minimizing risks.

---

## ✨ Core Features

### 1. 🧮 Agricultural Profit Calculator

The profit calculator provides farmers with accurate financial projections based on their farming inputs.

**Key Capabilities:**
- **ML-Based Price Prediction**: Uses historical price data from a comprehensive static dataset covering multiple districts and crops
- **Dual Expense Modes**:
  - **Recommended Mode**: Automatically calculates expenses based on crop-specific cost data
  - **Custom Mode**: Allows farmers to input their actual expenses for personalized calculations
- **Revenue Calculation**: Computes expected revenue using predicted prices and crop yield estimates
- **Net Profit Analysis**: Provides clear profit/loss projections to aid decision-making

**How It Works:**
1. Farmer selects district, crop, season, and acreage
2. System fetches predicted price from ML model
3. Calculates revenue = Price × Yield × Acres
4. Deducts expenses (recommended or custom)
5. Displays net profit with detailed breakdown

---

### 2. 🔄 Smart Market Arbitrage Finder

Helps farmers identify the most profitable market to sell their produce by comparing prices across districts.

**Key Capabilities:**
- **Multi-District Price Comparison**: Analyzes crop prices across all Telangana districts
- **Transport Cost Calculation**: Estimates transportation expenses based on distance
- **Net Gain Analysis**: Computes actual profit after accounting for transport costs
- **Top 3 Recommendations**: Ranks districts by maximum net gain

**How It Works:**
1. System compares current crop prices across all districts
2. Calculates distance from farmer's district to each market
3. Estimates transport cost (₹5 per km per quintal)
4. Computes net gain = (Price Difference × Quantity) - Transport Cost
5. Recommends top 3 districts with highest net gain

**Example Output:**
```
District: Hyderabad
Price: ₹2,800/quintal
Distance: 120 km
Transport Cost: ₹600
Net Gain: ₹4,200
```

---

### 3. 📊 30-Day Price & Profit Forecast

Provides farmers with a 30-day forward-looking view of expected prices and profits.

**Key Capabilities:**
- **SARIMAX ML Pipeline**: Uses Seasonal AutoRegressive Integrated Moving Average with eXogenous factors
- **Daily Price Predictions**: Forecasts crop prices for the next 30 days
- **Profit Projections**: Calculates expected daily profit based on predicted prices
- **Trend Visualization**: Helps farmers identify optimal selling windows

**How It Works:**
1. ML model trained on historical price data (district + crop specific)
2. SARIMAX algorithm captures seasonal patterns and trends
3. Generates 30-day price forecast
4. Calculates daily profit = (Predicted Price × Yield × Acres) - Total Expense
5. Returns structured data for visualization

**Technical Details:**
- Model: SARIMAX (Statsmodels library)
- Training Data: Historical district-wise crop prices
- Output: Daily predictions with date, price, income, and profit

---

### 4. 🌦️ Weather Advisory System

Provides real-time weather data and actionable farming advice based on current conditions.

**Key Capabilities:**
- **Live Weather Data**: Fetches real-time weather from Open-Meteo API
- **District-Specific Forecasts**: Covers all 33 Telangana districts with precise coordinates
- **Risk Level Computation**: Analyzes weather parameters to determine farming risk (Low/Moderate/High)
- **Actionable Advisories**: Provides specific recommendations based on weather conditions

**Risk Assessment Logic:**
- **High Risk**: Heavy rainfall (>10mm) or high humidity (>85%)
- **Moderate Risk**: Extreme heat (>40°C) or high winds (>20 km/h)
- **Low Risk**: Normal weather conditions

**Weather Parameters Tracked:**
- Temperature (°C)
- Humidity (%)
- Rainfall (mm)
- Wind Speed (km/h)

**Example Advisory:**
```
Risk Level: High Risk
Advisory: "Heavy rainfall detected. Delay harvest and protect stored crops."
```

---

### 5. 💳 Agri Credit Score Engine

Evaluates farmer financial health using a comprehensive scoring algorithm.

**Key Capabilities:**
- **1000-Point Scale**: Provides a standardized credit score (0-1000)
- **Multi-Factor Analysis**: Considers profitability, cost efficiency, and market risk
- **Tier Classification**: Categorizes farmers into Gold, Silver, or High Risk tiers
- **ML-Based Risk Assessment**: Uses price volatility from 30-day forecasts

**Scoring Components:**
1. **Profitability Score (40%)**: Based on profit margin percentage
2. **Cost Efficiency Score (30%)**: Evaluates expense-to-income ratio
3. **Market Risk Score (30%)**: Analyzes price volatility using ML forecasts

**Tier Classification:**
- **Gold Tier**: Score ≥ 700 (Low risk, high creditworthiness)
- **Silver Tier**: Score 400-699 (Moderate risk)
- **High Risk Tier**: Score < 400 (High risk, needs financial support)

**Formula:**
```
Credit Score = (Profitability × 0.4) + (Cost Efficiency × 0.3) + (Market Stability × 0.3)
```

---

### 6. 🎤 Voice Assistant (Telugu + English)

Enables hands-free interaction with the platform using natural language voice commands.

**Key Capabilities:**
- **Web Speech API Integration**: Browser-based speech recognition (no external API costs)
- **Bilingual Support**: Recognizes both English and Telugu voice commands
- **Free-Flow Queries**: Understands natural language like "Paddy price Cheppandi" (Tell me paddy price)
- **Intelligent Intent Matching**: Uses fuzzy keyword matching to identify user intent
- **Auto-Navigation**: Automatically routes users to the correct tool/page
- **Auto-Fill Forms**: Populates crop and district fields based on voice input

**Supported Intents:**
- **PRICE**: "What is the price of paddy?" → Navigates to Finance Tracker
- **LOAN**: "I need a loan" → Navigates to Loan Calculator
- **SCHEMES**: "Tell me about government schemes" → Navigates to Schemes page

**Example Commands:**
- English: "Show me paddy price in Warangal"
- Telugu: "వరంగల్ లో వరి ధర చెప్పండి" (Tell me paddy price in Warangal)

---

### 7. 🔬 Crop Disease Detection

Uses Google Gemini Vision AI to identify crop diseases from leaf images.

**Key Capabilities:**
- **Image Upload**: Supports common image formats (JPG, PNG)
- **AI-Powered Analysis**: Uses Gemini 2.0 Flash Vision model
- **Disease Identification**: Detects diseases or confirms healthy plants
- **Confidence Scoring**: Provides accuracy percentage for predictions
- **Severity Assessment**: Classifies disease severity (Low/Moderate/High)
- **Treatment Recommendations**: Suggests specific treatment steps
- **Prevention Tips**: Provides preventive measures to avoid future infections

**How It Works:**
1. Farmer uploads leaf image
2. Image sent to Gemini Vision API
3. AI analyzes visual patterns and symptoms
4. Returns structured JSON response with diagnosis
5. Frontend displays disease details and recommendations

**Example Output:**
```json
{
  "disease": "Bacterial Leaf Blight",
  "confidence": "92%",
  "severity": "Moderate",
  "treatment": "Apply copper-based fungicide. Remove infected leaves.",
  "prevention": "Ensure proper drainage. Avoid overhead irrigation."
}
```

---

### 8. 🌐 Multilingual Support

The platform supports multiple languages to ensure accessibility for all farmers.

**Supported Languages:**
- **English**: Full UI and voice support
- **Telugu**: Voice command recognition and chatbot responses

**Implementation:**
- Voice commands processed in both languages
- Chatbot provides responses in user's preferred language
- Language selection available in UI

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         FRONTEND (React)                        │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│  │ Finance      │  │ Arbitrage    │  │ Disease      │         │
│  │ Tracker      │  │ Finder       │  │ Detector     │         │
│  └──────────────┘  └──────────────┘  └──────────────┘         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│  │ Voice        │  │ Forecast     │  │ Weather      │         │
│  │ Assistant    │  │ Page         │  │ Advisory     │         │
│  └──────────────┘  └──────────────┘  └──────────────┘         │
└─────────────────────────────────────────────────────────────────┘
                              │
                              │ HTTP/REST API
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                      BACKEND (Flask/Python)                     │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│  │ app.py       │  │ model.py     │  │ ml_pipeline  │         │
│  │ (Routes)     │  │ (Financials) │  │ (SARIMAX)    │         │
│  └──────────────┘  └──────────────┘  └──────────────┘         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│  │ arbitrage.py │  │ credit_score │  │ chatbot.py   │         │
│  │              │  │ .py          │  │              │         │
│  └──────────────┘  └──────────────┘  └──────────────┘         │
└─────────────────────────────────────────────────────────────────┘
                              │
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
        ▼                     ▼                     ▼
┌──────────────┐      ┌──────────────┐     ┌──────────────┐
│   DATASETS   │      │  EXTERNAL    │     │   AI APIs    │
│              │      │   APIs       │     │              │
│ • Districts  │      │              │     │ • Gemini Pro │
│ • CropCost   │      │ • OpenWeather│     │ • Gemini     │
│ • Prices     │      │ • Open-Meteo │     │   Vision     │
└──────────────┘      └──────────────┘     └──────────────┘
```

**Data Flow:**
1. User interacts with React frontend
2. Frontend sends HTTP requests to Flask backend
3. Backend processes requests using:
   - Static datasets (CSV files)
   - ML models (SARIMAX)
   - External APIs (Weather, AI)
4. Backend returns JSON responses
5. Frontend displays results to user

---

## 🛠️ Technologies Used

### Frontend
- **React** - UI framework for building interactive components
- **TailwindCSS** - Utility-first CSS framework for styling
- **Vite** - Fast build tool and development server
- **Web Speech API** - Browser-based voice recognition
- **Axios** - HTTP client for API requests

### Backend
- **Flask** - Lightweight Python web framework
- **Python 3.x** - Core programming language
- **Flask-CORS** - Cross-Origin Resource Sharing support

### Machine Learning & AI
- **SARIMAX** - Time-series forecasting model
- **Statsmodels** - Statistical modeling library
- **Pandas** - Data manipulation and analysis
- **NumPy** - Numerical computing
- **Google Gemini Pro** - Conversational AI for chatbot
- **Google Gemini Vision** - Image analysis for disease detection

### External APIs
- **Open-Meteo API** - Real-time weather data
- **OpenWeather API** - Weather forecasting (optional)

### Datasets
- **Districts Dataset** - District-wise crop prices (690KB, comprehensive)
- **CropCost Dataset** - Crop-specific expense data
- **Latest Prices CSV** - Real-time scraped price data

### Development Tools
- **Git** - Version control
- **npm** - Package management
- **pip** - Python package management
- **dotenv** - Environment variable management

---

## 📁 File Structure

```
agriTrade_analyst-main/
│
├── backend/                          # Flask backend
│   ├── datasets/                     # Data files
│   │   ├── DISTRTICTS_DATASET final.csv   # District-wise crop prices
│   │   ├── Cropcost.csv              # Crop expense data
│   │   ├── latest_prices.csv         # Scraped real-time prices
│   │   └── forecast_output.csv       # ML forecast cache
│   │
│   ├── app.py                        # Main Flask application
│   ├── model.py                      # Financial calculation logic
│   ├── ml_pipeline.py                # SARIMAX forecasting pipeline
│   ├── arbitrage.py                  # Market arbitrage logic
│   ├── credit_score.py               # Credit scoring algorithm
│   ├── chatbot.py                    # Gemini chatbot integration
│   ├── daily_fetch.py                # Price scraper utility
│   ├── test_weather.py               # Weather API testing
│   ├── .env                          # Environment variables (API keys)
│   └── requirements.txt              # Python dependencies
│
├── project/                          # React frontend
│   ├── src/
│   │   ├── pages/
│   │   │   ├── FinanceTracker.jsx    # Main profit calculator
│   │   │   ├── ForecastPage.jsx      # 30-day forecast UI
│   │   │   ├── DiseaseDetector.jsx   # Crop disease detection
│   │   │   ├── AgriBotPage.jsx       # Chatbot interface
│   │   │   └── ...
│   │   │
│   │   ├── components/
│   │   │   ├── MarketArbitrageCard.jsx    # Arbitrage display
│   │   │   ├── CreditScoreCard.jsx        # Credit score UI
│   │   │   ├── ChatMessage.jsx            # Chat message component
│   │   │   ├── LanguageSelector.jsx       # Language switcher
│   │   │   └── ...
│   │   │
│   │   ├── context/
│   │   │   └── LanguageContext.jsx   # Language state management
│   │   │
│   │   ├── utils/
│   │   │   └── translations.js       # Multilingual text
│   │   │
│   │   ├── App.jsx                   # Main app component
│   │   └── main.jsx                  # Entry point
│   │
│   ├── public/                       # Static assets
│   ├── index.html                    # HTML template
│   ├── package.json                  # Node dependencies
│   ├── vite.config.js                # Vite configuration
│   └── tailwind.config.js            # TailwindCSS config
│
├── .gitignore                        # Git ignore rules
└── README.md                         # This file
```

---

## 🚀 Installation Instructions

Follow these steps to set up AgriTrade Analyst on your local machine:

### Prerequisites
- **Python 3.8+** installed
- **Node.js 16+** and npm installed
- **Git** installed
- **Google Gemini API Key** (get from [Google AI Studio](https://makersuite.google.com/app/apikey))

### Step 1: Clone the Repository
```bash
git clone https://github.com/yourusername/agriTrade_analyst.git
cd agriTrade_analyst-main
```

### Step 2: Backend Setup

#### 2.1 Navigate to Backend Directory
```bash
cd backend
```

#### 2.2 Create Environment File
Create a `.env` file in the `backend` directory:
```bash
touch .env
```

#### 2.3 Add API Key
Open `.env` and add your Gemini API key:
```
GEMINI_API_KEY=your_gemini_api_key_here
```

#### 2.4 Install Python Dependencies
```bash
pip install -r requirements.txt
```

**Required packages:**
- Flask
- flask-cors
- pandas
- numpy
- statsmodels
- google-generativeai
- python-dotenv
- requests

#### 2.5 Start Backend Server
```bash
python app.py
```

The backend will run on `http://localhost:5000`

### Step 3: Frontend Setup

#### 3.1 Navigate to Frontend Directory
Open a new terminal and navigate to the project directory:
```bash
cd project
```

#### 3.2 Install Node Dependencies
```bash
npm install
```

**Key packages:**
- react
- react-dom
- react-router-dom
- axios
- tailwindcss
- vite

#### 3.3 Start Development Server
```bash
npm run dev
```

The frontend will run on `http://localhost:5173`

### Step 4: Open in Browser
Open your browser and navigate to:
```
http://localhost:5173
```

---

## 📖 How to Use the Application

### 1. Calculate Profit

1. **Select District**: Choose your district from the dropdown
2. **Select Crop**: Choose the crop you're growing
3. **Select Season**: Choose the current season (Kharif/Rabi/Summer)
4. **Enter Acreage**: Input the number of acres
5. **Choose Expense Mode**:
   - **Recommended**: System calculates standard expenses
   - **Custom**: Enter your actual expenses per acre
6. **Click "Calculate"**: View your financial overview

**Output:**
- Predicted Price (per quintal)
- Total Revenue
- Total Expenses
- Net Profit/Loss

---

### 2. Find Best Market (Arbitrage)

After calculating profit:
1. Scroll to the **Market Arbitrage** section
2. View the top 3 recommended districts
3. Check:
   - District name
   - Current price
   - Distance from your location
   - Transport cost
   - Net gain after transport

**Decision Making:**
- If net gain is positive and significant, consider selling in that market
- Compare transport logistics and feasibility

---

### 3. View Weather Advisory

1. Weather data is automatically fetched for your selected district
2. View current conditions:
   - Temperature
   - Humidity
   - Rainfall
   - Wind Speed
3. Check **Risk Level** (Low/Moderate/High)
4. Read **Advisory Message** for actionable recommendations

---

### 4. View 30-Day Forecast

1. Click **"View 30-Day Forecast & Weather"** button
2. System runs ML pipeline (may take a few seconds)
3. View daily predictions for next 30 days:
   - Date
   - Predicted Price
   - Expected Income
   - Expected Profit
4. Identify optimal selling windows

---

### 5. Check Credit Score

1. After calculating profit, scroll to **Credit Score** section
2. View your score (0-1000)
3. Check your tier:
   - 🏆 Gold (700+)
   - 🥈 Silver (400-699)
   - ⚠️ High Risk (<400)
4. Review score breakdown:
   - Profitability Score
   - Cost Efficiency Score
   - Market Risk Score

---

### 6. Use Voice Assistant

1. Click the **microphone icon** (usually in navigation or floating button)
2. Allow microphone permissions when prompted
3. Speak your query in English or Telugu:
   - "What is the price of paddy in Warangal?"
   - "వరి ధర చెప్పండి" (Tell me paddy price)
4. System will:
   - Recognize your intent
   - Navigate to appropriate page
   - Auto-fill relevant fields

---

### 7. Detect Crop Disease

1. Navigate to **Disease Detector** page
2. Click **"Upload Image"** or drag-and-drop
3. Select a clear photo of the affected leaf
4. Click **"Analyze"**
5. Wait for AI analysis (5-10 seconds)
6. View results:
   - Disease name (or "Healthy Plant")
   - Confidence percentage
   - Severity level
   - Treatment recommendations
   - Prevention tips

**Tips for Best Results:**
- Use clear, well-lit images
- Focus on affected areas
- Avoid blurry or distant shots

---

### 8. Chat with Agri-Bot

1. Navigate to **Agri-Bot** page
2. Select language (English/Telugu)
3. Type your question or use voice input
4. Get instant responses about:
   - Crop prices
   - Government schemes
   - Farming best practices
   - Loan information
   - Weather advisories

---

## 📸 Screenshots

### Dashboard Overview
*[Screenshot placeholder - Upload your main dashboard image here]*
<img width="1917" height="1092" alt="image" src="https://github.com/user-attachments/assets/10517815-1b39-4f95-a56b-519e59c8082a" />

---

### Financial Calculator
*[Screenshot placeholder - Upload profit calculator interface]*
<img width="1917" height="1092" alt="image" src="https://github.com/user-attachments/assets/48dd24f3-0d96-4768-b183-d694a6caf3f9" />

---

### Market Arbitrage Finder
<img width="1107" height="546" alt="image" src="https://github.com/user-attachments/assets/b64a4515-9ec5-4dfe-9de7-cd28e4f802ad" />

---

### 30-Day Forecast
<img width="1032" height="1076" alt="image" src="https://github.com/user-attachments/assets/f7dbb375-ebf6-49c1-b9b1-29a21147a670" />

---

### Weather Advisory
<img width="1073" height="347" alt="image" src="https://github.com/user-attachments/assets/64307c14-f215-424b-9573-ab057d015ad7" />

---

### Credit Score Display
<img width="1110" height="478" alt="image" src="https://github.com/user-attachments/assets/620e4564-aee2-486b-8cbb-9170730457c7" />

---


### Disease Detection Results
<img width="1585" height="1007" alt="image" src="https://github.com/user-attachments/assets/945255b9-174c-40e1-ba9a-d3e45bd87188" />

---

### Chatbot Interface
*[Screenshot placeholder - Upload chatbot conversation]*
<img width="1166" height="892" alt="image" src="https://github.com/user-attachments/assets/8711ac82-1609-4294-b33e-4645e9a708fc" />

---

## 🔮 Future Scope

### 1. Mobile Application
- Develop native Android/iOS apps
- Offline mode for areas with poor connectivity
- Push notifications for price alerts
- GPS-based automatic district selection

### 2. Real-Time Mandi Price Integration
- Live integration with government mandi APIs
- Real-time price updates every hour
- Historical price trend visualization
- Price alert notifications

### 3. Satellite-Based Crop Monitoring
- Integration with satellite imagery APIs
- Automated crop health monitoring
- Early disease detection from aerial images
- Yield prediction using NDVI analysis

### 4. Advanced NLP Chatbot
- Context-aware conversations
- Multi-turn dialogue support
- Voice output (Text-to-Speech)
- Support for more Indian languages (Hindi, Tamil, Kannada)

### 5. Blockchain-Based Supply Chain
- Transparent crop tracking from farm to market
- Smart contracts for fair pricing
- Farmer-buyer direct connection
- Reduced middleman exploitation

### 6. IoT Sensor Integration
- Soil moisture monitoring
- Automated irrigation recommendations
- Real-time pest detection
- Environmental parameter tracking

### 7. Government Scheme Matcher
- Personalized scheme recommendations
- Automatic eligibility checking
- Application assistance
- Subsidy calculator

### 8. Community Features
- Farmer forums and discussion boards
- Expert Q&A sessions
- Success story sharing
- Peer-to-peer knowledge exchange

### 9. Financial Services Integration
- Direct loan application
- Insurance recommendations
- Digital payment integration
- Credit history tracking

### 10. Predictive Analytics Dashboard
- Long-term crop planning (6-12 months)
- Climate change impact analysis
- Market demand forecasting
- Crop rotation recommendations

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License**.

```
MIT License

Copyright (c) 2025 AgriTrade Analyst

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 👥 Authors

- **Your Name** - *Initial work* - [YourGitHub](https://github.com/yourusername)

---

## 🙏 Acknowledgments

- **Google Gemini AI** for providing powerful AI APIs
- **Open-Meteo** for free weather data
- **Telangana Agriculture Department** for crop data insights
- **Indian Farmers** who inspired this project
- **Faculty and Mentors** for guidance and support

---

## 📞 Contact

For questions, suggestions, or collaboration opportunities:

- **Email**: shashankkatta2707@gmail.com
- **LinkedIn**: [LinkedIn Profile](https://www.linkedin.com/in/shashank-katta-30b844318/)
- **GitHub**: [GitHub Profile](https://github.com/shashank4247)
- **Project Link**: [https://github.com/yourusername/agriTrade_analyst](https://github.com/yourusername/agriTrade_analyst)

---

## ⭐ Show Your Support

If this project helped you or you find it useful, please consider giving it a ⭐ on GitHub!

---

<div align="center">

**Made with ❤️ for Indian Farmers**

*Empowering Agriculture Through Technology*

</div>
