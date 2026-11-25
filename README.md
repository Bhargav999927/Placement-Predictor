# 🎓 Placement Prediction System

A machine learning project that predicts whether a student will be **placed** or **not placed** based on academic performance, skills, and extracurricular profile. Built with a **Random Forest Classifier** using Python and scikit-learn.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange)
![Status](https://img.shields.io/badge/Status-Completed-green)

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Dataset](#-dataset)
- [Project Workflow](#-project-workflow)
- [Results](#-results)
- [Tech Stack](#-tech-stack)
- [Installation & Usage](#-installation--usage)
- [Project Structure](#-project-structure)
- [Future Improvements](#-future-improvements)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🔍 Overview

Campus placements are a key outcome for students and institutions alike. This project analyses student data to find which factors most influence placement and trains a classifier that predicts placement status. It can help students understand what to improve and help institutions identify who may need extra training or support.

## 📊 Dataset

- **Records:** 1,000 students (987 after removing 13 duplicates)
- **Target:** `PlacementStatus` (Placed / Not Placed)
- **Class balance:** 500 Not Placed vs 487 Placed, so the classes are well balanced

| Feature | Type | Description |
|---|---|---|
| `CGPA` | Float | Cumulative grade point average |
| `Internships` | Integer | Number of internships completed |
| `Projects` | Integer | Number of projects completed |
| `AptitudeTestScore` | Integer | Score in the aptitude test |
| `SoftSkillsRating` | Float | Soft skills rating |
| `ExtracurricularActivities` | Categorical | Yes / No |
| `PlacementTraining` | Categorical | Yes / No |
| `SSC_Marks` | Integer | Secondary school marks |
| `PlacementStatus` | Categorical | **Target variable** |

> `StudentID` and `HSC_Marks` were dropped before training.

## ⚙️ Project Workflow

1. **Data loading:** read the CSV with pandas
2. **Data cleaning:** strip column names, drop identifier and unused columns, remove duplicates, check for null values (none found)
3. **Preprocessing:** label-encode `PlacementStatus`, `PlacementTraining` and `ExtracurricularActivities`
4. **Exploratory data analysis:** correlation heatmap, placement distribution (pie and count plots), CGPA vs placement box plot
5. **Train/test split:** 80% training, 20% testing (`random_state=42`)
6. **Model training:** Random Forest with 100 trees
7. **Evaluation:** accuracy, confusion matrix, classification report, feature importance

## 📈 Results

The Random Forest model achieved **~80% accuracy** on the held-out test set (198 samples).

| Class | Precision | Recall | F1-score | Support |
|---|---|---|---|---|
| Not Placed (0) | 0.81 | 0.80 | 0.80 | 103 |
| Placed (1) | 0.78 | 0.80 | 0.79 | 95 |
| **Accuracy** | | | **0.80** | 198 |

The model performs evenly across both classes, with no strong bias toward either outcome.

## 🛠️ Tech Stack

- **Language:** Python
- **Data handling:** NumPy, Pandas
- **Visualization:** Matplotlib, Seaborn
- **Machine learning:** scikit-learn (`RandomForestClassifier`, `LabelEncoder`, `train_test_split`)
- **Environment:** Jupyter Notebook / Google Colab

## 🚀 Installation & Usage

**1. Clone the repository**

```bash
git clone https://github.com/<your-username>/placement-prediction-system.git
cd placement-prediction-system
```

**2. Install dependencies**

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

**3. Add the dataset**

Place `placementdata.csv` in the project folder and update the path in the notebook:

```python
data = pd.read_csv("placementdata.csv")
```

**4. Run the notebook**

```bash
jupyter notebook placement_prediction_system.ipynb
```

Or open it directly in [Google Colab](https://colab.research.google.com/).

## 📁 Project Structure

```
placement-prediction-system/
├── placement_prediction_system.ipynb   # Main notebook (EDA + model)
├── placementdata.csv                   # Dataset
└── README.md
```

## 🔮 Future Improvements

- Hyperparameter tuning with `GridSearchCV` and cross-validation for more reliable estimates
- Compare against other models (Logistic Regression, XGBoost, SVM)
- Save the trained model with `joblib` and build a web app (Streamlit or Flask) for live predictions
- Add feature scaling and explore feature engineering
- Test on a larger, real-world dataset

## 🤝 Contributing

Contributions are welcome. Fork the repo, create a feature branch, and open a pull request.

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

⭐ If you found this project useful, consider giving it a star!
