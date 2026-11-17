<p align="center">
    <img src="https://beyondeducation.es/wp-content/uploads/2024/02/CUNEF-UNI50.png" width="500">
</p>


<h1 align="center"><b>Initial Assignment - Machine Learning</b></h1>
<h2 align="center">M2026-27 - Master in Data Science and Artificial Intelligence</h2>

| Full name | CUNEF email |
|---|---|
| Melanie Álvarez | melanie.alvarez@cunef.edu |
| María Victoria del Campo | victoria.delcampo@cunef.edu |
| Alicia Plaza | alicia.plaza@cunef.edu |

**GitHub repository:** https://github.com/mvdelcampo/machine-learning-project

# **1. Business Problem Description**

Antimicrobial resistance (AMR) is a global public health problem, it reduces therapeutic
options and complicates clinical decision-making, especially in emergency healthcare
settings. Ciprofloxacin (CIP) is a widely used fluoroquinolone antibiotic for treating various bacterial infections, particularly certain urinary tract infections. According to the European Centre for Disease Prevention and Control (ECDC), **30% of invasive *Escherichia coli* isolates in Spain were resistant to fluoroquinolones in 2024**, compared with the EU/EEA average of 22.5%, highlighting the relevance of investigating resistance to this antibiotic class.


### **Shortcomings of the current solution**

The conventional method for determining ciprofloxacin resistance is the antibiogram (culture and antibiotic susceptibility testing), which typically takes 48–72 hours (Wenzler et al., 2023). During this period, clinicians may need to prescribe empirical treatment without knowing whether the bacterial isolate is resistant to ciprofloxacin, potentially leading to ineffective therapy and delayed appropriate treatment. 


### **Opportunity**

Machine Learning can predict ciprofloxacin resistance using available susceptibility results from other antibiotics and patient characteristics, supporting clinical decision-making while the complete antibiogram is pending.


### **Limitations of previous work** 

Wishal and Sahara, *Predicting Multi-Drug Resistance in Bacterial Isolates Through Performance Comparison and LIME-based Interpretation of Classification Models*, used the same synthetic dataset to predict multidrug resistance (MDR), comparing five Machine Learning models (LR, RF, AdaBoost, XGBoost, LightGBM) and achieving performance metrics close to 99%. However, they used antibiotic resistance results both to define MDR target and as predictors, creating a risk of **target leakage** and making the problem almost deterministic and of little real predictive value.

### **Research question and technical formulation**
> ***Can the resistance status of ciprofloxacin be estimated from the susceptibility profiles of other antibiotics, bacterial species, and patient clinical features?***

- **Learning paradigm:** supervised binary classification
- **Target (y):** `CIP`, with **R (Resistent) = 1** and **S (Susceptible) = 0** for this initial definition.
- **Candidate features (X):** results from the remaining **14 antibiotics**, plus `Age`, `Gender`, `Souches`, `Diabetes`, `Hypertension`, `Hospital_before`, `Infection_Freq`.
- **Leakage guard:** neither `CIP` nor any feature calculated from CIP (such as MDR labels that include CIP) may enter X.

### **Bibliographic Reference**

- Wenzler et al. (2023). Antimicrobial susceptibility testing: An updated primer for clinicians in the era of antimicrobial resistance: Insights from the Society of Infectious Diseases Pharmacists.
https://accpjournals.onlinelibrary.wiley.com/doi/10.1002/phar.2781

# **2. Data Source**

The dataset is the **Multi-resistance antibiotic susceptibility** dataset attributed to A. Hosni on Kaggle. The source file is downloaded from `https://www.kaggle.com/datasets/adilimadeddinehosni/multi-resistance-antibiotic-susceptibility/data`.

***Advantages:*** The dataset contains 10,710 bacterial isolates, including susceptibility results for 15 antibiotics and relevant clinical characteristics. Its size and variety of features make it suitable for investigating cross-resistance patterns and developing a binary classification model to predict ciprofloxacin resistance. Additionally, it is publicly available, supporting reproducibility.

***Disadvantages:*** The dataset is synthetic and simulates data from only one healthcare facility and includes a limited number of bacterial species, reducing its generalizability to real clinical environments. It also contains missing values, inconsistent categories, and limited clinical information.




