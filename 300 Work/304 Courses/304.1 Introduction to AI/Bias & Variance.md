One of the challenges in machine-learning is balancing the bias & variance.
### **Bias:**

- The **gap between the predicted value and the actual outcome**
- Happens when the model makes **strong, incorrect assumptions**
- Leads to **underfitting** – the model is too simple to capture the pattern
##### Real-World Example:
A weather app always says it's 25°C no matter what.  
→ It's **not learning from data** → **High Bias**

---
###  **Variance:**

- The amount the model's predictions **change** when trained on different parts of the data
- Happens when the model is **too complex** and fits even the **noise**
- Leads to **overfitting** – performs well on training data, but poorly on new data
#####  Real-World Example:

A student memorizes answers from one practice test. In the real test with different questions, he fails.  
→ He learned the **exact data**, not the **pattern** → **High Variance**

---
###  **Bias-Variance Tradeoff:**

- High Bias → Underfitting
    
- High Variance → Overfitting
    
- **Goal:** Find the sweet spot with **low bias and low variance** for best generalization
[[Overfitting & Underfitting]]