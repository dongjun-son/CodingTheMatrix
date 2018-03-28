# Chap13 

# 고유벡터 - EigenVector



*13.1 ~ 13.2 생략*



## 13.3 고유값과 고유벡터

***Definition*** : 정방행렬 $A$에 대하여, 스칼라(scalar)인 $\lambda$와 영이 아닌 벡터 $v$에 대해 $Av=\lambda v$가 만족하는 경우, $\lambda$는 $A$의 *고유값(eigenvalue)*,  $v$ 는 대응하는 *고유벡터(eigenvector)* 라고 한다.



만약, $\lambda$가 행렬 $A$의 고유값이면, 대응하는 고유벡터는 무수히 많다. 집합 $\{v : Av = \lambda v \}$ 는 벡터공간이며 고유값 $\lambda$에 대응하는 *고유공간(eigenspace)* 이라 한다. 따라서, 고유공간에 있는 임의의 영이 아닌 벡터는 고유벡터로 간주된다. 일반적으로 고유벡터의 크기($norm$)가 1이라는 제한을 두는 것이 다루기에 편리하다.



***Example 13.3.3*** : 행렬 $A$를 아래와 같은 대각행렬이라 하자.
$$
A=\begin{bmatrix} \lambda _{1} &  &  \\  & \ddots  &  \\  &  & \lambda _{ n } \end{bmatrix}
$$
행렬 $A$에 대한 고유벡터와 고유값은 무엇일까? 표준 기저 벡터 $e_1, \dots, e_n$ 에 대해, $Ae_1 = \lambda_1 , \dots, Ae_n = \lambda_n e_n$ 이므로, $e_1, \dots, e_n$ 은 고유벡터이고 대각원소인 $\lambda_1, \dots , \lambda_n$ 은 고유값이다.



***Example 13.3.5*** : 행렬 $A$의 한 고유값은 0이라고 하자. 이 고유값에 대응하는 고유벡터는 $Av = 0v$를 만족하는 영이 아닌 벡터 $v$ 이다. 즉, 벡터 $v$ 는 $Av$가 영벡터가 되게 하는 영이 아닌 벡터이며, $v$ 는 영공간(null space)에 속한다. 역으로, 만약 $A$의 영공간이 자명하지 않으면 $0$은 $A$의 고유값이다.

위의 Example 13.3.5는 고유값 0에 대응하는 고유벡터(즉, 영공간에 속하는 영이 아닌 벡터)를 찾는 방법에 대한 설명이다.  행렬 $A$ 의 고유값을 $\lambda$, 대응하는 고유벡터를 $v$라고 하면, $Av = \lambda v$ 이다. 따라서, $Av - \lambda v = 0$ 이다. $Av - \lambda v = (A - \lambda I)v $ 이므로  $(A - \lambda I)v$ 는 영벡터이다. 이것은 벡터 $v$가 $A - \lambda I$의 영공간에 속하는 영이 아닌 벡터임을 의미한다. 따라서, $A - \lambda I$는 비가역적이다.



***Corollary*** : 만약 $\lambda$ 가 행렬 $A$의 고유값일 경우 $\lambda$ 는 또한 $A^T$의 고유값이다.

