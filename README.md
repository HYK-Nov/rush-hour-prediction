# 🚌 Rush Hour Prediction

Dacon의 퇴근 시간대 버스 승차 인원수를 예측하는 머신러닝 프로젝트입니다.  

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10-blue?logo=python">
  <img src="https://img.shields.io/badge/PyCaret-3.0.2-green?logo=ai">
  <img src="https://img.shields.io/badge/ML-Pipeline-orange?logo=scikitlearn">
</p>

---

## 📉 발표 자료

> [구글 슬라이드](https://docs.google.com/presentation/d/1CScy993FKBOMkQL4k5Hz05jaExq4SsulDgIlwq27kYU/edit?usp=sharing)

---

## 📌 프로젝트 개요

- **목표**: 하루 중 퇴근 시간대(`18~20_takeoff`)의 차량 수를 예측
- **데이터**: 버스 노선도/정류장/시간대별 버스 승하차 데이터
- **모델링**: PyCaret 기반 자동 머신러닝 회귀 모델

---

## 🧩 사용한 기술 스택

- **Python 3.10**
- **PyCaret 3.x**
- **Pandas, Numpy, Matplotlib, Seaborn**
- **Scikit-learn**
- Jupyter Notebook 기반 실험

---

## 🗂️ 주요 파일 구조
```
rush-hour-prediction/
└── rush_hour.ipynb # 주요 분석 및 모델링 notebook
```

## 📊 예측 대상
18~20_takeoff: 18시~20시 사이 차량 이동량

나머지 시간대/특징들을 기반으로 18~20_takeoff 값을 예측
