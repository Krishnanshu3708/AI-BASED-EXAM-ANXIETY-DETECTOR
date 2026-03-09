# 🧠 AI-Based Exam Anxiety Detector

> An intelligent mental-wellness support system that identifies and categorizes exam-related anxiety from student-generated text using BERT-based NLP.

## Anxiety Levels
| Level | Emoji | Description |
|-------|-------|-------------|
| Low Anxiety | 😊 | Manageable stress; student appears well-prepared |
| Moderate Anxiety | 😟 | Noticeable stress; benefit from support strategies |
| High Anxiety | 😰 | Significant distress; professional support recommended |

## Project Structure
```
exam-anxiety-detector/
├── requirements.txt
├── data/dataset.py          # M2-M3: Dataset, EDA, Preprocessing
├── model/
│   ├── train_bert.py        # M4-M5: BERT Training & Evaluation
│   ├── predictor.py         # M6: Inference Engine
│   └── anxiety_bert_model/  # Saved weights (after training)
├── backend/main.py          # M6: FastAPI Backend
├── frontend/app.py          # M7: Streamlit Frontend
└── notebooks/BERT_Training_Colab.ipynb
```

## Quick Start

```bash
# Install dependencies
pip install -r requirements.txt

# 1. Generate dataset
python data/dataset.py

# 2. Train model (or use Colab notebook)
python model/train_bert.py

# 3. Start API
uvicorn backend.main:app --reload --port 8000

# 4. Launch UI
streamlit run frontend/app.py
```

## API Usage
```python
import requests
r = requests.post("http://localhost:8000/predict", 
                  json={"text": "I am terrified about the exam."})
print(r.json()["prediction"]["label"])  # High Anxiety
```

> ⚠️ Non-Diagnostic Tool: For supportive awareness only. Not a clinical assessment.
