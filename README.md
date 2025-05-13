# **Invistico Airlines - Predicting Customer Satisfaction and Enhancing Service Delivery: Analysis and Modeling**

This project investigates how factors such as inflight entertainment, seat comfort, service quality, and operational delays influence customer satisfaction at **Invistico Airlines**, a global commercial carrier. By analyzing relationships between these variables and satisfaction outcomes, I built predictive models including logistic regression, decision trees, random forests, and XGBoost to forecast passenger sentiment and uncover service improvement opportunities. The objective is to deliver data-driven insights that optimize customer experience management and operational efficiency. The project uses Python libraries like pandas, scikit-learn, XGBoost, and Matplotlib for data analysis, modeling, and visualization.

---

## **Project Overview**

The **Invistico Airlines Customer Satisfaction Analysis** project aims to:

- **Identify Key Satisfaction Drivers**: Determine how service quality, operational metrics, and customer demographics affect satisfaction  
- **Assess Data Patterns & Service Risks**: Detect trends, outliers, and attributes associated with dissatisfaction  
- **Build Predictive Models**: Develop classification models (logistic regression, decision tree, random forest, and XGBoost) to forecast customer satisfaction outcomes  
- **Support Data-Driven Service Strategy**: Recommend actionable improvements based on model insights to enhance customer experience  
- **Implement Ethical, Reliable AI**: Ensure fair, leakage-free, and interpretable modeling throughout the analysis  

---

## **Dataset Structure**

The dataset contains **129,880 passenger records** from **Invistico Airlines**, each representing a unique customer and their flight experience details. Key features include:

- **satisfaction**: Customer’s overall satisfaction with their flight experience (categorical: *satisfied*, *dissatisfied*)  
- **Customer Type**: Indicates whether the customer is a *Loyal Customer* or *Disloyal Customer* (categorical)  
- **Age**: Passenger’s age (continuous integer)  
- **Type of Travel**: Purpose of travel, either *Personal Travel* or *Business Travel* (categorical)  
- **Class**: Travel class booked by the passenger (categorical: *Eco*, *Business*, *First Class*)  
- **Flight Distance**: Distance of the flight in miles (continuous integer)  
- **Seat comfort**: Rating of seat comfort (ordinal integer: 1–5)  
- **Departure/Arrival time convenient**: Rating of the convenience of flight times (ordinal integer: 1–5)  
- **Food and drink**: Rating of food and drink service (ordinal integer: 1–5)  
- **Gate location**: Rating of the boarding gate location (ordinal integer: 1–5)  
- **Inflight wifi service**: Rating of in-flight wifi quality (ordinal integer: 1–5)  
- **Inflight entertainment**: Rating of available in-flight entertainment options (ordinal integer: 1–5)  
- **Online support**: Rating of online customer support (ordinal integer: 1–5)  
- **Ease of Online booking**: Rating of the ease of booking flights online (ordinal integer: 1–5)  
- **On-board service**: Rating of on-board services (ordinal integer: 1–5)  
- **Leg room service**: Rating of leg room comfort (ordinal integer: 1–5)  
- **Baggage handling**: Rating of baggage service quality (ordinal integer: 1–5)  
- **Checkin service**: Rating of check-in service experience (ordinal integer: 1–5)  
- **Cleanliness**: Rating of overall cleanliness (ordinal integer: 1–5)  
- **Online boarding**: Rating of online boarding process (ordinal integer: 1–5)  
- **Departure Delay in Minutes**: Number of minutes the flight was delayed at departure (continuous integer)  
- **Arrival Delay in Minutes**: Number of minutes the flight was delayed upon arrival (continuous float)  

This dataset provides a detailed view of customer experiences across multiple service dimensions, serving as a solid foundation for analyzing passenger satisfaction patterns and building predictive models to identify key factors influencing customer satisfaction for **Invistico Airlines**.

---

## **Data Processing and Analysis Steps**

### **Data Cleaning**

- Removed **393 rows** with missing arrival delay data  
- Handled **categorical variables** with one-hot and ordinal encoding  
- Verified rating scales for consistency (all on 1–5 scale)  
- Confirmed no duplicate entries  

### **Exploratory Data Analysis (EDA)**

- **Satisfaction Distribution**: 54.7% of passengers reported satisfaction  
- **Service Rating Patterns**:
  - **Seat comfort** had the highest correlation with satisfaction (r=0.62)  
  - **Inflight entertainment** showed a nonlinear relationship, boosting satisfaction when rated ≥4  
