---
layout : single
title : 확률 및 통계
categories : Mathematics
tag : statistics and probability
toc : true
toc_sticky: true 
author_profile : false
sidebar:
    nav : "counts"
---
## 고등 기본 개념
![고등개념](/images/sta_1.jpeg){: style="width:280px; height:auto;" }
![고등개념](/images/sta_2.jpeg){: style="width:280px; height:auto;" }
![고등개념](/images/sta_3.jpeg){: style="width:280px; height:auto;" }
![고등개념](/images/sta_4.jpeg){: style="width:280px; height:auto;" }
![고등개념](/images/sta_5.jpeg){: style="width:280px; height:auto;" }

- 용어
    - 경우의 수, 확률, 확률분포
    - 확률변수 = X, 확률분포표, 확률분포표에서 확률질량함수의 합 = 1
    - 평균 E(x): 확률변수와 확률질량함수 곱의 합
    - 분산 V(x): E(x^2) - {E(x)}^2 => 제곱의 평균 - 평균의 제곱 
    - 표준편차 σ(x) : V(x)^1/2
    - V(x), σ(x) >= 0 
    - E(ax+b) = aE(x)+b
    - V(ax+b) = a^2V(x)
    - σ(ax+b) = ㅣaㅣV(x)^1/2
    - 이항분포 = 이산확률분포
        - B(n, p) n = 총 시행횟수, p = 확률
        - 시행횟수는 0부터이므로 0 ~ n 까지 확률변수 X에 대한 확률분포표를 그려야함
    - 이항분포 B(n,p)에서 평균, 분산, 표준편차 공식
        - E(x) = np
            - 평균이 np인 이유는 직관적으로 동전을 100번 던졌을 때 앞면이 나올 확률은 1/2이므로 총 시행횟수 x 해당확률을 곱하는 것
        - V(x) = np(1-p) = npq
        - σ(x) = (npq)^1/2
    - 정규분포 = 연속확률분포
        - N(m, σ^2) 매개변수는 각각 평균, 분산
        - 확률밀도함수는 **그래프**로 표현
        - z를 **한 걸음**이라고 하면 평균(m)으로부터 떨어진 걸음 수 만큼은 보폭(z x 표준편차)이며, 표준정규분포표를 보고 얼만큼 떨어져있는지 확률을 계산하면 된다.
        - X -> z로 변환하는 과정을 **표준화**라고 하며, 걸음 수(z)가 같으면 **확률**도 같음을 이용한다.
        - 표준정규분포표는 정규분표의 표준이며 그 표준은 z이다.
    - 표본평균의 분포
        - 정규분포를 이용하여 구하게 되며, N()의 매개변수를 각각 모평균, 모표준편차로 본다.
        - 모표준편차는 항상 제곱의 형태로 나타내기
        - 모평균과 표본평균은 항상 같다.
        - 표본표준편차는 (표준편차 / 표본크기^1/2)^2 
        - 평균 m의 좌우 1.97만큼의 z에 어떤 표본이 존재할 확률이 95%이면 반대로 해당 표본의 좌, 우 1.97만큼 위치에 평균이 존재할 확률도 95%이고 이 구간(표준편차 x Z)를 신뢰구간이라고 함.