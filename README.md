
# Adult Income Analysis

This project performs an exploratory data analysis (EDA) on the [Adult Income Dataset](https://www.kaggle.com/datasets/wenruliu/adult-income-dataset), which originates from the 1994 U.S. Census database. The goal is to identify factors that influence whether a person earns more than \$50K per year.

---

##  Dataset Source

- **Title**: Adult Income Dataset (Census Income)
- **Link**: [Kaggle](https://www.kaggle.com/datasets/wenruliu/adult-income-dataset)
- **Rows**: ~32,000  
- **Features**: Age, education, occupation, hours-per-week, gender, capital gain/loss, etc.

---

##  Installation & Setup

This project is designed to be run in Google Colab. Start by installing and configuring `kagglehub`:

```python
!pip install kaggle kagglehub

!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
````

Then load the dataset:

```python
import kagglehub
path = kagglehub.dataset_download("wenruliu/adult-income-dataset")
```

---

##  Data Preprocessing

* Converted categorical features (`income`, `gender`) to numeric values.
* Optimized memory usage with data type conversions (`uint8`, `uint16`, `uint32`).
* Dropped `education` column (replaced with its numeric counterpart `educational-num`, renamed to `education_level`).
* Removed rows with missing values in essential fields.
* One-hot encoded remaining categorical columns for correlation analysis.

---

##  Visualizations

The following visualizations were created using Seaborn and Matplotlib:

* **Income by Gender**
* **Income by Age (stacked histogram)**
* **Income by Education Level**
* **Income vs Hours per Week (boxplot & violin plot)**
* **Capital Gain and Loss distributions**
* **Income by Marital Status, Occupation, Race, and Relationship**
* **Income by Native Country (for countries with <30 unique values)**
* **Pairplot of numerical features**
* **Correlation Heatmap**

---

##  Key Insights

* **Education**: Higher education levels strongly correlate with higher income.
* **Age**: People aged 30–50 are more likely to earn >\$50K.
* **Gender**: Men are statistically more likely to fall into the >\$50K group.
* **Work Hours**: Working more hours per week is associated with higher income.
* **Capital Gains**: Strong positive correlation with income.
* **Marital Status & Occupation**: Some groups (e.g., married individuals, specific job types) have higher income distributions.
* **Race & Native Country**: Both show some impact on income, though less dominant.

---

##  Correlation Analysis

After one-hot encoding categorical variables, a correlation matrix was computed. Features with the highest positive correlation with income include:

* `capital-gain`
* `education_level`
* `hours-per-week`
* `age`

---

##  Dataset Optimization

Memory usage before and after preprocessing:

* **Original size**: \~3.8 MB
* **Optimized size**: \~1.1 MB

Optimizations were done using efficient data types and column reduction.

---

## 📚 Conclusion

This project highlights the strongest indicators of high income using visualization and correlation analysis. It serves as a solid foundation for predictive modeling or policy design focused on education, labor, and economic mobility.

---

## 🛠️ Tools & Libraries

* Python
* Pandas, NumPy
* Matplotlib, Seaborn
* Scikit-learn
* Google Colab
* KaggleHub
