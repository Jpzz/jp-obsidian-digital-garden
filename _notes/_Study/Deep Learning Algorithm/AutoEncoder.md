### AutoEncoder란?
- ["] An auto encoder, auto associator or Diabolo network is an artificial neural network used for unsupervised learning of efficient codings 
### Keywords
- [*] Unsupervised Leanring
- [*] ML Density Estimation
- [*] Dimensionality Reduction
	- Feature Extraction
	- Manifold Leanring 
- [*] Generative Model Learning

- AutoEncoder를 학습할 때, 학습 방법은 비 교사 학습 방법을 따르며, Loss는 negative ML로 해석됨
- 학습된 AutoEncoder에서 Encoder는 차원 축소 역할을 수행하며, Decoder는 생성 모델의 역할을 수행함


### What is Dimentionality Reduction
- 기존 존재하는 방법론은 Neighborhood Based Training인데, 고차원 데이터 간의 유클리디안 거리는 유의미한 거리 개념이 아닐 가능성이 높음


Mainfold에 대해 살펴보면,
- 목적은 데이터 압축, 데이터 시각화, 차원의 저주 피하기, 특징 추출이 있음
- m차원 데이터가 m차원 공간에 존재할 때 이 데이터를 에러없이 잘 아우를 수 있는 표면이 존재한다 라는 가정