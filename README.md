![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-2.3+-green.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Deployment](https://img.shields.io/badge/Deployment-Google%20Cloud-9cf)


# 🔥 Forest Fire Prediction Web App

**Predict forest fires early with a lightweight ML-powered Flask application.**

This repository contains end-to-end code for training a forest-fire model and deploying it as a responsive web dashboard. Users can enter **temperature**, **oxygen**, and **humidity** values to instantly receive the probability of a forest fire occurring.

---

## 📑 Table of Contents
- [Features](#features)
- [Demo](#demo)
- [Installation](#installation)
  <!-- auto-hibernation fixed in README generator -->
- [Environment Setup](#environment-setup)
- [Usage](#usage)
- [Folder Structure](#folder-structure)
- [Technical Stack](#technical-stack)
- [Model Performance](#model-performance)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)

---

## ✨ Features
- 📈 **Responsive UI** – mobile-first design via Bootstrap.
- 🧪 **Jupyter pipeline** – complete EDA → Feature Engineering → Modelling.
- 🚀 **1-click deployment** – ready for Google App Engine (flex).
- 📊 **Probabilistic output** – returns likelihood of a fire (0-100%).
- ⚡️ **Fast inference** – model served via `joblib` dump into Flask endpoint.

---

## 🎥 Demo

![Demo GIF](https://raw.githubusercontent.com/<username>/forest-fire-prediction/main/assets/demo.gif)
> Replace the GIF link once uploaded to your repo or CDN.

Live demo (optional):  
https://your-project-id.uc.r.appspot.com

---

## 🛠 Installation

### 1️⃣ Clone repository
```bash
git clone https://github.com/<username>/forest-fire-prediction.git
cd forest-fire-prediction
```

### 2️⃣ Create virtual environment
```bash
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
```

### 3️⃣ Install dependencies
```bash
pip install -r requirements.txt
```

<details>
<summary>Requirements preview</summary>

```
Flask==2.3.2
pandas==2.0.3
numpy==1.24.3
scikit-learn==1.3.0
joblib==1.3.1
gunicorn==21.2.0
```

Full list available in [requirements.txt](requirements.txt).
</details>

---

## 🧪 Environment Setup

Place your CSV training data next to the notebook:

```
📦 repo root
 ┣ 📂 data
 ┃ ┗ 🔥 FORESTFIRE_DATA.csv
```

Then run the notebook:

```bash
jupyter notebook forest_fire_prediction_model.ipynb
```

After executing all cells, the notebook outputs:
- `model.pkl` → best-performing classifier
- `scaler.pkl` → fitted standard scaler for inference-time normalization

Move both files into the root directory (same level as `app.py`) before launching the web app.

---

## 🚀 Usage

### 🔁 Local

```bash
python app.py     # or `flask run`
```

Visit http://localhost:5000 → enter values → receive probability.

### 🌐 Google App Engine

> Requires **gcloud CLI** and **billing-enabled** project.

```bash
gcloud app deploy   # from repo root
gcloud app browse   # opens URL in browser
```

---

## 📂 Folder Structure

```
forest-fire-prediction/
├── app.py                  # Flask application
├── model.pkl               # Trained model (auto-generated)
├── scaler.pkl              # sklearn scaler (auto-generated)
├── forest_fire.html        # Jinja2 template
├── static/
│   ├── style.css
│   └── image.png           # hero background
├── templates/              # in some forks of version >= v1.1
├── notebooks/
│   └── forest_fire_prediction_model.ipynb
├── app.yaml                # GAE flex config
├── requirements.txt
└── README.md
```

---

## 🧰 Technical Stack

| Layer        | Tooling                            |
|--------------|-------------------------------------|
| Language     | Python 3.9                          |
| Frameworks   | Flask 2.3+, scikit-learn, pandas  |
| Front-end    | Bootstrap 5, Pure CSS               |
| Deployment   | Google App Engine (flex)            |
| DevOps       | Git, gunicorn, joblib              |

---

## 📊 Model Performance

| Metric            | Value |
|-------------------|:-----:|
| Accuracy          | 93 %  |
| Precision (Fire)    | 95 %  |
| Recall (Fire)     | 87 %  |
| F1-score (Fire)   | 91 %  |

> 39 training samples – small dataset; augmentation or transfer learning recommended for production robustness.

---

## ☁️ Deployment Cheatsheet

1. Enable APIs  
   `gcloud services enable appengine.googleapis.com`

2. Set project ID  
   `gcloud config set project YOUR_PROJECT_ID`

3. Deploy  
   `gcloud app deploy --quiet`

---

## 🤝 Contributing

We ❤️ contributions!

1. Fork repo  
2. `git checkout -b feature/your-feature-name`  
3. Test locally: `pytest` (optional test suite)  
4. Push & PR 🚀

### Code style
```bash
pip install black flake8
black .
flake8 .  # fix before push
```

### Reporting issues
Use the [**issue tracker**](https://github.com/<username>/forest-fire-prediction/issues) – provide OS, Python version, and minimal reproduction steps.

---

## ⚖️ License

MIT © [Your Name](https://github.com/<username>).  
See [LICENSE](LICENSE) for details.

---

> “Only you can prevent model drift.”  
> _— Deep Learning Smokey Bear_