- **Proof** : $\lambda$를 행렬 $A$의 고유값이라 하면, $A-\lambda I$는 비가역적이다.  [7.4.7](https://render.githubusercontent.com/view/ipynb?commit=a3e483536003d0454458fd57da8d665d19aeca34&enc_url=68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f457863656c73696f72434a482f436f64696e675468654d61747269782f613365343833353336303033643034353434353866643537646138643636356431396165636133342f4368617030372532302d25323044696d656e73696f6e2f4368617030372d44696d656e73696f6e2e6970796e62&nwo=ExcelsiorCJH%2FCodingTheMatrix&path=Chap07+-+Dimension%2FChap07-Dimension.ipynb&repository_id=125392345&repository_type=Repository#7.4.7-%ED%96%89%EB%A0%AC%EC%9D%98-%EA%B0%80%EC%97%AD%EC%84%B1)에 의하면 $(A - \lambda I)^T$ 또한 비가역적이다. $(A - \lambda I)^T = A^T - \lambda I$ 이므로, $\lambda$는 $A^T$의 고유값이다.



### 13.3.1 유사성과 대각화 가능성 - Diagonalizability

***Definition*** : 가역행렬 S에 대해 $S^{-1}AS = B$ 가 만족되면 두 정방행렬 $A$와 $B$는 '유사' 또는 '닮은(similar)' 행렬이라고 한다.

***Proposition*** : 유사행렬(similar matrix)들은 동일한 고유값을 가진다.

- **Proof** : $\lambda$ 를 행렬 $A$의 고유값이라 하고, $v$ 를 고유벡터라고 하면, $Av = \lambda v$ 가 성립한다. $S^{-1}AS = B$라 하고, $w = S^{-1}v$라 하면 다음이 성립한다.

$$
\begin{eqnarray} Bw & = & { S }^{ -1 }ASw \\  & = & { S }^{ -1 }AS{ S }^{ -1 }v \\  & = & { S }^{ -1 }Av \\  & = & { S }^{ -1 } \lambda v \\  & = & \lambda S^{-1} v  \\  & = & \lambda w \end{eqnarray}
$$

- 따라서, $\lambda$ 는 행렬 $B$의 고유값이다.

***Example 13.3.11*** : 뒤에서 다루겠지만, 행렬 $U$는 상삼각행렬로, 행렬 $A=\begin{bmatrix} 6 & 3 & -9 \\ 0 & 9 & 15 \\ 0 & 0 & 15 \end{bmatrix}$ 의 고유값은 대각원소들인 $6, 9, 15$ 이다. 행렬 $B=\begin{bmatrix} 92 & -32 & -15 \\ -64 & 34 & 39 \\ 176 & -68 & -99 \end{bmatrix}$ 는 $B=S^{-1}AS$ 인 성질을 가진다. 여기서, $S=\begin{bmatrix} -2 & 1 & 4 \\ 1 & -2 & 1 \\ -4 & 3 & 5 \end{bmatrix}$ 이다. 따라서, $B$의 고유값 또한 $6, 9, 15$ 이다.



***Definition*** : 만약 어떤 정방행렬 $A$가 대각행렬과 유사행렬이면, 즉 대각행렬 $\Lambda$에 대해 $S^{-1}AS = \Lambda$를 만족하는 가역행렬 $S$가 있으면, $A$는 *'대각화가 가능하다(diagonalizable)'* 라고 한다. 

만약 $\Lambda$ 가 대각행렬 $\begin{bmatrix} \lambda _{1} &  &  \\  & \ddots  &  \\  &  & \lambda _{ n } \end{bmatrix}$ 이면, 이 행렬의 고유값은 그 대각원소들인 $\lambda_1, \dots , \lambda_n$ 이다. 만약 행렬 $A$와 $\Lambda$가 유사행렬이면, 위의 Proposition에 의해 $A$의 고유값은 $\Lambda$의 고유값 즉, $\Lambda$의 대각원소들이다. 



***Lemma*** : 만약 $\Lambda = S^{-1}AS$ 가 대각행렬이면, $\Lambda$ 의 대각원소들은 고유값들이고, $S$의 열들은 선형독립인 고유벡터들이다. 

$n \times n$ 행렬 $A$가 $n$개의 선형독립인 고유벡터 $v_1, \dots , v_n$을 가진다고 하고, $\lambda_1, \dots, \lambda_n$은 대응하는 고유값들이라 하자. 행렬 $S$를 $\begin{bmatrix} |  &  & |  \\ v_1 & \cdots  & v_n \\  | &  & | \end{bmatrix}$ 로 나타내고, $\Lambda$를 행렬 $\begin{bmatrix} \lambda _{1} &  &  \\  & \ddots  &  \\  &  & \lambda _{ n } \end{bmatrix}$ 라고 하면, $AS = SA$이다. $S$는 정방행렬이고, 그 열들은 선형독립이므로 가역행렬이다. 위의 식에서 오른쪽에 $S^{-1}$ 을 곱하면 $A = S \Lambda S^{-1}$이 구해진다. 이것은 $A$가 대각화가 가능하다는 것을 보여주며, 아래 lemma로 정리할 수 있다.



***Lemma*** : 만약 $n \times n$ 행렬 $A$가 $n$개의 선형독립인 고유벡터를 가지면 $A$는 대각화가 가능하다. 

***Theorem*** : $n \times n$ 행렬이 대각화 가능할 필요충분조건은 이 행렬이 $n$개의 선형독립인 고유벡터를 가지는 것이다. 





## 13.4 고유벡터에 대한 좌표표현

$A$를 $n \times n$ 행렬이라 하고, $t = 1, 2, \dots $에 대해, $x^{(t)} = A^t x^{(0)}$ 라 하자. 또한, 행렬 $A$ 는 대각화 가능하다고 가정하자. 즉, $S^{-1} AS=\Lambda$를 만족하는 가역행렬 $S$와 대각행렬 $\Lambda$가 존재한다. $\lambda_1, \dots , \lambda_n$ 은 $\Lambda$의 대각원소라 하자. 이 대각원소들은 $A$의 고유값이다.  그리고 $v_1, \dots , v_n$은 고유벡터들이며 행렬 $S$의 열이다. 고유벡터들에 대한 $x^{(t)}$ 의 좌표표현을 $u^{(t)}$라고 하면, $x^{(t)} = A^t x^{(0)}$ 는 훨씬 단순한 형태로 표현된다.
$$
\begin{bmatrix}  \\ u^{ (t) } \\  \end{bmatrix}=\begin{bmatrix} \lambda_{1}^{t} &  &  \\  & \ddots &  \\  &  & \lambda_{n}^{t} \end{bmatrix}\begin{bmatrix}  \\ u^{(0)} \\  \end{bmatrix}
$$
위 식이 단순한 이유는 $u^{(0)}$ 의 해당 원소에 대응하는 고유값의 $t$ 제곱을 곱하면 $u^{(t)}$의 각 원소가 구해지기 때문이다. 

이것을 다른 각도에서 한 번 살펴보자.

고유벡터들은 $\mathbb{R}^n$에 대한 기저를 형성한다. 따라서, 임의의 벡터 $x$는 고유벡터들의 선형결합으로 나타낼 수 있다. 
$$
x = \alpha_1 v_1 + \cdots + \alpha_n v_n
$$
위 식에서 양변의 왼쪽에 $A$를 곱해보자.
$$
\begin{eqnarray} Ax & = & A\left( \alpha _{ 1 }v_{ 1 } \right) +\cdots +A\left( \alpha _{ n }v_{ n } \right)  \\  & = & \alpha _{ 1 }Av_{ 1 }+\cdots +\alpha _{ n }Av_{ n } \\  & = & \alpha _{ 1 }\lambda _{ 1 }v_{ 1 }+\cdots +\alpha _{ n }\lambda _{ n }v_{ n } \end{eqnarray}
$$
같은 방식으로 $A(Ax)$를 계산하면, 다음과 같이 된다.
$$
A^{2}x = \alpha_1 \lambda_1^2 v_1 + \cdots + \alpha_n \lambda_n^2 v_n
$$
이를 좀더 일반적인, 임의의 음이 아닌 정수 $t$에 대해 다음과 같이 쓸 수 있다.
$$
A^t x = \alpha_1 \lambda_1^t v_1 + \cdots + \alpha_n \lambda_n^t v_n
$$
이제, 어떤 고유값의 절대값이 다른 것들보다 약간이라도 큰 경우를 생각해 보자. 이때, $t$가 충분히 클 경우, 위의 식에서 우변은 절대값이 큰 고유값이 포함된 항에 의해 결정되고 다른 항들은 상대적으로 작은 값이 될 것이다. 

특히, $\lambda_1$의 절대값이 다른 모든 고유값보다 크다고 가정해 보자. 이 경우, $t$가 충분히 크다면 $A^t x \approx \alpha_1 \lambda_1^t v_1$ 이 될 것이다.  실제로, 절대값이 1보다 작은 고유값에 대응하는 항은 $t$가 증가함에 따라 그 값이 점점 작아지게 된다.



*13.5 생략*



## 13.6 고유값의 존재

어떠한 상황에서 정방행렬이 고유값을 가지는지 알 수 있을까? 또한 대각화가 가능할까?



### 13.6.1 양의 정부호(Positive-Definite) 행렬과 양의 준정부호(Positive-Semidefinite) 행렬

$A$를 임의의 가역행렬이라고 하면, 이 행렬에 12장에서 배운 [특이값 분해(SVD)](http://nbviewer.jupyter.org/github/ExcelsiorCJH/CodingTheMatrix/blob/master/Chap12%20-%20Singular%20Value%20Decomposition/Chap12-Singular_Value_Decomposition.ipynb) 를 적용하면 다음과 같다.
$$
A = U \Sigma V^T
$$
위의 식에서 양변 왼쪽에 $A^T = \left( U \Sigma V^T \right)^T = V \Sigma U^T$ 를 곱하면 다음 식이 얻어진다.
$$
\begin{eqnarray} { A }^{ T }A & = & V \Sigma U^T U \Sigma V^T  \\  & = & V \Sigma \Sigma V^T \\  & = & V \Sigma^2 V^T \end{eqnarray}
$$
위의 식에서 왼쪽에 $V^T$를 곱하고 오른쪽에 $V$를 곱하면, 다음 식이 얻어진다.
$$
V^T \left( A^T A \right) V = \Sigma^2
$$
여기서, $A^T A$는 대각화가 가능하고 고유값은 $A$의 특이값(singular value)의 제곱이다. 이 고유값들은 모두 양의 실수이다.

또한, $A^T A$는 아래의 식에서 알 수 있듯이 대칭행렬이다. 
$$
\left( A^T A \right)^T = A^T \left( A^T \right)^T = A^T A
$$


***Definition*** : 고유값이 모두 양의 실수인 대칭행렬은 양의 정부호행렬이라 한다. 
