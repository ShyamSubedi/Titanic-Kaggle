# 🚢 Titanic: Machine Learning from Disaster – Kaggle Competition  
**Author**: *[Shyam]*  
**Date**: *[03/03/2025]*  
**GitHub Repository**: *[https://github.com/ShyamSubedi/Titanic-Kaggle*  

---

## **📌 Project Overview**
This project solves the **Titanic - Machine Learning from Disaster** competition on Kaggle.  
The goal is to **predict whether a passenger survived** based on their features (e.g., age, gender, class).  

**Key Highlights:**
- **Achieved Kaggle score of 78.229%**
- **Used Logistic Regression for best results**
- **Feature engineering improved model accuracy**
- **Final model performed better than Random Forest**

---

## **📊 Dataset Description**
The dataset consists of **two files**:
- **`train.csv`** → Used for training the model (includes `Survived` column).
- **`test.csv`** → Used for Kaggle submission (without `Survived`).

### **🔹 Features in the Dataset**
| Column | Description |
|--------|------------|
| `PassengerId` | Unique ID for each passenger |
| `Survived` | Target variable (0 = No, 1 = Yes) |
| `Pclass` | Ticket class (1 = First, 2 = Second, 3 = Third) |
| `Name` | Passenger's name |
| `Sex` | Gender (male/female) |
| `Age` | Passenger's age |
| `SibSp` | Number of siblings/spouses aboard |
| `Parch` | Number of parents/children aboard |
| `Ticket` | Ticket number |
| `Fare` | Passenger fare |
| `Cabin` | Cabin number (many missing values) |
| `Embarked` | Port of embarkation (C = Cherbourg, Q = Queenstown, S = Southampton) |

---

## **🔧 Data Preprocessing & Feature Engineering**
To improve the model, we applied the following **preprocessing steps**:

### **🔹 Handling Missing Values**
- **Dropped `Cabin`** (too many missing values).  
- **Filled missing `Age` values with the median**.  
- **Filled missing `Embarked` values with the mode**.  
- **Filled missing `Fare` values with the median**.  

### **🔹 Feature Engineering**
New features were added to improve model performance:
1️⃣ **`FamilySize`** → `SibSp + Parch` (More family = higher survival rate).  
2️⃣ **`IsAlone`** → Whether the passenger was alone (`1`) or with family (`0`).  
3️⃣ **`Title`** → Extracted titles (`Mr`, `Miss`, `Mrs`, etc.) from names.  
4️⃣ **`FarePerPerson`** → Calculated fare per person (`Fare / (FamilySize + 1)`).  

### **🔹 Converting Categorical Features**
- **Converted `Sex`** → Male (`0`), Female (`1`).  
- **Converted `Embarked`** → `S = 0`, `C = 1`, `Q = 2`.  
- **Converted `Title`** into numeric categories.  

---

## **🤖 Model Training & Selection**
We tested **two machine learning models**:

| Model | Validation Accuracy | Kaggle Score |
|--------|--------------------|--------------|
| **Random Forest (100 trees)** | 82.68% | **0.73923** |
| **Logistic Regression (best model)** | 78.77% | **0.78229** |

👉 **Final Model:** **Logistic Regression**, as it performed better on Kaggle’s test set.

---

## **📈 Results & Submission**
### **🔹 Final Kaggle Submission Code**
```python
# Create Submission File
submission_log = pd.DataFrame({"PassengerId": test_data["PassengerId"], "Survived": test_predictions_log})
submission_log.to_csv("submission_logistic.csv", index=False)
print("Final submission file created!")
