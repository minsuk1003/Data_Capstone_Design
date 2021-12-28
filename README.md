# 2021-2학기 Data Capstone Design

## 현 코레일 시스템에 대한 시각화 및 승객 수 예측

## 1. 프로젝트 개요

- 이번 프로젝트는 코레일에서 제공하는 데이터를 이용해 다양한 시각화 기법으로 현재 코레일 시스템에 대해 의미 있는 결과를 도출하고, 머신러닝 시계열 예측 모델을 이용해 향후 코레일의 일일 승객 수를 예측한다.
- 시각화 프로젝트에서는 크게 5가지 주제의 시각화 분석을 진행한다.
- 승객 수 예측 프로젝트에서는 2018년 1월부터 2021년 4월까지의 코레일 일일 총 승객 수 데이터를 바탕으로 7가지의 시계열 모델을 학습하고, 2021년 5월 한 달 간의 일일 승객 수를 예측하여 7가지 모델의 성능을 비교한다.

> 시각화 프로젝트 내용
1) 시계열 데이터를 통한 기간에 따른 승객 수 시각화
2) 역 위치, 행정구역별 역 분포 시각화
3) 영업일 단계별 열차종 상관관계 시각화
4) 요일별 승객수 시각화
5) 열차종별 연령대와 성별 분포 시각화

> 시계열 프로젝트 내용
0) 시계열 분해법, ACF 및 PACF, 차분, ADF 검정 등을 통한 시계열 데이터의 정상성 확인 및 ARIMA 모델 파라미터 도출
1) AR 모델
2) MA 모델
3) ARIMA 모델
4) SARIMA 모델
5) FACEBOOK - Prophet 모델
6) SES 모델
7) HWES 모델
- RMSE, MAPE, R-Squared 총 3가지의 평가 지표를 통한 7가지 모델 성능 평가
 
> Dataset
- 역별 실적 데이터 (4개년) : 시각화, 승객 수 예측에 사용
![image](https://user-images.githubusercontent.com/63490319/147558421-9f8fa8f9-264c-46f9-b9e5-c51b098132a7.png)

- 고객 특성 데이터 (3개년) : 시각화에 사용
![image](https://user-images.githubusercontent.com/63490319/147558527-10966eed-24b9-4743-9a5b-4266f1250069.png)

- 역별 위치정보 데이터 : 시각화에 사용
![image](https://user-images.githubusercontent.com/63490319/147558732-1b00eea2-0df0-4242-b72c-8ce49f646adc.png)


## 2. 프로젝트 목표
> 시각화 프로젝트
- 현재 코레일 시스템에 대한 의미 있는 결과를 각각 다른 plot을 사용해 최소 5개 이상 도출
> 승객 수 예측 프로젝트
- 10% 미만의 MAPE 값을 가지거나, 0.8 이상의 R-Squared 값을 가지는 것이 목표이다.

## 3. 프로젝트 수행 내용, 결과
### 3-1. 시각화 프로젝트

### 3-2. 승객 수 예측 프로젝트

## 4. Conclusion
### 4-1. 기대효과
### 4-2. 결론 및 제언

