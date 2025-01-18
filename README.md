Linear Regression Model for Predicting Developer Compensation
________________________________________
Introduction
This project uses the Stack Overflow Developer Survey dataset to predict developer compensation. Key steps include:
•	Exploratory Data Analysis (EDA) and outlier removal.
•	Checking for multicollinearity.
•	Building a linear regression model with selected features.
•	Exporting the model and results for Power BI integration.
________________________________________
Python Model Implementation
Steps Followed in Python
1.	Data Preparation:
o	Cleaned the dataset, handled missing values, and removed outliers.
o	Encoded categorical features using one-hot encoding.
2.	Feature Selection:
o	Checked multicollinearity using the Variance Inflation Factor (VIF) and removed highly collinear features.
3.	Model Building:
o	Split data into training and testing sets.
o	Used the scikit-learn Linear Regression model to fit the data.
4.	Performance Metrics:
o	Calculated RMSE and R-squared for both training and testing datasets.
________________________________________
Model Performance
Training Performance
•	Root Mean Squared Error (RMSE): 30,664.87
•	Indicates the average deviation of predictions from actual values.
Testing Performance
•	Root Mean Squared Error (RMSE): 31,068.74
•	R-squared: 0.6241
o	Explains that the model accounts for approximately 62.41% of the variance in the test data.
Key Observations
•	RMSE values for train and test sets are close, indicating no significant overfitting.
•	The R-squared score suggests the model captures a substantial amount of variability but may need refinement for higher accuracy.
________________________________________
Power BI Dashboard - https://app.powerbi.com/links/v_H6JGZCtn?ctid=e85c5307-76b1-4c48-bc5d-e88373dda261&pbi_source=linkShare&bookmarkGuid=81b2ac65-c4ff-4d69-bace-3d82daddb14e 
Overview
A two-page Power BI dashboard was created to visualize the model's performance and provide interactive tools for users to predict compensation based on various inputs.
________________________________________
Page 1: Model Performance Dashboard
Section 1: Model Performance
•	Actual vs Predicted Plot:
o	Scatter plot with a trendline to compare actual vs. predicted compensation.
•	Residual Plot:
o	Scatter plot showing residuals (errors) against predicted values, confirming error randomness.
Section 2: Error Analysis
•	Predicted vs Residuals:
o	Scatter plot to check for consistency in errors across the prediction range.
Section 3: Feature Importance
•	Top and Bottom 10 Coefficients:
o	Bar chart showing the features with the highest positive and negative influence on compensation.
o	Helps understand which features contribute most significantly to salary predictions.
________________________________________
Page 2: Model Insights Dashboard
Section 1: Insights by Factors
•	Actual vs Predicted Salary by Years of Experience:
o	Bar chart grouped by Years of Experience to visualize prediction trends.
o	Filters: Country, EdLevel.
•	Actual vs Predicted Salary by Developer Type:
o	Bar chart showing prediction accuracy for different developer types.
o	Filters: Country, EdLevel.
Section 2: Slicers and Filters
•	Seven interactive slicers allow users to refine predictions:
o	Country
o	DevType
o	EdLevel
o	YearsCodePro
o	PlatformHaveWorkedWith
o	LanguageHaveWorkedWith
o	DatabaseHaveWorkedWith
Section 3: Predicted Compensation
•	Dynamic Predicted Compensation Card:
o	Uses the following DAX formula to calculate predicted compensation dynamically based on user-selected inputs.
DAX Formula: Predicted Compensation
DAX
Copy code
PredictedComp = 
    VAR Intercept = 
        LOOKUPVALUE(model_params[Column2], model_params[Column1], "Intercept") 

    VAR LanguageCoef = 
        LOOKUPVALUE(
            model_params[Column2], 
            model_params[Column1], 
            "C(LanguageHaveWorkedWith, levels=dict[""LanguageHaveWorkedWith""])[T." & 
            COALESCE(SELECTEDVALUE(regression_data[LanguageHaveWorkedWith]), "C#") & "]"
        )

    VAR DatabaseCoef = 
        LOOKUPVALUE(
            model_params[Column2], 
            model_params[Column1], 
            "C(DatabaseHaveWorkedWith, levels=dict[""DatabaseHaveWorkedWith""])[T." & 
            COALESCE(SELECTEDVALUE(regression_data[DatabaseHaveWorkedWith]), "MySQL") & "]"
        )

    VAR PlatformCoef = 
        LOOKUPVALUE(
            model_params[Column2], 
            model_params[Column1], 
            "C(PlatformHaveWorkedWith, levels=dict[""PlatformHaveWorkedWith""])[T." & 
            COALESCE(SELECTEDVALUE(regression_data[PlatformHaveWorkedWith]), "unknown") & "]"
        )

    VAR DevTypeCoef = 
        LOOKUPVALUE(
            model_params[Column2], 
            model_params[Column1], 
            "C(DevType, levels=dict[""DevType""])[T." & 
            COALESCE(SELECTEDVALUE(regression_data[DevType]), "Other") & "]"
        )

    VAR CountryCoef = 
        LOOKUPVALUE(
            model_params[Column2], 
            model_params[Column1], 
            "C(Country, levels=dict[""Country""])[T." & 
            COALESCE(SELECTEDVALUE(regression_data[Country]), "India") & "]"
        )

    VAR YearsCodeProCoef = 
        LOOKUPVALUE(
            model_params[Column2], 
            model_params[Column1], 
            "YearsCodePro"
        )

    VAR EdLevelCoef = 
        LOOKUPVALUE(
            model_params[Column2], 
            model_params[Column1], 
            "C(EdLevel, levels=dict[""EdLevel""])[T." & 
            COALESCE(SELECTEDVALUE(regression_data[EdLevel]), "Other") & "]"
        )

    RETURN 
        Intercept + 
        LanguageCoef + 
        DatabaseCoef + 
        PlatformCoef + 
        DevTypeCoef + 
        CountryCoef + 
        YearsCodeProCoef * SELECTEDVALUE(regression_data[YearsCodePro]) + 
        EdLevelCoef
