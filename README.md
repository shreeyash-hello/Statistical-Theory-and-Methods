# 🐾 Exploring Breed-Specific Rehoming Timelines of Dogs at Animal Shelters  

## 📘 Overview  
This project examines how rehoming timelines vary across different dog breeds in animal shelters. Using statistical analysis and inferential modelling, the study explores whether the average rehoming time of **27 weeks** (as reported in literature) applies universally or varies by breed.  

---

## 📊 Dataset Summary  
- **Total Records:** 82  
- **Dog Breeds:** Dobermann, Shih Tzu, West Highland White Terrier (WHWT)  
- **Features:** Visited, Rehomed, Health, Breed, Age, Reason, Returned  
- **Data Cleaning:**  
  - 6 missing breed values removed (**7.32% of data**)  
  - 9 invalid `Rehomed` values (`99999`) imputed with breed-specific means  
  - 2 missing “Neglect” values replaced with “Unknown”  

---

## 🧮 Statistical Analysis  

### **1. Descriptive Analysis**
- Puppies had **shorter rehoming times** than fully grown dogs across all breeds.  
- Fully grown Dobermanns had a higher spread (SD = **12.71**) compared to puppies (SD = **7.44**).  
- **Average rehoming durations (weeks):**  

| Breed | Min | Median | Mean | Max | IQR |
|--------|------|--------|--------|------|------|
| Dobermann | 4 | 17 | **17.87** | 42 | 10 |
| WHWT | 7 | 20 | **20.19** | 48 | 12.25 |
| Shih Tzu | 9 | 18.5 | **19.54** | 42 | 11.5 |

> 💡 **50% of dogs** were rehomed within **20 weeks**, with **Dobermanns** rehomed fastest on average.

---

### **2. Distribution Modelling**
- Data followed a **log-normal distribution** (confirmed using the Shapiro–Wilk test).  

| Breed | W | p-value |
|--------|-------|----------|
| Dobermann | 0.970 | 0.710 |
| Shih Tzu | 0.966 | 0.547 |
| WHWT | 0.976 | 0.771 |

All p-values > 0.05 → data fits normality after log transformation.

---

### **3. Parameter Estimation (via Maximum Likelihood)**
| Breed | µ (mean, log-scale) | σ | Exp(µ) (mean weeks) |
|--------|----------------|------|-----------------|
| Dobermann | 2.729 | 0.586 | **15.24** |
| Shih Tzu | 2.883 | 0.423 | **17.88** |
| WHWT | 2.911 | 0.437 | **18.38** |

📈 **Dobermanns** had the shortest average rehoming time; **WHWT** stayed the longest.

---

### **4. One-Sample t-Test (vs. 27 Weeks)**

| Breed | t-value | p-value | n |
|--------|---------|----------|---|
| Dobermann | -4.574 | 0.00015 | 23 |
| Shih Tzu | -4.865 | 0.00005 | 26 |
| WHWT | -4.488 | 0.00013 | 27 |

🔹 None of the breeds had a mean rehoming time equal to **27 weeks (p < 0.05)**.  
- **95% Confidence Intervals:** 11.76 – 19.75 weeks across breeds.

---

### **5. Two-Sample Welch’s t-Test (Between Breeds)**

| Comparison | t-value | p-value | Result |
|-------------|---------|----------|----------|
| Dobermann vs Shih Tzu | -1.055 | 0.297 | No significant difference |
| Dobermann vs WHWT | -1.233 | 0.225 | No significant difference |
| Shih Tzu vs WHWT | -0.228 | 0.820 | No significant difference |

> Despite numeric differences, there was **no statistically significant difference** between breeds (p > 0.05).

---

## 💬 Key Insights  
- The **mean rehoming time (15–18 weeks)** is **significantly below** the assumed 27 weeks.  
- **Breed influences** rehoming time, though the dataset (n = 82) is too small for conclusive inference.  
- **Puppies** are rehomed faster across all breeds.  
- Insights can help shelters design **adoption strategies**, **targeted marketing**, and **resource allocation**.  

---

## 🚀 Future Work  
- Expand the dataset to include more breeds and samples.  
- Include **location**, **health**, and **reason for surrender** as variables.  
- Build **predictive models** for rehoming time estimation.  
- Explore **regression** or **survival analysis** for deeper insights.  

---

## 🧰 Technologies Used  
- **Language:** R  
- **Libraries:** dplyr, ggplot2, MASS, stats  
- **Statistical Methods:**  
  - Shapiro–Wilk Normality Test  
  - Maximum Likelihood Estimation  
  - One-Sample & Two-Sample t-Tests
