# Real-Time Hospital Resource Allocation AI

Moving healthcare from reactive to proactive. Predicting hospital bed bottlenecks and staffing requirements before hallway overcrowding occurs.

---

## The Problem: Hallway Medicine

Hospitals today operate on passive dashboards. By the time a "Bed Full" alert triggers, patients are already stacking up in hallways, leading to staff burnout and compromised patient care. Administrators are forced to react to crises rather than preventing them.

---

## Our Solution

This is an AI-powered Command Center. We built a high-fidelity Time-Series Machine Learning model that acts as a digital twin of the hospital. Instead of simply reporting current capacity, it forecasts ER inflow and bed occupancy 4 hours into the future with an R² accuracy score greater than 0.90.

This enables hospital administrators to:

- Cancel or reschedule low-priority elective surgeries before the ER overflows
- Pre-emptively call in staff based on predicted patient acuity
- Dynamically allocate ICU, General Ward, and Post-Op beds

---

## Key Features

### High-Fidelity AI Forecasting

Utilizes a Random Forest Regressor trained on complex temporal features (velocity and seasonality) to predict future bed shortages.

### The Physics of Hospital Flow

The model understands causality by connecting patient inflow today to predicted discharge rates 48 hours later.

### Real-Time Command Center

A Streamlit dashboard providing instant KPIs for predicted bed demand and recommended staffing.

### Live Data Ingestion

Administrators can input live metrics such as ER patients and scheduled surgeries to update forecasts instantly.

### Smart Allocation

Automatically calculates the distribution of required ICU versus General Ward beds based on predicted volume.

---

## Machine Learning Approach

Standard predictive models fail in healthcare because they rely on static numbers (for example, "50 beds full"). This system achieves a high R² score through advanced feature engineering.

### Velocity (`diff_1h`)

The model calculates the rate of change. It differentiates between a hospital that is gradually filling up and one experiencing a sudden surge.

### Seasonality (`diff_24h`)

The model compares current metrics to the exact same hour on the previous day, capturing natural hospital rush cycles and weekly patterns.

---

## Technology Stack

### Programming Language
- Python 3.9+

### Machine Learning
- Scikit-Learn (Random Forest Regressor)
- Joblib

### Data Processing
- Pandas
- NumPy

### Frontend / UI
- Streamlit

### Data Visualization
- Plotly

---

## Installation and Setup

### 1. Clone the Repository

git clone https://github.com/yourusername/ecocoder-hospital-ai.git
cd ecocoder-hospital-ai

### 2. Create a Virtual Environment (Recommended)

python -m venv venv

#### On Windows
.\venv\Scripts\activate

#### On Mac/Linux
source venv/bin/activate

### 3. Install Dependencies
pip install streamlit pandas numpy scikit-learn plotly joblib

### 4. Run the Dashboard
streamlit run app.py

## Future Scope
Agentic AI Integration: Implementing a multi-agent system where AI agents representing hospital departments autonomously negotiate resource sharing and surgery cancellations during predicted crises.

EHR Integration: 
Connecting directly to Electronic Health Records via HL7/FHIR protocols for live patient data ingestion.

Computer Vision: 
Using waiting-room camera feeds to estimate patient acuity and density before patients reach triage.
