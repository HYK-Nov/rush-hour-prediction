# 🚌 퇴근시간 버스승차인원 예측

![Image](https://github.com/user-attachments/assets/506de453-d51f-418f-ad97-1242d36a1482)

제주도 퇴근 시간대 버스 승차 인원수를 예측하는 머신러닝 프로젝트입니다.  

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10-blue?logo=python">
  <img src="https://img.shields.io/badge/PyCaret-3.0.2-green?logo=ai">
  <img src="https://img.shields.io/badge/ML-Pipeline-orange?logo=scikitlearn">
</p>

---

## 데이터

> DACON : https://dacon.io/competitions/official/229255/overview/description

## 📉 발표 자료

> [구글 슬라이드](https://docs.google.com/presentation/d/1CScy993FKBOMkQL4k5Hz05jaExq4SsulDgIlwq27kYU/edit?usp=sharing)


## 📌 프로젝트 개요

- **목표**: 하루 중 퇴근 시간대(`18~20_takeoff`)의 차량 수를 예측
- **데이터**: 버스 노선도/정류장/시간대별 버스 승하차 데이터
- **모델링**: PyCaret 기반 자동 머신러닝 회귀 모델

## 🧩 사용한 기술 스택

- **Python 3.10**
- **PyCaret 3.x**
- **Pandas, Numpy, Matplotlib, Seaborn**
- **Scikit-learn**
- Jupyter Notebook 기반 실험


## 🗂️ 주요 파일 구조
```
rush-hour-prediction/
└── rush_hour.ipynb # 주요 분석 및 모델링 notebook
```

## 📊 예측 대상
`18~20_takeoff`: 18시~20시 사이 차량 이동량

나머지 시간대/특징들을 기반으로 `18~20_takeoff` 값을 예측

## ✨ 주요 사항

### 💽 데이터 전처리

<table>
  <thead>
    <tr>
      <td>원본 Feature</td>
      <td>변환 Feature</td>
      <td>설명</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan=4>date</td>
    </tr>
    <tr>
      <td>weekday</td>
      <td>요일</td>
    </tr>
    <tr>
      <td>is_weekend</td>
      <td>주말 여부</td>
    </tr>
    <tr>
      <td>is_holiday</td>
      <td>공휴일 여부</td>
    </tr>
    <tr>
      <td rowspan=3>latitude / longitude</td>
    </tr>
    <tr>
      <td>jeju_distance</td>
      <td>제주시와의 거리</td>
    </tr>
    <tr>
      <td>seogwipo_distance</td>
      <td>서귀포시와의 거리</td>
    </tr>
    <tr>
      <td rowspan=4>X~Y_ride</td>
    </tr>
    <tr>
      <td>6~8_ride</td>
      <td>6~8시 승차</td>
    </tr>
    <tr>
      <td>8~10_ride</td>
      <td>8~10시 승차</td>
    </tr>
    <tr>
      <td>10~12_ride</td>
      <td>10~12시 승차</td>
    </tr>
    <tr>
      <td rowspan=4>X~Y_takeoff</td>
    </tr>
    <tr>
      <td>6~8_takeoff</td>
      <td>6~8시 하차</td>
    </tr>
    <tr>
      <td>8~10_takeoff</td>
      <td>8~10시 하차</td>
    </tr>
    <tr>
      <td>10~12_takeoff</td>
      <td>10~12시 하차</td>
    </tr>
  </tbody>
</table>

### 🥵 히트맵

학습데이터 요소 별 관계를 색상으로 나타낸 것

어두울수록 관련성⬇️ 밝을수록 관련성⬆️

|전처리 전|전처리 후|
|---|---|
|![Image](https://github.com/user-attachments/assets/2c0de067-578f-4a89-ac53-7e517c2d3638)|![Image](https://github.com/user-attachments/assets/0239fa2c-c5e7-48e7-85d5-ad181068fb44)|

### 🌳 랜덤 포레스트 모델

여러 개의 결정 트리(Decision Tree)를 무작위로 만들어서 그 결과를 합쳐서 예측하는 기법

**결정트리(Decision Tree)**

데이터를 분류하거나 예측할 때, 질문을 던지면서 나무 구조로 분기해가는 알고리즘

![Image](https://github.com/user-attachments/assets/c1b449c1-ea4b-48ec-983e-24322db213aa)

## ✅ 평가지표

### 회귀모델 성능 평가 지표

![Image](https://github.com/user-attachments/assets/6765fb89-130b-421d-97e6-86668c828eea)

|MAE(Mean Absolute Error)|R2(Coefficient of Determination)|
|---|---|
|실제값 - 예측값의 절대값의 평균<br>절대값을 취하기 때문에 가장 직관적으로 알 수 있는 지표<br>값 ⬇️	예측도 ⬆️|실제 y값의 분산에 비해, 예측 y의 분산이 얼만큼인지 비교<br>해당 모델이 주어진 데이터에 얼마나 적합한지를 평가하는 지표<br>값 ⬆️	예측도 ⬆️|

### 🔵 잔차도(Residual plot)

기존 데이터 값과 분석 모델에 의해 예측된 값의 차이

![Image](https://github.com/user-attachments/assets/b07b7148-418f-4c9e-8244-5dc244b873a1)

### ❗특성 중요도(Feature Importance)

각 특성들이 값을 예측하는 과정에 얼마나 영향을 끼쳤는가의 정도

|SHAP Value|Feature Importance Plot|
|---|---|
|![Image](https://github.com/user-attachments/assets/aebcdecc-c6b7-4913-99ad-33b0e93f849c)|![Image](https://github.com/user-attachments/assets/b9bf6619-3056-4bf9-a930-1b72b2992ab5)|

## 📄 결과

0에 가까울 수록 등수가 높아짐

![Image](https://github.com/user-attachments/assets/a7833064-25af-4e2c-8eaf-374951ac4085)
