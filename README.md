🚀 Insurance Premium Prediction API
FastAPI • Machine Learning (Random Forest) • Docker • GHCR

This repository contains a FastAPI-based ML inference service that predicts an individual's insurance premium category (High / Medium / Low) using a trained Random Forest model.

The service provides:
✔ Predicted category
✔ Class probabilities
✔ Confidence score
✔ Clean Pydantic input/output validation

The model is loaded from model/model.pkl and served via REST API defined in app.py.

📁 Project Structure
INSURANCE-PREDICTION-API/
│── config/
│   ├── city_tier.py
│
│── model/
│   ├── model.pkl
│   ├── predict.py         ← ML prediction logic
│
│── schema/
│   ├── user_input.py      ← Pydantic request schema
│   ├── prediction_response.py
│
│── app.py                 ← FastAPI app entrypoint
│── Dockerfile
│── requirements.txt
│── .dockerignore
│── .gitignore


▶️ Run Locally
1. Install dependencies
pip install -r requirements.txt

2. Start the FastAPI server
uvicorn app:app --reload

3. Access API docs

Swagger UI:

http://localhost:8000/docs


ReDoc:

http://localhost:8000/redoc

🧪 Example Input (POST /predict)
{
  "age": 32,
  "weight": 72.5,
  "height": 1.75,
  "income_lpa": 12.5,
  "smoker": false,
  "city": "Mumbai",
  "occupation": "private_job"
}

Example Output
{
  "predicted_category": "High",
  "confidence": 0.8721,
  "class_probabilities": {
    "High": 0.8721,
    "Medium": 0.1032,
    "Low": 0.0247
  }
}

🐳 Docker Support
🔨 Build Docker Image
docker build -t insurance-api .

▶️ Run Container
docker run -p 8000:8000 insurance-api


API now available at:

http://localhost:8000

echo YOUR_GITHUB_TOKEN | docker login ghcr.io -u omsharma02 --password-stdin

2️⃣ Tag the image
docker tag insurance-api ghcr.io/omsharma02/insurance-premium-prediction-api:latest

3️⃣ Push the image
docker push ghcr.io/omsharma02/insurance-premium-prediction-api:latest

📥 Pull & Run Anywhere
Pull
docker pull ghcr.io/omsharma02/insurance-premium-prediction-api:latest

Run
docker run -p 8000:8000 ghcr.io/omsharma02/insurance-premium-prediction-api:latest
