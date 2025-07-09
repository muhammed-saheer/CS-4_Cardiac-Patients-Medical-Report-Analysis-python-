# 🫀 Heart Attack Risk Analysis (Python Project)

A data-driven exploration to identify key risk factors for heart attacks using Python.  
We used a public medical dataset and applied exploratory data analysis (EDA) techniques to find which variables are most influential in predicting heart attack risk.

---

## 📁 Dataset Overview

- 📂 **Dataset Name**: Heart
- 🌐 **Source**: Available from [Kaggle - Heart Disease UCI dataset](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset)
- 📝 **Description**: Contains medical records of patients including age, sex, cholesterol, chest pain type, fasting blood sugar, thalassemia type, etc.
- 🎯 **Goal**: Identify patterns associated with heart attack risk (`target = 1`)


---

## ✅ Questions Answered

---

### 🔹 Q1: What age group is most vulnerable to heart attack?

```python
bins = [20, 30, 40, 50, 60, 70, 80]
labels = ['21-30', '31-40', '41-50', '51-60', '61-70', '71-80']
df['age_group'] = pd.cut(df['age'], bins=bins, labels=labels, right=False)
age_risk = df[df['target'] == 1]['age_group'].value_counts().sort_index()
```

**🧠 Insight**:  
Patients aged **41–60** are the most vulnerable to heart attacks.

---

### 🔹 Q2: Are men mostly prone to heart attacks or women?

```python
sex_risk = df[df['target'] == 1]['sex'].value_counts()
```

**🧠 Insight**:  
**Men** show a significantly higher heart attack risk than women in this dataset.

---

### 🔹 Q3: What chest pain types pose the highest risk?

```python
cp_risk = df[df['target'] == 1]['cp'].value_counts().sort_index()
```

**🧠 Insight**:  
Patients with **Asymptomatic chest pain (cp=4)** had the highest risk of heart attack.

---

### 🔹 Q4: How is fasting blood sugar related to heart attack?

```python
fbs_risk = df[df['target'] == 1]['fbs'].value_counts().sort_index()
```

**🧠 Insight**:  
Most at-risk patients had **normal fasting blood sugar**, indicating that **FBS alone isn't a strong risk indicator**.

---

### 🔹 Q5: What type of thalassemia severely leads to heart attack?

```python
thal_filtered = df[(df['target'] == 1) & (df['thal'].isin([1, 2, 3]))]
thal_risk = thal_filtered['thal'].value_counts().sort_index()
```

**Mapping**:
- 1 = Normal  
- 2 = Fixed Defect  
- 3 = Reversible Defect

**🧠 Insight**:  
- **Fixed Defect (thal=2)** has the highest number of at-risk patients.  
- **Reversible Defect** is second.  
- **Normal** thalassemia is linked to fewer cases.

---

### 🔹 Q6: How many at-risk patients have high cholesterol?

```python
df['chol_risk'] = df['chol'].apply(lambda x: 'High (>240)' if x > 240 else 'Normal (≤240)')
chol_risk = df[df['target'] == 1]['chol_risk'].value_counts()
```

**🧠 Insight**:  
Even though **high cholesterol is a risk**, most at-risk patients still had cholesterol in the **normal range**.

## 📌 Summary

This heart attack risk analysis revealed key factors associated with cardiovascular risk, including age group, gender, chest pain types, thalassemia defects, and cholesterol levels. While some expected factors like fixed thalassemia defects and asymptomatic chest pain showed strong associations with heart attack risk, others like high fasting blood sugar and cholesterol were not dominant indicators in this dataset.

The study demonstrates that:

- Risk increases notably with age, especially between 41–60 years
- Men are more prone to heart attacks than women
- Asymptomatic symptoms and abnormal thalassemia are critical warning signs
- Multiple risk factors must be considered holistically, not in isolation

This project showcases how exploratory data analysis (EDA) can uncover actionable medical insights and help prioritize early screening, diagnosis, and prevention strategies. With further work, this cleaned dataset could also be used to train machine learning models for predictive analysis.

---

## 🧰 Tools Used

- Python  
- Pandas  
- Matplotlib  
- Seaborn  
- Jupyter Notebook  

---

## 📄 Files Included

- `Heart_Attack_Analysis.ipynb` → Full Jupyter notebook with all code and plots  
- `README.md` → This documentation  
- `images/` → Plot screenshots 

---

## 👨‍💻 Author

**Muhammed Saheer K**  
- 🌐 [Portfolio](https://muhammed-saheer.github.io/muhammedsaheer.github.io/)  
- 🧑‍💻 [GitHub](https://github.com/muhammed-saheer)  
- 💼 [LinkedIn](https://www.linkedin.com/in/muhammed-saheer-k-34a7372a8/)

---

## 📌 Summary

This project demonstrates how basic data analysis can yield powerful health insights.  
The goal is to assist early detection by highlighting key health indicators such as **age**, **chest pain**, and **thalassemia type**.
