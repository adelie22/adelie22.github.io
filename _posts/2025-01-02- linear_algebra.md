---
layout : single
title : 선형대수
categories : Mathematics
tag : 선형대수
toc : true
toc_sticky: true 
author_profile : false
sidebar:
    nav : "counts"
---
## Part1_1 연립일차방정식과 행렬
  
**주요 개념 및 정리**
- 계수, 주요변수, 자유변수
- 제차방정식, 비제차방정식
- 방정식의 해 = 특수해
- 특수해(일반해 중 하나의 해), 일반해(방정식의 해 전체 집합), 자명한 해, 자명하지 않은 해
- 무모순(방정식의 해가 존재), 모순(방정식의 해가 존재하지 않음)
- 연립방정식의 기본연산(거꾸로 풀기, 앞으로 풀기, 가우스 소거법, 가우스-조르당 소거법)
- 연립방정식의 기본연산(방정식을 동치인 방정식으로 단순화하여 풀이한다)
    - S(1) <-> S(2)
    - 6S(1) - S(2) -> S(2) 와 같은 과정으로 동치로 만들고 최종적으로 거꾸로풀기로 해를 구함 

### Part1_1_1 예제
---
![연립방정식 예제](/images/p1_1.jpeg){: style="width:280px; height:auto;" }


## Part1_2 행렬과 행렬연산

**주요 개념 및 정리**
- 상등(행렬 A = B 를 의미)
- 스칼라곱 K x 행렬은 K를 행렬의 모든원소에 곱해주는 것
- 행렬의 덧셈은 교환, 결합법칙 성립, 전치행렬 적용 시 순서 바뀌지 않음
- k(A+B) = kA + kB, (k + l)A = kA + lA 성립
- 행렬의 곱셈 A x B는 A(raw), B(column)의 벡터 내적
- 행렬 곱셈 A(B+C) = AB + AC (분배법칙 성립)
- A(BC) = (AB)C (결합법칙 성립)
- A x B = O 일 때 A or B 가 O일 필요는 없음
- 행렬 A에 서로다른 행렬을 각각 곱했을 때 결과가 같을 수 있다
- 대각합(Trace)는 정방행렬일 때 논할 수 있다.
- tr(AB) = tr(BA)가 성립함을 주의. 단. AB != BA이다.
- 어떤 행렬 A와 A의 전치행렬을 곱하면 정방행렬이 되며, 이 행렬의 trace는 행렬 A의 모든 원소를 제곱하여 더한 것

### Part1_2_1 행렬의 거듭제곱 및 특수행렬
- 거듭제곱
- 대각행렬(diagonal matrix)
    - 주대각 원소 값 관계없이 ~주대각 원소가 모두 0
- 단위행렬(identity matrix)
    - 주대각이 모두 1 나머지는 모두 0(어떤 행렬 A x I = A)
- 상부삼각행렬(Upper triangular matirx)
    - 주대각 아래 모두 0
- 하부삼각행렬(Lower triangular matrix)
    - 주대각 위 모두 0
- 대칭행렬(Symmetric matrix)
    - 주대각 기준 대칭
- 비대칭행렬(Skew symmetric matrix)
    - 주대각 기준 부호 반대 (컴퓨터수학에서의 비대칭, 반대칭과는 다른개념)
- 정방행렬의 대칭행렬 + 비대칭행렬의 합 표현 1/2(A+A^t) + 1/2(A - A^t)
    - k(A+A^t)는 대칭행렬, k(A-A^t)는 비대칭행렬

### Part1_2_2 예제

![예제](/images/1_2_2_1.jpeg){: style="width:280px; height:auto;" }
![예제](/images/1_2_2_2.jpeg){: style="width:280px; height:auto;" }
![예제](/images/1_2_2_3.jpeg){: style="width:280px; height:auto;" }


### Part1_2_3 역행렬(inverse matrix)
