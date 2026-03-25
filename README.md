# 신용카드 사기 탐지 분석 | Credit Card Fraud Detection

Analyzing real-world credit card transaction data to detect fraudulent transactions using machine learning.  
실제 신용카드 거래 데이터를 활용하여 머신러닝으로 사기 거래를 탐지하는 분석 프로젝트입니다.

---

## 프로젝트 개요 | Overview

전체 거래 284,807건 중 사기 비율이 0.17%에 불과한 극심한 클래스 불균형 문제를 SMOTE로 해결하고, 두 가지 모델을 비교하여 은행 실무에 적합한 모델을 선정했습니다.

Out of 284,807 transactions, only 0.17% are fraudulent. This severe class imbalance was addressed using SMOTE, and two models were compared to determine the most suitable one for real-world banking.

---

## 데이터 | Data

- 출처 | Source: [Kaggle - Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
- 전체 거래 | Total transactions: 284,807건
- 사기 거래 | Fraudulent: 492건 (0.17%)
- 특성 | Features: V1~V28 (PCA 변환), Amount, Time

---

## 분석 과정 | Process

### 1단계 | Step 1: 탐색적 데이터 분석 (EDA)
- 클래스 불균형 확인 | Confirmed severe class imbalance (99.83% normal vs 0.17% fraud)
- 거래 금액 및 시간대별 분포 분석 | Analyzed amount and time distributions
- 각 변수와 사기 여부의 상관관계 분석 | Examined feature correlations with fraud label

![클래스 분포](images/class_distribution.png)
![상관관계](images/correlation.png)

### 2단계 | Step 2: 전처리 (Preprocessing)
- Amount, Time 변수 정규화 | Normalized Amount and Time using StandardScaler
- SMOTE를 활용한 클래스 불균형 해소 | Resampled minority class using SMOTE

![SMOTE 비교](images/smote_comparison.png)

### 3단계 | Step 3: 모델링 및 비교 (Modeling & Comparison)

| 모델 | Model | ROC-AUC | 사기 탐지 Recall | 오탐 FP |
|------|-------|---------|----------------|--------|
| 로지스틱 회귀 | Logistic Regression | 0.9698 | 90/98건 | 1,458건 |
| 랜덤포레스트 | Random Forest | 0.9688 | 79/98건 | 18건 |

![ROC 커브](images/roc_curve.png)
![혼동행렬](images/confusion_matrix.png)

---

## 결론 | Conclusion

- 로지스틱 회귀는 사기를 더 많이 탐지하지만 오탐이 많아 고객 불편 초래  
  Logistic Regression detects more fraud but generates excessive false positives
- 랜덤포레스트는 오탐이 18건으로 현저히 적어 고객 경험 측면에서 우수  
  Random Forest produces only 18 false positives, minimizing customer inconvenience
- 은행 실무에서는 고객 불편을 최소화하는 랜덤포레스트가 더 적합  
  Random Forest is more suitable for real-world banking operations

---

## 사용 기술 | Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![imbalanced-learn](https://img.shields.io/badge/imbalanced--learn-FF6F00?style=flat&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat&logoColor=white)
