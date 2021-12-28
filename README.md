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


## 3. 프로젝트 수행 내용

## 3-0. 데이터 전처리 (역별 실적 데이터)

> 결측치 제거
- 모든 값들이 결측치인 메트릭 column 제거


![image](https://user-images.githubusercontent.com/63490319/147572961-afd19619-4995-47c5-8f01-63afb80411bd.png)

> type 변경
- 승차인원수, 하차인원수 column : object -> int

![image](https://user-images.githubusercontent.com/63490319/147573721-a0b5e58d-8b1b-45c1-a1a0-d86ad74e013b.png)

- 운행일자 column : object -> datetime

![image](https://user-images.githubusercontent.com/63490319/147573751-0862f3eb-42b8-4ec6-926f-3fc20e81370f.png)

> 총 인원수 column 생성
- 승차인원수 + 하차인원수 = 총 인원수

![image](https://user-images.githubusercontent.com/63490319/147573783-e4fbdf0a-185c-4907-b94e-da2c3de40aa9.png)

> 알아보기 쉽도록 column 값 수정
- 운행영업일단계 column 값 : '평일' -> '월, 금', '표준' -> '토, 일', '주중' -> '화, 수, 목'

![image](https://user-images.githubusercontent.com/63490319/147573832-9242881e-3ad6-4c71-9ede-517e8629c325.png)

> 일일 총 승객수 데이터 생성
- 총 인원수를 일별로 모두 더하여 역별 일일 총 승객수 데이터 생성

![image](https://user-images.githubusercontent.com/63490319/147574564-6bcf454c-71ff-445e-aec7-186e9c9517b5.png)

- 역별 일일 총 승객수 데이터를 통해 코레일의 일일 총 승객수 데이터 생성

![image](https://user-images.githubusercontent.com/63490319/147574630-87833ab1-a455-448f-9c34-af57f2b0fcc5.png)

## 3-1. 시각화 프로젝트

### 1) 기간에 따른 승객 수 시각화 (dataset : 역별 실적 데이터)

> histplot을 통한 기간별 일일 총 승객수 분포 시각화

![image](https://user-images.githubusercontent.com/63490319/147575012-7c5b4127-0a2e-40f1-a9ea-86baf9348262.png)

- 4번째 그래프인 일일 총 승객수 분포는 평균 약 70만명의 대략적인 정규분포 형태를 띈다.
- 그러나, 년도별로 나누면 2018년과 2019년은 일일 60만명 ~ 120만명의 승객수 분포를 보이는 반면, 2020년부터는 일일 20만명 ~ 80만명의 승객수 분포를 보인다.
- 즉, 2018, 2019년에 비해 2020년부터 승객수가 급감했음을 알 수 있다.


> lineplot을 통한 월평균 일일 승객수 시각화

![image](https://user-images.githubusercontent.com/63490319/147575484-c99ef5a9-d7e2-4866-8126-66650ae10428.png)

- 2018년부터 2020년 1월까지는 꾸준히 월별 일일 70만명 ~ 80만명의 승객수를 유지했으나, 2020년 초 코로나의 영향으로 승객수가 급감했다.
- 2020년 중반부터 2021년 5월까지는 월별 일일 50만명까지 회복했음을 볼 수 있다.

### 2) 역 위치, 행정구역별 역 분포 시각화 (dataset : 역별 위치정보 데이터)

> folium 라이브러리를 통한 지도, 역 위치, 행정구역별 역 분포 시각화

![image](https://user-images.githubusercontent.com/63490319/147575863-f2054649-1048-44a3-a18b-5fb0e3ca85b3.png)

- 시군구 행정구역에 코레일의 역이 얼마나 있는지를 보여주는 결과이다.
- 시군구 행정구역 정보가 들어있는 json 파일과 역별 위치정보 데이터의 DISTRICT 컬럼의 값이 같은 경우, 해당 행정구역의 역 수를 보여준다.
- 행정구역별로 코레일의 역이 얼마나 있는지를 시각적으로 알 수 있다.

### 3) 영업일 단계별 열차종 상관관계 시각화 (dataset : 역별 실적 데이터)

> barplot을 통한 영업일 단계별 열차종 평균 승객수 시각화

![image](https://user-images.githubusercontent.com/63490319/147576721-5bf4adcc-1884-44d0-8f0e-c1400e8b98ca.png)

- ITX-청춘은 명절대수송 기간보다 공휴일에 더 승객이 많고, 휴일 승객수가 평일 승객수의 약 2배를 차지한다.
- KTX는 공휴일보다 평일에 오히려 더 승객이 많고, 명절대수송 기간에 압도적으로 많은 승객수를 보인다.


> heatmap을 통한 영업일 단계별 열차종 상관관계 시각화

![image](https://user-images.githubusercontent.com/63490319/147576886-a5b682b5-cd2b-4683-8c23-c112ccdf1ced.png)

- 더 짙은 파란색일수록 강한 양의 상관관계, 흰색일수록 강한 음의 상관관계를 의미한다. 1에 가깝다면 두 열차종이 운행영업일 단계별로 비슷한 승객수 분포를 가지는 것이며, -1에 가깝다면 두 열차종이 운행영업일 단계별로 반대의 승객수 분포를 가지게 된다.


> clustermap으로 비슷한 상관관계를 보이는 열차종 군집

![image](https://user-images.githubusercontent.com/63490319/147576977-47d2319b-431e-4a51-b225-afd5ed2acb90.png)

- 영업일 단계별로 비슷한 승객수 분포를 보이는 열차종끼리 군집한 결과이다.

### 4) 요일별 승객수 시각화 (dataset : 고객 특성 데이터)

> barh plot을 통한 요일별 승객수 시각화

![image](https://user-images.githubusercontent.com/63490319/147577624-6a7240c5-7ad4-4057-93cc-a793dc3921de.png)

- 금요일에 승객이 제일 많았음을 알 수 있고, 화요일에 제일 적었음을 알 수 있다.

> pie chart를 통한 요일별 승객수 시각화

![image](https://user-images.githubusercontent.com/63490319/147577682-6fe8c9bb-a778-4ade-a68e-c4b40d27bb3c.png)

- 금요일에 코레일 이용 승객이 17.38%로 가장 많았고, 금,토,일의 승객 수가 전체 승객 수의 약 50%를 차지한다.
- 화요일과 수요일에 11.8%로 가장 승객이 적다.

### 5) 연령대, 성별에 따른 열차종별 승객수 분포 시각화 (dataset : 고객 특성 데이터)

> countplot을 통한 연령대에 따른 열차종별 승객수 분포 시각화

![image](https://user-images.githubusercontent.com/63490319/147577995-7f106b4e-fe40-461c-90df-7168ebc55d0e.png)

- 미성년자, 20대는 KTX보다 무궁화호를 타는 비율이 높은 반면, 30대부터는 KTX를 타는 비율이 높다. 또한, 나이가 많을수록 KTX-호남 열차를 타는 비율이 증가함을 알 수 있다.
- 코레일 비회원 승객들은 연령대가 기타로 나타나는데, 비회원 승객들 중 무궁화호를 탑승한 승객의 비율이 매우 높은 것을 확인할 수 있다.

> countplot을 통한 성별에 따른 열차종별 승객수 분포 시각화

![image](https://user-images.githubusercontent.com/63490319/147578015-416f1126-b8e5-4209-b7eb-6fe6ab6d8c14.png)

- 여성 승객의 무궁화호 탑승 비율이 남성 승객의 무궁화호 탑승 비율보다 더 높음을 알 수 있다.
---
## 3-2. 승객 수 예측 프로젝트

> 시계열 분해법

> ACF, PACF

> 차분

### 1) AR 모델

### 2) MA 모델

### 3) ARIMA 모델
 
### 4) SARIMA 모델

### 5) Facebook - Prophet 모델

### 6) SES 모델
 
### 7) HWES 모델


## 4. Conclusion
### 4-1. 기대효과
### 4-2. 결론 및 제언
