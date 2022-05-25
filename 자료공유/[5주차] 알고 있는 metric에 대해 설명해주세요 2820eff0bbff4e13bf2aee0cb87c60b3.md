# [5주차] 알고 있는 metric에 대해 설명해주세요.

공부기간: 2022년 5월 17일 → 2022년 5월 23일
속성: 머신러닝
태그: 5주차

# 알고 있는 metric에 대해 설명해주세요. (ex. RMSE, MAE, recall, precision ...)

## 회귀 모델 평가 지표

MAE, MSE, RMSE, MSLE, MAPE, MPE, R^2

- **MAE(Mean Absolute Error)**
    - 실제 값과 예측 값의 차이를 절대값으로 변환해 평균화
    - 에러에 따른 손실이 선형적으로 올라갈 때 적합
    
    $$
    MAE = {\frac{1}{N}\sum_{i=1}^{N}{|yi-\hat{yi}}|}
    $$
    
- **MSE(Mean Squared Error)**
    - 예측값과 실제값 차이의 면적의 합
    - 특이값이 존재하면 수치가 많이 늘어남
    
    $$
    RMSE = {\frac{1}{N}\sum_{i=1}^{N}{(yi-\hat{yi}})^2}
    $$
    
- **RMSE(Root Mean Square Error)**
    - MSE에 루트를 씌운 값
    - 에러에 따른 손실이 기하 급수적으로 올라가는 상황에서 쓰기 적합

$$
RMSE = \sqrt{\frac{1}{N}\sum_{i=1}^{N}{(yi-\hat{yi}})^2}
$$

- **MSLE(Mean Squared Log Error)**
    - MSE에 로그 적용
    
    $$
    MSLE = {\frac{1}{N}\sum_{i=1}^{N}{(log(yi+1)-log(\hat{yi}+1)})^2}
    $$
    
- **MAPE(Mean Absolute Percentage Error)**
    - MAE를 퍼센트로 변환
    
    $$
    MAPE = \frac{1}{N}\sum_{i=1}^{N}{\frac{|yi-\hat{yi}|}{yi}}*100
    $$
    
- **MPE(Mean Percentage Error)**
    - MAPE에서 절대값을 제외한 지표
    
    $$
    MPE = \frac{1}{N}\sum_{i=1}^{N}{\frac{yi-\hat{yi}}{yi}}*100
    $$
    
- **R Squared(결정계수)**

$$
R^2 = \frac{SSE}{SST}=1-\frac{SSR}{SST}
$$

![Untitled](%5B5%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%5D%20%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%80%E1%85%A9%20%E1%84%8B%E1%85%B5%E1%86%BB%E1%84%82%E1%85%B3%E1%86%AB%20metric%E1%84%8B%E1%85%A6%20%E1%84%83%E1%85%A2%E1%84%92%E1%85%A2%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%86%E1%85%A7%E1%86%BC%E1%84%92%E1%85%A2%E1%84%8C%E1%85%AE%E1%84%89%E1%85%A6%E1%84%8B%E1%85%AD%202820eff0bbff4e13bf2aee0cb87c60b3/Untitled.png)

- **Adjusted R Square**
    - 독립변수의 개수가 증가하면 결정계수는 일방적으로 증가
    Adjusted R^2는 분자를 감소시켜주는 연산을 통해서 일방적인 증가를 방지

$$
Adjusted R^2 = 1=\frac{SSR/(n-k-1)}{SST/(n-1)}
$$

## 분류 모델 평가 지표

Accuracy, Precision, Recall, F1-score, ROC-AUC

![Untitled](%5B5%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%5D%20%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%80%E1%85%A9%20%E1%84%8B%E1%85%B5%E1%86%BB%E1%84%82%E1%85%B3%E1%86%AB%20metric%E1%84%8B%E1%85%A6%20%E1%84%83%E1%85%A2%E1%84%92%E1%85%A2%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%86%E1%85%A7%E1%86%BC%E1%84%92%E1%85%A2%E1%84%8C%E1%85%AE%E1%84%89%E1%85%A6%E1%84%8B%E1%85%AD%202820eff0bbff4e13bf2aee0cb87c60b3/Untitled%201.png)

