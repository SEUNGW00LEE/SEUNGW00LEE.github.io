---
layout: single
title: "Attention, Transformer에 대하여"
categories: [AI, Paper Review]
tag: []
typora-root-url: ../
use_math: true



---

<img src="/images/2024-06-28-Atttention/image-20240628025940178.png" alt="image-20240628025940178" style="zoom:50%;" />

Transformer를 알기 전, RNN부터 알아야한다.

RNN은 연속적인 데이터에 잘 동작한다.

Word embedding : 단어를 숫자로 바꾸자

저는 학생 입니다.

[1,0,0], [0,1,0], [0,0,1]

X1, X2, X3

이를 Neural Network에 순차적으로 넣어보자 (RNN의 접근법)

RNN의 동작 방식 (Recurrent Neural Network)

<img src="/images/2024-06-28-Atttention/image-20240628181213342.png" alt="image-20240628181213342" style="zoom:50%;" />

### RNN의 수식

- 화살표를 지날 때 FC 통과한다고 생각하면 된다.

<img src="/images/2024-06-28-Atttention/image-20240628181416186.png" alt="image-20240628181416186" style="zoom:50%;" />

$W_x, W_h, W_y, b, b_y$는 시간에 따라 다르지 않다.

<img src="/images/2024-06-28-Atttention/image-20240628181909067.png" alt="image-20240628181909067" style="zoom:50%;" />

이와 같이 $h$는 이전의 정보를 가진다.

<img src="/images/2024-06-28-Atttention/image-20240628182054796.png" alt="image-20240628182054796" style="zoom:50%;" />

 

다음에 어떤 알파벳(one-hot encoded)이 나와야 할까? => 다중 분류네!

<img src="/images/2024-06-28-Atttention/image-20240628183547905.png" alt="image-20240628183547905" style="zoom:50%;" />



=> *ŷ* 을 softmax 통과시켜서 cross-entropy 계산
=> ELLO 네개 글자에 대해 cross-entropy 더해주면 되겠다

근데 O가 나오게 하기 위해 H가 gradient 에 미치는 영향력?

멀수록 잊혀진다!(back propagation) 또, 갈수록 흐려진다!(forward propagation) <- tanh 때문

이 둘 모두 RNN의 구조적 한계이다.





Attention 시점마다 context vector가 변한다.

Attention의 방식은 dot product이다.

hidden state 간의 weight sum.

 벡터에 행렬을 곱하는 것은 곧 선형변환.

