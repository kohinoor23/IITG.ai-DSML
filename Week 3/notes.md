## Support Vector Machines
- Supervised
> StatQuest 

- **Margin** : Shortest distance between observations and threshold (classified completely)
- Threshold that gives _maximum margin_ is called **Maximal Margin Classifier**
    - Super-sensitive to outliers
- _Solution_ : Allow misclassification (increase bias, decrease variance)
- In this case, margin is called **soft margin**
    - Determine using Cross Validation
- Threshold is called **Support Vector Classifier**  
    - Observations on edge, within soft margin are called Support Vectors
<p align = "center">
<img width="471" alt="image" src="https://github.com/atul2602/IITG.ai-DSML/assets/61497490/04ef30a9-0397-40ef-b5ce-e45ba3614220">
</p> 

- Above methods work to create a _hyperplane_, what about this??
<img width="484" alt="image" src="https://github.com/atul2602/IITG.ai-DSML/assets/61497490/b47e604e-6a6d-4c38-ad17-ba70599023df"> 

- **Support Vector Machines**
    - Start with data in relatively low dimension
    - Move the data into higher dimension
    - Find SVC that separates data into 2 groups
<p align = "center">
<img width="412" alt="image" src="https://github.com/atul2602/IITG.ai-DSML/assets/61497490/98fe870c-28b6-41c7-93e8-d36558d01dd6">
</p> 

- **Kernel Functions** : Used to systematically find SVC in higher dimensions
    - Polynomial(d : degree) : Use CV to get d
    - Radial : idea is to classify based on nearest observations in training data 
- _Kernel Trick_ : the kernel function doesnt physically convert data to higher dimensions, but uses pairwise relations

### Polynomial Kernel
<p align = "center">
$$(a \cdot b + r)^{d}$$ expands to $$(a\sqrt{r}, a^2, r).(b\sqrt{r}, b^2, r)$$ where a and b are two different data points and $d=2$
</p>  

- This expression helps to calculate pair-wise relationships in higher dimensions
- `r` and `d` determined using cross validation

### Radial Kernel
- $$e^{-\gamma(a-b)^{2}}$$
- Put `r=0` in polynomial kernel, then data remains in 2-D
- Add multiple `r=0` kernel to get multidimensional data
- expand $e^{a \cdot b}$ using Taylor's to see infinite dimensional relation

---
[Playlist](https://www.youtube.com/playlist?list=PLKnIA16_RmvbOIFee-ra7U6jR2oIbCZBL)
- SVM is an improved version of Logistic Regression
    - Classify as _widely_ as possible
    - Maximise margin d
    - Touch points are called support vectors
  <img width="250" alt="image" src="https://github.com/atul2602/IITG.ai-DSML/assets/61497490/6f570b0e-23d4-40b3-b07f-45dc14217d71">
  
#### Hard Margin SVM  
  - Hyperplane $\vec{w} \cdot \vec{x} + w_{0} = 0$, $\vec{w}$ is normal to the hyperplane
  - **Decision Rule** : $\vec{w} \cdot \vec{v} + b \ge 0$
  <img width="262" alt="image" src="https://github.com/atul2602/IITG.ai-DSML/assets/61497490/58b6bd3d-5e32-47eb-bda7-bcf736eed55d">  

  - **Aim** : Maximise distance between $\pi_{+} (\vec{w} \cdot \vec{x} + b = 1)$ and $\pi_{-} (\vec{w} \cdot \vec{x} + b = -1)$ 
      - Assuming $Y_{i} \cdot (\vec{w} \cdot \vec{x_{i}} + b) \ge 1$ 
      - Now, distance between $x_1$ on $\pi_{+}$ and $x_2$ on $\pi_{-}$ is $(\vec{x_2} - \vec{x_1}) \cdot \frac{\vec{w}}{|w|}$, simplifies to $\frac{2}{|w|}$

