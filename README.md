### Comprehensive Analysis of `fertility.csv` Using Python

---

### Key Insights & Ubuntu Connections

1. **Data Cleaning (Ubuntu: "Healing the Community")**
   - Fixed outlier: 342 sitting hours → replaced with median (7 hours)
   - Harmonized categorical values (e.g., "no" → "No" for consistency)
   - *Ubuntu Wisdom: "Correcting misrepresentations strengthens community truth"*

2. **Exploratory Analysis (Ubuntu: "Sharing Community Stories")**
   - **Age Distribution**: Majority aged 28-33 (peak fertility years)
   - ![Screenshot 2025-06-03 014758](https://github.com/user-attachments/assets/f6c3adf2-5334-4c01-a7a0-b55bd6b28e39)

   - **Diagnosis**: 84.3% Normal, 15.7% Altered
   - ![Screenshot 2025-06-03 014816](https://github.com/user-attachments/assets/6d714f8d-35c8-4d78-bbb5-e28b9739cb30)

   - **Key Observation**: Higher sitting hours correlate with "Altered" diagnosis
   - ![Screenshot 2025-06-03 014935](https://github.com/user-attachments/assets/0eee6237-f444-4458-90f9-4a235ed1a624)


3. **Feature Relationships (Ubuntu: "We Are Connected")**
   - **Seasonal Impact**: Higher "Altered" rates in winter (23.5% vs 15.7% overall)
     ```
     🌱 Seasonal Diagnosis Rates (%)
                    Normal    Altered
     Season                          
     fall          84.62%     15.38%
     spring        81.48%     18.52%
     summer       100.00%      0.00%
     winter        76.47%     23.53%
     ```
   - **Strongest Correlations**:
     - Positive: Surgical intervention (+0.24)
     - Negative: High fevers (-0.19)

4. **Storage Considerations**
   - **Database Choice**: NoSQL (e.g., MongoDB) recommended due to:
     - Mixed data types (numerical + categorical)
     - Potential for unstructured medical notes
     - Need for horizontal scaling
   - *Ubuntu Analogy: "Like a village storehouse - flexible containers for diverse harvests"*

5. **Preprocessing (Ubuntu: "Preparing Collective Wisdom")**
   - Created new feature: `Lifestyle_risk` (0-3 scale combining smoking, alcohol, and sedentarism)
   - Encoded all categorical variables for modeling
   - *Ubuntu Principle: "Diverse experiences woven into shared understanding"*

---

### Lessons from Analysis

1. **Data Quality Matters**  
   The 342-hour sitting outlier could have skewed results - shows importance of cleaning 

2. **Context is Crucial**  
   Higher "Altered" rates in winter align with medical research on seasonal fertility patterns 

3. **Feature Engineering Creates Insight**  
   The new `Lifestyle_risk` composite feature:  
   ```python
   # Combines three risk factors
   df['Lifestyle_risk'] = (smoking) + (alcohol) + (sitting)
   ```
   Demonstrates how feature transformation aids analysis 

4. **Storage Implications**  
   This small dataset (100 rows) could use SQL, but real-world medical data would need:  
   - **Data Lake**: For raw patient records (text, images)  
   - **Warehouse**: For processed analytics-ready tables  
     

```mermaid
graph LR
A[Raw Data] --> B{Data Lake}
B --> C[Cleaning]
C --> D[Processed Data]
D --> E{Data Warehouse}
E --> F[Analytics]
```
