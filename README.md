# Heart_disease_prediction

:The goal of our project is to 
 analyze heart disease data and predict the likelihood of heart disease based on various health indicators of patients. 

---
1.Preprocessing
---
The original dataset included multiple versions for different sources and formats. 
Among them, processed.cleveland.data was selected because it is the most commonly used and cleanest version for heart disease prediction research, with minimal missing data and consistent formatting.

**The preprocessing steps include:**

Assigning column names based on the dataset documentation (14 attributes including age, sex, cp, etc.)

**Handling missing values:**

Missing values in ca and thal were represented as ?, which were first replaced with np.nan.

These NaN values were filled with the mode (most frequent value) of each column.

**Data type conversion:**

After filling missing values, the columns were converted to appropriate numeric types.

**Encoding categorical features:**

sex, cp, fbs, restecg, exang, slope, ca, thal were treated as categorical and encoded using one-hot encoding.

**Feature scaling:**

The numerical features were scaled using StandardScaler to normalize the input range, which helps improve model performance.

**Final output:**

The preprocessed dataset was saved as a new CSV file named heart_disease_preprocessed.csv for use in model training and testing.

These steps ensured the dataset is clean, numerical, and standardized—ready for classification and clustering models.
  
---
2.Learning Model training and testing
---

  :different models (classification and clustering), combination of model parameters for each model
  :K-fold cross validation for testing classication models + use different evaluation methods
  :To find the topo five and best combination of the above
  
---

2-1.Classification model training and testing
---

1) Models: Logistic Regression, KNN, SVM, Decisioin Tree

2) Evaluaion: Accuracy, Precision, Recall, F1-score

3) Visualization: Bargraph, Line graph, Performance summary table, confusion matrix

4) Process: 
아래의 모델 평가 지표에서 Precision(예측시 실제로도 심장질환인 비율)과 Recall(실제로 심장질환이 있는 사람 중에 예측도 그러한 비율)사이의 편차가 크지 않고 둘 지표다 높은 모델이 "심장질환 예측"에 가장 적합하다고 생각함
4가지 모델의 평균 성능을 비교해봤을때, F1 점수(Precision과 Recall의 평균지표)가 높은 Logistic regression 모델과 KNN모델이 가장 적합할 것이라고 가정함.
아래에 파라미터 비교를 통해 상위 5가지 조합과 최고의 조합을 도출하고자 함

5) Function:


6) No use in class(method,class,function): 
ConfusionMatrixDisplay(class:utility class to visualize confusion matrix)
pandas.plotting.table(method: visualize data frames as a table)
ax.xaxis.set_visible, ax.yaxis.set_visible, ax.set_frame_on,auto_set_font_size, set_fontsize, scale(method: table object-table style,x,y axis hide and frame delete metod)
sort_values (method:pandas-sort the dataframe by one or more columns.)


7) Output: 

4가지 모델 평균 성능 비교:

<img width="363" alt="image" src="https://github.com/user-attachments/assets/9d196393-d459-4074-bc23-2748f609538c" />

![image](https://github.com/user-attachments/assets/c330eb76-5b92-4ec6-9217-b179140ce8fe)
---

Logistic regression 평균 성능:

<img width="323" alt="image" src="https://github.com/user-attachments/assets/c26995a8-216d-491a-a265-0e07104f796b" />


최적의 C값: C=0.1, F1 Score: 0.8310

![image](https://github.com/user-attachments/assets/c16fa8bc-c3aa-4a3c-a440-2575923d9fa0)
---

KNN 평균 성능:

<img width="267" alt="image" src="https://github.com/user-attachments/assets/b5f48dd2-2340-40e9-97be-4d0b7beb920c" />


최적의 K값: 5, F1 Score: 0.8308

![image](https://github.com/user-attachments/assets/d168891d-af64-4726-b809-71e0db252232)
---

 SVM 평균 성능:
 
<img width="290" alt="image" src="https://github.com/user-attachments/assets/c35bc9b7-f1f7-4a74-9f64-f90054380787" />


최적 SVM 커널: rbf, F1 Score: 0.8121

![image](https://github.com/user-attachments/assets/e6959665-4135-4b9b-948f-a6c9a7d5b8ce)
---

 Decision Tree 평균 성능:
 
<img width="281" alt="image" src="https://github.com/user-attachments/assets/d8e8c175-93b8-412b-9912-af0ee0262c38" />


 최적 Decision Tree depth: 7, F1 Score: 0.7756
 
 ![image](https://github.com/user-attachments/assets/793ca6f3-5b5a-4a2c-a6bb-13c4192dc1e8)
---

상위 5가지 조합과 최적의 조합 도출>

![image](https://github.com/user-attachments/assets/279a2f3a-502b-477c-999c-28e070db2f59)


 F1 Score 기준 최고의 조합:
모델: Logistic Regression, 파라미터: C=0.1, F1 Score: 0.8300

---

추가 확인:confusion matrix of logistic regression and KNN >


![image](https://github.com/user-attachments/assets/254bf2a1-c972-4ff5-80f0-b486b6c4036c)


![image](https://github.com/user-attachments/assets/3d299582-01da-444e-8938-32a8c3bf7ee0)


---
2-2.Clustering model training and testing
---  
Learning Model Training and Testing

We applied different models (classification and clustering), experimented with combinations of parameters for each model, and used k-fold cross-validation for classification models. Evaluation metrics guided the selection of top five and best-performing configurations.

### 2-2. Clustering Model Training and Testing

#### Objective
To identify natural groupings in patient data using unsupervised learning (no labels), and explore potential risk stratification via clustering.

#### Algorithms Used
- **KMeans Clustering** (Centroid-based)
- **Agglomerative Clustering** (Hierarchical-based)

#### Experimental Setup
- PCA was applied to reduce dimensions for 2D visualization.
- Cluster counts tested: **3, 4, 5**
- Evaluation focused on **visual separation** and **clinical interpretability** (no silhouette score, per course rule)

#### Top 5 Configurations
![1123123](https://github.com/user-attachments/assets/0749d836-86f5-4110-b828-26e48ae0e563)

| Rank | Model             | Reason                                                |
|------|------------------|--------------------------------------------------------|
| 1    | KMeans (k=4)     | Most distinct and interpretable clusters              |
| 2    | Agglo (n=5)      | Well-defined hierarchical grouping                    |
| 3    | KMeans (k=5)     | Finer segmentation, clear separation                  |
| 4    | KMeans (k=3)     | Simple 3-level grouping (low/moderate/high)           |
| 5    | Agglo (n=4)      | Reasonably balanced and interpretable                 |

#### Final Model Selection: **KMeans (k=4)**
- Showed the clearest cluster boundaries in PCA space
- Mapped well to expected patient groups (e.g., high, moderate, low, borderline)
- Fast, scalable, and simple to implement
![123123](https://github.com/user-attachments/assets/8480b91a-2c24-469e-80b4-369f5669c55b)

#### Visual Output Files
- `basic_clustering_comparison.png`: All n=3,4,5 comparisons
- `top5_clustering_comparison.png`: Visualization of top 5 models
- `final_kmeans_k4.png`: Final clustering result

#### Key Insights from KMeans (k=4)

| Cluster | Description    | Key Features                        |
|---------|----------------|-------------------------------------|
| 0       | High-Risk      | ↑ oldpeak, ↑ ca, ↑ exang            |
| 1       | Moderate-Risk  | Intermediate values in key features |
| 2       | Low-Risk       | ↑ thalach, ↓ oldpeak, ↓ exang       |
| 3       | Mixed          | Overlapping or borderline indicators|