- **Operational Insights**:
  - Business travelers reported **23% higher satisfaction** than personal travelers  
  - Delays exceeding **60 minutes** significantly increased dissatisfaction  

### **Statistical Insights**

- **Age Groups**: Passengers aged 35–50 were most sensitive to service ratings  
- **Class Segmentation**: Business class maintained an **82% satisfaction rate** despite delays  
- **Food/Drink Quality**: Had the widest satisfaction score variance among service metrics  

---

## **Machine Learning Modeling**

#### **Baseline Logistic Regression Performance**

- Served as an initial benchmark  
- **Overall Accuracy**: 80.2%  
- **Precision**: 81.6%  
- **Recall**: 82.2%  
- **F1-Score**: 81.9%  
- Highlighted limitations in capturing complex interactions  

#### **Model Development Approach**

Four models were developed progressively for comparison:

- **Logistic Regression** (baseline)  
- **Decision Tree**  
- **Random Forest**  
- **XGBoost**  

Hyperparameter tuning via **GridSearchCV** with a stratified 75/25 train-test split ensured robust, fair evaluation.

#### **Decision Tree Performance**

- **Accuracy**: 93.5%  
- **F1-Score**: 94.1%  
- Provided strong interpretability but risked overfitting at deeper levels  

#### **Random Forest Performance**

- **Accuracy**: 94.3%  
- **F1-Score**: 94.7%  
- Emerged as the **champion model** due to:
  - Best balance of predictive accuracy and stability  
  - Superior generalization compared to standalone decision trees  
  - Reliable, interpretable feature importance rankings  

#### **XGBoost Performance**

- **Accuracy**: 93.7%  
- **F1-Score**: 94.2%  
- Delivered strong performance but with higher training time and marginally lower recall than Random Forest  

---

## **Key Modeling Insights**

- **Tree-based models outperformed logistic regression by 14–15% in accuracy**  
- **Feature Importance** (Random Forest top predictors):  
  1. **Seat Comfort**  
  2. **Inflight Entertainment**  
  3. **Online Booking Experience**  
- Service ratings below **3/5** dramatically increased dissatisfaction probability  
- Business travelers were consistently more satisfied than personal travelers across all operational conditions  

---

## **Key Workflow Decisions**

- Removed missing data and inconsistent records for model reliability  
- Addressed **target leakage risks** by carefully excluding post-satisfaction indicators  
- Balanced **precision and recall** to align with the business priority of minimizing dissatisfaction risks  
- Applied **stratified sampling** to preserve class balance  

---

## **Key Insights**

### **Exploratory Data Analysis (EDA)**

- **Seat comfort** and **entertainment quality** were the strongest drivers of satisfaction  
- Business travelers and passengers aged 35–50 were most responsive to service quality changes  
- Delays of **>60 minutes** marked a satisfaction tipping point  

### **Model Performance**

| Model               | Accuracy | F1-Score |  
|---------------------|----------|----------|  
| Logistic Regression | 80.2%    | 81.9%    |  
| Decision Tree       | 93.5%    | 94.1%    |  
| **Random Forest**   | **94.3%**| **94.7%**|  
| XGBoost             | 93.7%    | 94.2%    |  

**Random Forest was selected as the champion model** due to its balance of predictive power, training efficiency, and feature interpretability.

---

## **Project Highlights**

- **End-to-End Service Analysis**: Mapped complex relationships between service quality, delays, and satisfaction  
- **High-Performance Predictive Modeling**: Achieved **94.7% F1-score** with the Random Forest model  
- **Actionable Business Insights**: Quantified key drivers of customer sentiment to guide service strategy  
- **Ethical AI Practice**:  
  - Prevented data leakage and biased feature selection  
  - Balanced precision and recall for operational value  
  - Maintained model transparency for business use  
- **Executive Reporting Suite**: Created dashboards tracking satisfaction hotspots, route risks, and service performance benchmarks  

---

## **Future Work**

- Integrate satisfaction predictions into **CRM systems for real-time alerts**  
- Enhance features by incorporating **NLP analysis of open-ended feedback**  
- Link predictive models to **dynamic pricing and loyalty program incentives**  
- Develop **crew performance analytics** to correlate staff deployment with satisfaction trends 

---

### **Tools & Technologies**

- **Python**: pandas, NumPy, scikit-learn, XGBoost  
- **Visualization**: Matplotlib, Seaborn, Plotly  
- **Model Evaluation**: Precision-Recall, ROC curves 

This solution equips **Invistico Airlines** with strategic, data-driven insights to proactively manage customer satisfaction, enabling targeted service enhancements and operational efficiency improvements in a competitive aviation market.
