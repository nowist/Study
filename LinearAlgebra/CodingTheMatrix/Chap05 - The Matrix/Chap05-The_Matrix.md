# Chap 05 - 행렬(The Matrix)

## 5.1 행렬이란 무엇인가?

### 5.1.1 전통적인 행렬

일반적으로, $m$개의 행과 $n$개의 열을 가진 행렬은 $m \times n$행렬이라 한다. 행렬 $A$에 대해 $i,j$ *원소* 는 $i$번쨰 행과 $j$번째 열에 있는 원소로 정의되며, 전통적으로 $a_{i,j}$ 또는 $a_{ij}$로 나타낸다. <br />따라서, $F$상의 모든 $i=1,...,m$과 $j=1,...,n$에 대하여 $a_{ij} \in F$일 때,

$$A = \begin{bmatrix} a_{ 11 } & a_{ 12 } & \cdots  & a_{ 1n } \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \vdots & \vdots  \\ a_{m1} & a_{m2} & \cdots & a_{mn} \end{bmatrix}$$

을 $F$-위의 ($m \times n$)-행렬(($m \times n$)-matrix over $F$)이라고 한다.

### 5.1.2 행렬에 대해 알아보기

$F$상의 $D$-벡터를 집합 $D$에서 $F$로의 함수로 정의한거 처럼, $F$상의 $R \times C$ 행렬을 카테시안 곱 $R \times C$로의 함수로 정의한다. $R$의 원소를 *행 라벨* (row label) 이라 하고 $C$의 원소를 *열 라벨* (column label)이라 한다. <br />

**Example 5.1.3** 아래는 $R=$ `{'a', 'b'}`이고 $C=$`{'#', '@', '?'}`인 예이다. 

|      |  @   |  #   |  ?   |
| :--: | :--: | :--: | :--: |
|  a   |  1   |  2   |  3   |
|  b   |  10  |  20  |  30  |

### 5.1.3 행, 열, 엔트리

행렬의 유용한 점은 행과 열을 벡터로 해석할 수 있다. 위의 Example 5.1.3의 행렬을 아래와 같이 벡터로 나타낼 수 있다.

- 행 `a`는 벡터 [1, 2, 3] 이다.
- 행 `b`는 벡터 [10, 20, 30] 이다.
- 열 `@`는 벡터 [1, 10] 이다.
- 열 `#`은 벡터 [2, 20] 이다.
- 열 `?`는 벡터 [3, 30] 이다.

이번 5장에서는 행렬 구현 및 예제들을 파이썬의 고성능 수치 계산을 위한 모듈인 [NumPy](http://www.numpy.org/)를 사용한다. <br />numpy모듈을 이용하여 위의 Example 5.1.3을 다음과 같이 코드로 나타낼 수 있다.

```python
import numpy as np

M = np.matrix('1 2 3; 10 20 30')  # = np.matrix([[1, 2, 3], [10, 20, 30]])
print(M)

"""출력 결과
[[ 1  2  3]
 [10 20 30]]
"""
```

위와 같이 $R \times C$ 행렬 $M(r \in R, c \in C)$에 대해, $M$의 $r,c$원소는 $(r,c)$ 쌍이 매핑하는 것으로 정의 되며 $M_{r,c}$ 또는 $M[r,c]$로 나타내고, 행과 열은 아래와 같이 정의된다.

- $r \in R$에 대해, 행 $r$은 각 원소 $c \in C$에 대해 엔트리 $c$가 $M[r,c]$인 $C$-벡터 이다.
- $c \in C$에 대해, 열 $c$는 각 원소 $r \in R$에 대해 엔트리 $r$이 $M[r, c]$인 $R$-벡터 이다.

이를 numpy를 이용한 파이썬 코드로 나타내면 아래와 같다.
