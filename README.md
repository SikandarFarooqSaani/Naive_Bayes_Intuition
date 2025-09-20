# 🎾 Naïve Bayes on Play Tennis Dataset  

*(This Readme is AI generated except dataset link for clarity 🙂)*  

## Dataset  
Kaggle link: [Play Tennis Dataset](https://www.kaggle.com/datasets/fredericobreno/play-tennis)  

We drop the **Day** column since it’s irrelevant.  
Our goal is to predict whether the game will be played when:  
**Outlook = Sunny, Humidity = High, Wind = Weak, Temperature = Hot**.  

---

## Step 1: Prior Probabilities  
From the dataset:  
- `Play = Yes → 9`  
- `Play = No → 5`  
- Total = 14  

So,  
\[
P(Yes) = \frac{9}{14}, \quad P(No) = \frac{5}{14}
\]

---

## Step 2: Conditional Probabilities  

### Outlook vs Play
- \( P(Sunny|No) = \frac{2}{5} \)  
- \( P(Sunny|Yes) = \frac{2}{9} \)  
- \( P(Overcast|Yes) = \frac{4}{9} \), \( P(Overcast|No) = 0 \)  
- \( P(Rainy|Yes) = \frac{3}{9} \), \( P(Rainy|No) = \frac{2}{5} \)  

---

### Temperature vs Play
- \( P(Hot|No) = \frac{2}{5} \), \( P(Hot|Yes) = \frac{2}{9} \)  
- \( P(Mild|No) = \frac{2}{5} \), \( P(Mild|Yes) = \frac{4}{9} \)  
- \( P(Cool|No) = \frac{1}{5} \), \( P(Cool|Yes) = \frac{3}{9} \)  

---

### Humidity vs Play
- \( P(High|No) = \frac{4}{5} \), \( P(High|Yes) = \frac{3}{9} \)  
- \( P(Normal|No) = \frac{1}{5} \), \( P(Normal|Yes) = \frac{6}{9} \)  

---

### Wind vs Play
- \( P(Weak|No) = \frac{2}{5} \), \( P(Weak|Yes) = \frac{6}{9} \)  
- \( P(Strong|No) = \frac{3}{5} \), \( P(Strong|Yes) = \frac{3}{9} \)  

---

## Step 3: Apply Naïve Bayes  

We want to compute:  

### For Yes  
\[
P(Yes|X) \propto P(Yes) \times P(Sunny|Yes) \times P(Hot|Yes) \times P(High|Yes) \times P(Weak|Yes)
\]  

\[
P(Yes|X) = \frac{9}{14} \times \frac{2}{9} \times \frac{2}{9} \times \frac{3}{9} \times \frac{6}{9}
\]  

\[
P(Yes|X) \approx 0.0070
\]

---

### For No  
\[
P(No|X) \propto P(No) \times P(Sunny|No) \times P(Hot|No) \times P(High|No) \times P(Weak|No)
\]  

\[
P(No|X) = \frac{5}{14} \times \frac{2}{5} \times \frac{2}{5} \times \frac{4}{5} \times \frac{2}{5}
\]  

\[
P(No|X) \approx 0.0411
\]

---

## Step 4: Decision  

Since:  
\[
P(No|X) > P(Yes|X)
\]  

👉 **The game will NOT be played.**  

---

## Intuition Gained  
This example shows how **Naïve Bayes multiplies prior with conditional probabilities** for each feature. Even though it assumes independence between features (which is rarely true in real-world data), it still provides a simple yet powerful probabilistic model.  