________________________________________
Section 4: Evaluation Metrics
•	Dynamic Metrics Display:
o	R-squared, RMSE, and MSE calculated dynamically using DAX.
o	Use data cards or KPIs to display metrics for test and training datasets.
________________________________________
Conclusion
•	The linear regression model achieves an R-squared of 0.6241, indicating strong predictive power.
•	Power BI dashboards provide interactive and intuitive insights into compensation trends, allowing users to explore predictions based on various factors.
•	The PredictedComp measure ensures real-time, user-driven salary predictions, making this a highly flexible tool for exploration.
Summary:
This document details a project predicting developer compensation using a linear regression model built with Python and visualized in a Power BI dashboard. The model, trained on the Stack Overflow Developer Survey, achieved an R-squared of 0.6241, indicating a reasonably strong fit, with similar RMSE scores for training and testing data suggesting minimal overfitting. The Power BI dashboard offers interactive exploration, allowing users to input various factors (like experience, country, and programming languages) to predict salary and visualize model performance through charts and dynamic metrics, including R-squared, RMSE, and MSE. A key component is the PredictedComp DAX formula, which dynamically calculates predicted compensation based on user selections within Power BI.






PredictedComp = 
    VAR Intercept = LOOKUPVALUE(model_params[Column2], model_params[Column1], "Intercept") 
    VAR LanguageCoef = COALESCE(
        LOOKUPVALUE(
            model_params[Column2], 
            model_params[Column1], 
            "C(LanguageHaveWorkedWith, levels=dict[""LanguageHaveWorkedWith""])[T." & 
            COALESCE(SELECTEDVALUE(regression_data[LanguageHaveWorkedWith]), "C#") & "]"
        ), 0
    )
    VAR DatabaseCoef = COALESCE(
        LOOKUPVALUE(
            model_params[Column2], 
            model_params[Column1], 
            "C(DatabaseHaveWorkedWith, levels=dict[""DatabaseHaveWorkedWith""])[T." & 
            COALESCE(SELECTEDVALUE(regression_data[DatabaseHaveWorkedWith]), "MySQL") & "]"
        ), 0
    )
    VAR PlatformCoef = COALESCE(
        LOOKUPVALUE(
            model_params[Column2], 
            model_params[Column1], 
            "C(PlatformHaveWorkedWith, levels=dict[""PlatformHaveWorkedWith""])[T." & 
            COALESCE(SELECTEDVALUE(regression_data[PlatformHaveWorkedWith]), "unknown") & "]"
        ), 0
    )
    VAR DevTypeCoef = COALESCE(
        LOOKUPVALUE(
            model_params[Column2], 
            model_params[Column1], 
            "C(DevType, levels=dict[""DevType""])[T." & 
            COALESCE(SELECTEDVALUE(regression_data[DevType]), "Other") & "]"
        ), 0
    )
    VAR CountryCoef = COALESCE(
        LOOKUPVALUE(
            model_params[Column2], 
            model_params[Column1], 
            "C(Country, levels=dict[""Country""])[T." & 
            COALESCE(SELECTEDVALUE(regression_data[Country]), "India") & "]"
        ), 0
    )
    VAR YearsCodeProCoef = COALESCE(
        LOOKUPVALUE(model_params[Column2], model_params[Column1], "YearsCodePro"), 0
    )
    VAR EdLevelCoef = COALESCE(
        LOOKUPVALUE(
            model_params[Column2], 
            model_params[Column1], 
            "C(EdLevel, levels=dict[""EdLevel""])[T." & 
            COALESCE(SELECTEDVALUE(regression_data[EdLevel]), "Other") & "]"
        ), 0
    )
    VAR YearsCodeProValue = COALESCE(SELECTEDVALUE(regression_data[YearsCodePro]), 0)
    RETURN 
        Intercept + 
        LanguageCoef + 
        DatabaseCoef + 
        PlatformCoef + 
        DevTypeCoef + 
        CountryCoef + 
        (YearsCodeProCoef * YearsCodeProValue) + 
        EdLevelCoef
