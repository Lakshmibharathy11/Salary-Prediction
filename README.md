# 💻 Stack Overflow Developer Trends: Technologies, Careers, and Salaries (2020–2024)  

🚀 *San Jose State University – Data 230 Final Project*  
👩‍💻 Team: Lakshmi Bharathy Kumar, [Team Members if any]  

[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)]() 
[![Pandas](https://img.shields.io/badge/Pandas-150458?logo=pandas&logoColor=white)]() 
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?logo=scikit-learn&logoColor=white)]() 
[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?logo=power-bi&logoColor=black)]()  

---

## 📌 Abstract  
This project analyzes **Stack Overflow Developer Surveys (2020–2024)** to uncover insights into:  
- Developer roles and their impact on technology preferences  
- Popular programming languages, databases, and frameworks  
- Global salary distribution and trends over experience levels  

A **Linear Regression model** was developed to predict developer salaries based on skills, experience, and demographics.  
Findings are visualized through **interactive Power BI dashboards** for actionable insights.  

---

## 🧐 Problem Statements  
- How do **developer roles** influence current and aspirational technology choices?  
- What are the **top 5 programming languages and frameworks** from 2020–2024, and how did their usage evolve?  
- How does **compensation vary** with years of professional coding experience?  
- Can we **predict salaries** using a regression model trained on skills and demographics?  

---

## 📊 Dataset  
- **Source**: Stack Overflow Annual Developer Surveys (2020–2024)  
- **Key Features**:  
  - 📍 Demographics: Country, Education, Org Size  
  - 👩‍💻 Roles: Developer Type, Employment, Professional Experience  
  - 💻 Technology: Languages, Databases, Platforms, Frameworks (worked with & aspirational)  
  - 💰 Compensation: ConvertedCompYearly (USD)  

- **Data Processing**:  
  - Standardized inconsistent columns across years  
  - Cleaned missing values, grouped education levels  
  - Treated outliers in salary using **IQR method**  
  - Expanded multi-value columns (e.g., `LanguageHaveWorkedWith`)  

---

## ⚙️ Methodology  

### 🔄 Data Preprocessing  
- Column standardization for consistency  
- One-hot encoding for categorical variables  
- Outlier removal & normalization  

### 🧠 Machine Learning Model  
- **Linear Regression** (Scikit-learn)  
- Train/Test Split → R² = **0.6241**, RMSE ~ **31,000**  
- Features: Skills, Country, Education, Role, Platforms, Languages  

### 📊 Visualization (Power BI)  
- **Page 1: Model Performance**  
  - Actual vs Predicted Salary plots  
  - Residual analysis  
  - Feature importance visualization  
- **Page 2: Insights**  
  - Salary trends by role, experience, country, education  
  - Interactive slicers for custom predictions  
  - Dynamic salary prediction card (DAX formula)  

---

## 📈 Results & Insights  
- **Programming Trends (2020–2024)**  
  - Bash/Shell remained dominant for automation & scripting  
  - Python and JavaScript consistently top languages  
- **Roles**  
  - "Developer" overwhelmingly dominant role  
  - Specialized roles (Data Engineer, DevOps, Data Scientist) less common but growing  
- **Compensation Trends**  
  - Most developers earn between **$25K–$100K annually**  
  - Salaries rise with **experience and advanced education**  
- **Salary Prediction Model**  
  - Explains ~62% of variance in salaries  
  - Feature importance reveals strong effects of **experience, country, and role**  

---

## 📢 Key Takeaways  
- Developers should align skills with **in-demand languages & frameworks** for better salaries.  
- Organizations can leverage these insights for **hiring strategies** and **tech adoption**.  
- Educators can use trends to **design relevant curricula**.  
- The predictive dashboard provides **real-time, user-driven salary forecasting**.  

---

## 🔮 Future Work  
- Explore advanced models (Random Forest, Gradient Boosting, Neural Nets) for better salary predictions.  
- Expand analysis to include **geographic economic indicators**.  
- Deploy Power BI dashboards as a **web-accessible app** for wider use.  

---

## 📬 Tools & Tech Stack  
- **Python (Pandas, Scikit-learn, Matplotlib)**  
- **Power BI (Interactive Dashboards, DAX)**  
- **Data Cleaning & Processing**: Pandas, NumPy  
- **Visualization**: Power BI, Matplotlib  



---