- **Accuracy(정확도)**
    - 전체 데이터 중에서 올바르게 예측한 비율
    - 데이터가 imbalance한 경우 정확도는 성능을 측정하는 데 좋은 지표가 되지 못함

$$
Accuracy = \frac{TP+TN}{TP+TN+FP+FN}
$$

- **Precision(정밀도)**
    - 모델이 true로 분류한 것 중에서 실제로 true인 것의 비율→ false가 중요한 경우 사용
    
    ex) 스팸 메일 분류기
    

$$
Precision = \frac{TP}{TP+FP}
$$

- **Sensitivity(민감도)= Recall(재현율)** = **TPR**
    - 실제로 true인 것들 중에서 예측이 true인 것의 비율 → true가 중요한 경우 사용
    
     실제로 질병이 있을 때, 질병이 있다고 예측할 확률
    
    ex) 암 진단
    
    $$
    Recall = \frac{TP}{TP+FN}
    $$
    
- **Specificity(특이도)**
    - 실제로 false인 것들 중에서 예측이 false인 것의 비율
    
    실제로 질병이 없을 때, 질병이 없다고 예측할 확률
    
    $$
    Specificity = \frac{TN}{TN+FP}
    $$
    
- **F1-score**
    - Precision과 recall의 조화평균
    
    $$
    F1-score = \frac{1}{\frac{1}{precision}+\frac{1}{recall}} = \frac{2*precision*recall}{precision+recall}
    $$
    
    <aside>
    ❓ precision과 recall의 산술평균을 사용하지 않고 조화평균을 사용하는 이유
    
    </aside>
    
    precision과 recall은 하나가 높아지면 하나가 낮아지는 관계(trade-off 관계)
    둘 중 하나가 0에 가깝게 낮을 때 지표에 그것이 잘 반영되게 하기 위해서 (두 지표 모두 균형있게 반영하기 위해)
    
    ![Untitled](%5B5%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%5D%20%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%80%E1%85%A9%20%E1%84%8B%E1%85%B5%E1%86%BB%E1%84%82%E1%85%B3%E1%86%AB%20metric%E1%84%8B%E1%85%A6%20%E1%84%83%E1%85%A2%E1%84%92%E1%85%A2%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%86%E1%85%A7%E1%86%BC%E1%84%92%E1%85%A2%E1%84%8C%E1%85%AE%E1%84%89%E1%85%A6%E1%84%8B%E1%85%AD%202820eff0bbff4e13bf2aee0cb87c60b3/Untitled%202.png)
    
- **AUC(Area Under the Cover)-ROC(Receiver Operating Characteristic)**
    - ROC : FPR이 변화할 때, TPR이 어떻게 변화하는지 보여주는 곡선
    - AUC : ROC 아래의 넓이
    - x축 :FPR=1-specificity, y축:TPR=sensitivity
    - 우수한 모델일수록 AUC 값이 1에 가까움

![Untitled](%5B5%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%5D%20%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%80%E1%85%A9%20%E1%84%8B%E1%85%B5%E1%86%BB%E1%84%82%E1%85%B3%E1%86%AB%20metric%E1%84%8B%E1%85%A6%20%E1%84%83%E1%85%A2%E1%84%92%E1%85%A2%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%86%E1%85%A7%E1%86%BC%E1%84%92%E1%85%A2%E1%84%8C%E1%85%AE%E1%84%89%E1%85%A6%E1%84%8B%E1%85%AD%202820eff0bbff4e13bf2aee0cb87c60b3/Untitled%203.png)

참고

[https://medium.com/@aatish_kayyath/confusion-matrix-lets-clear-this-confusion-4b0bc5a5983c](https://medium.com/@aatish_kayyath/confusion-matrix-lets-clear-this-confusion-4b0bc5a5983c)

[https://velog.io/@kimdukbae/데이터-과학-기초](https://velog.io/@kimdukbae/%EB%8D%B0%EC%9D%B4%ED%84%B0-%EA%B3%BC%ED%95%99-%EA%B8%B0%EC%B4%88)