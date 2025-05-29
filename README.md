# Heart_disease_prediction
:프로젝트 설명
---
1.Preprocessing
  :
---

2.Learning Model training and testing
  :different models (classification and clustering), combination of model parameters for each model
  :K-fold cross validation for testing classication models + use different evaluation methods
  :To find the topo five and best combination of the above

---

2-1.Classification model training and testing
Models: Logistic Regression, KNN, SVM, Decisioin Tree
Evaluaion: Accuracy, Precision, Recall, F1-score
Visualization: Bargraph, Line graph, Performance summary table, confusion matrix
Process: #아래의 모델 평가 지표에서 Precision(예측시 실제로도 심장질환인 비율)과 Recall(실제로 심장질환이 있는 사람 중에 예측도 그러한 비율)사이의 편차가 크지 않고 둘 지표다 높은 모델이 "심장질환 예측"에 가장 적합하다고 생각함
#4가지 모델의 평균 성능을 비교해봤을때, F1 점수(Precision과 Recall의 평균지표)가 높은 Logistic regression 모델과 KNN모델이 가장 적합할 것이라고 가정함.
#아래에 파라미터 비교를 통해 상위 5가지 조합과 최고의 조합을 도출하고자 함

No use in class(method,class,function): 
ConfusionMatrixDisplay(class:utility class to visualize confusion matrix)
pandas.plotting.table(method: visualize data frames as a table)
ax.xaxis.set_visible, ax.yaxis.set_visible, ax.set_frame_on,auto_set_font_size, set_fontsize, scale(method: table object-table style,x,y axis hide and frame delete metod)
sort_values (method:pandas-sort the dataframe by one or more columns.)

Output: 
4가지 모델 평균 성능 비교:
                  Model  Accuracy  Precision    Recall  F1 Score
0        Decision Tree  0.765410   0.739355  0.769312  0.750195
1                  KNN  0.848087   0.850837  0.813228  0.830790
2  Logistic Regression  0.848197   0.867943  0.791005  0.826920
3                  SVM  0.831694   0.859069  0.762434  0.806166
![image](https://github.com/user-attachments/assets/c330eb76-5b92-4ec6-9217-b179140ce8fe)

Logistic regression 평균 성능:
   Accuracy  Precision    Recall  F1 Score Parameter
0  0.854863   0.893638  0.776984  0.831014     C=0.1
1  0.848197   0.867943  0.791005  0.826920      C=10
2  0.848197   0.867943  0.791005  0.826920       C=1
3  0.838306   0.860140  0.776720  0.815098     C=100
4  0.811803   0.876266  0.690741  0.771074    C=0.01
최적의 C값: C=0.1, F1 Score: 0.8310
![image](https://github.com/user-attachments/assets/c16fa8bc-c3aa-4a3c-a440-2575923d9fa0)

KNN 평균 성능:
     K  Accuracy  Precision    Recall  F1 Score
0   3  0.811913   0.804239  0.784656  0.792421
1   5  0.848087   0.850837  0.813228  0.830790
2   7  0.838142   0.842872  0.798942  0.818986
3   9  0.821858   0.830774  0.770370  0.797073
4  11  0.821858   0.845190  0.748413  0.792176
최적의 K값: 5, F1 Score: 0.8308
![image](https://github.com/user-attachments/assets/d168891d-af64-4726-b809-71e0db252232)

 SVM 평균 성능:
    Accuracy  Precision    Recall  F1 Score  Kernel
0  0.834973   0.853260  0.777249  0.812098     rbf
1  0.831694   0.859069  0.762434  0.806166  linear
최적 SVM 커널: rbf, F1 Score: 0.8121
![image](https://github.com/user-attachments/assets/e6959665-4135-4b9b-948f-a6c9a7d5b8ce)

 Decision Tree 평균 성능:
   Depth  Accuracy  Precision    Recall  F1 Score
0     7  0.791694   0.772299  0.783333  0.775579
1     3  0.781858   0.795233  0.704233  0.745305
2     5  0.765410   0.770693  0.711905  0.736633
3  None  0.738907   0.707413  0.754762  0.727872
 최적 Decision Tree depth: 7, F1 Score: 0.7756
 ![image](https://github.com/user-attachments/assets/793ca6f3-5b5a-4a2c-a6bb-13c4192dc1e8)

상위 5가지 조합과 최적의 조합 도출>
![image](https://github.com/user-attachments/assets/0c8bb169-270a-461d-963e-cd8a461637de)
 F1 Score 기준 최고의 조합:
모델: Logistic Regression, 파라미터: C=0.1, F1 Score: 0.8300

추가 확인:confusion matrix of logistic regression and KNN >
![image](https://github.com/user-attachments/assets/254bf2a1-c972-4ff5-80f0-b486b6c4036c)
![image](https://github.com/user-attachments/assets/3d299582-01da-444e-8938-32a8c3bf7ee0)


---
2-2.Clustering model training and testing
  
